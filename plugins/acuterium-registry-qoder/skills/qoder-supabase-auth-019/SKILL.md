---
name: qoder-supabase-auth-019
description: "User → Supabase Auth → JWT (15min) + Refresh Token → Membership Lookup → Tenant Context → RLS Policies"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Supabase Auth + Multi-Tenant JWT Integration

## Auth Flow

```
User → Supabase Auth → JWT (15min) + Refresh Token → Membership Lookup → Tenant Context → RLS Policies
```

## Registration

```javascript
async function register(email, password, displayName, tenantSlug) {
  // 1. Create Supabase Auth user
  const { data: authUser, error: authError } = await supabase.auth.signUp({
    email, password, options: { data: { display_name: displayName } }
  });
  if (authError) throw authError;

  // 2. Get or create tenant
  let { data: tenant } = await supabase.from('tenants').select('*').eq('slug', tenantSlug).single();
  if (!tenant) {
    const { data: newTenant } = await supabase.from('tenants').insert({ slug: tenantSlug, name: tenantSlug }).select().single();
    tenant = newTenant;
  }

  // 3. Create membership (owner role for new tenant creators)
  await supabase.from('memberships').insert({
    tenant_id: tenant.id, user_id: authUser.user.id, role: 'owner', status: 'active'
  });

  return { user: authUser.user, tenant };
}
```

## Login

```javascript
async function login(email, password) {
  const { data, error } = await supabase.auth.signInWithPassword({ email, password });
  if (error) throw error;

  // Resolve tenant memberships
  const { data: memberships } = await supabase
    .from('memberships').select('tenant_id, role, tenants(*)')
    .eq('user_id', data.user.id).eq('status', 'active');

  // Issue short-lived JWT
  const token = jwt.sign(
    { userId: data.user.id, email: data.user.email },
    process.env.JWT_SECRET,
    { expiresIn: '15m' }
  );

  return { user: data.user, memberships, token, refreshToken: data.session.refresh_token };
}
```

## Token Refresh

```javascript
async function refreshToken(refreshToken) {
  const { data, error } = await supabase.auth.refreshSession({ refresh_token: refreshToken });
  if (error) throw error;
  const token = jwt.sign(
    { userId: data.user.id, email: data.user.email },
    process.env.JWT_SECRET, { expiresIn: '15m' }
  );
  return { token, session: data.session };
}
```

## Row-Level Security (RLS) Policies

```sql
-- Enable RLS on all tenant-scoped tables
ALTER TABLE tenants ENABLE ROW LEVEL SECURITY;
ALTER TABLE projects ENABLE ROW LEVEL SECURITY;
ALTER TABLE documents ENABLE ROW LEVEL SECURITY;
ALTER TABLE assessments ENABLE ROW LEVEL SECURITY;
ALTER TABLE appeals ENABLE ROW LEVEL SECURITY;

-- Tenant isolation: only access rows belonging to your current tenant
CREATE POLICY tenant_isolation ON projects
  USING (tenant_id = current_setting('app.current_tenant_id')::UUID);

-- User access: must have active membership in the tenant
CREATE POLICY user_access ON documents
  USING (
    tenant_id = current_setting('app.current_tenant_id')::UUID
    AND EXISTS (
      SELECT 1 FROM memberships
      WHERE memberships.tenant_id = documents.tenant_id
      AND memberships.user_id = auth.uid()
      AND memberships.status = 'active'
    )
  );
```

## Middleware: Set Current Tenant

```javascript
function setTenantContext(tenantId) {
  // Must be called before any DB query in a request lifecycle
  await supabase.rpc('set_current_tenant', { tenant_id: tenantId });
}
```

## Security Notes

- JWT expiry: 15 minutes (short-lived for security)
- Always pair with QODER-Q-ENC-SECURITY-011 for encrypting sensitive payloads
- Audit all auth events via audit_log table
- Membership roles: owner, admin, member, viewer

## Environment Variables

```
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_SUPABASE_SERVICE_KEY=your-service-key (server-side only!)
JWT_SECRET=your-jwt-secret
```

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** W-09 (Baranurion) | **Thread:** T13 — ACAI V2
- **Dependencies:** QODER-URANA-PLATFORM-010, QODER-Q-ENC-SECURITY-011
- **Sovereignty Tier:** 10 (air-gap deployment for Urana)
