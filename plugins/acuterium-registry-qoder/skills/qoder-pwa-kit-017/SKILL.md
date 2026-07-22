---
name: qoder-pwa-kit-017
description: "json { 'name': 'Urana - The Flame of Intelligence', 'short_name': 'Urana', 'description': 'AI-Powered Quality Assurance & Accreditation Platform', 'theme_color': '#1a1f2e', 'background_color': '#0a0f1a', 'display': 'standalone', 'orientation': 'portrait', 'scope': '/urana/', 'start_url': '/urana/', 'icons': [ { 'src': '/icons/icon-192.png', 'sizes': '192x192', 'type': 'image/png', 'purpose': 'any maskable' }, { 'src': '/icons/icon-512.png', 'sizes': '512x512', 'type': 'image/png', 'purpose': 'any maskable' } ], 'shortcuts': [ { 'name': 'New Conversation', 'short_name': 'New Chat', 'url': '/urana/chat', 'icons': [{ 'src': '/icons/new-chat.png', 'sizes': '96x96' }] }, { 'name': 'Quality Dashboard', 'short_name': 'Dashboard', 'url': '/urana/dashboard', 'icons': [{ 'src'..."
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# PWA Service Worker Kit

## PWA Manifest (manifest.json)

```json
{
  "name": "Urana - The Flame of Intelligence",
  "short_name": "Urana",
  "description": "AI-Powered Quality Assurance & Accreditation Platform",
  "theme_color": "#1a1f2e",
  "background_color": "#0a0f1a",
  "display": "standalone",
  "orientation": "portrait",
  "scope": "/urana/",
  "start_url": "/urana/",
  "icons": [
    { "src": "/icons/icon-192.png", "sizes": "192x192", "type": "image/png", "purpose": "any maskable" },
    { "src": "/icons/icon-512.png", "sizes": "512x512", "type": "image/png", "purpose": "any maskable" }
  ],
  "shortcuts": [
    { "name": "New Conversation", "short_name": "New Chat", "url": "/urana/chat", "icons": [{ "src": "/icons/new-chat.png", "sizes": "96x96" }] },
    { "name": "Quality Dashboard", "short_name": "Dashboard", "url": "/urana/dashboard", "icons": [{ "src": "/icons/dashboard.png", "sizes": "96x96" }] }
  ]
}
```

## Service Worker — Hybrid Caching Strategy

```javascript
const CACHE_NAME = 'urana-v2';
const STATIC_ASSETS = ['/', '/index.html', '/manifest.json'];

// Install: pre-cache static assets
self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then(cache => cache.addAll(STATIC_ASSETS)).then(() => self.skipWaiting())
  );
});

// Activate: clean old caches
self.addEventListener('activate', (event) => {
  event.waitUntil(
    caches.keys().then(keys => Promise.all(keys.filter(k => k !== CACHE_NAME).map(k => caches.delete(k))))
      .then(() => self.clients.claim())
  );
});

// Fetch: network-first for API, cache-first for static
self.addEventListener('fetch', (event) => {
  const url = new URL(event.request.url);
  if (url.pathname.startsWith('/api/')) {
    // Network-first with cache fallback for API calls
    event.respondWith(fetch(event.request).catch(() => caches.match(event.request)));
    return;
  }
  // Cache-first with network fallback for static assets
  event.respondWith(
    caches.match(event.request).then(cached => {
      if (cached) return cached;
      return fetch(event.request).then(response => {
        if (!response || response.status !== 200) return response;
        const clone = response.clone();
        caches.open(CACHE_NAME).then(cache => cache.put(event.request, clone));
        return response;
      });
    })
  );
});
```

## Background Sync

```javascript
self.addEventListener('sync', (event) => {
  if (event.tag === 'sync-submissions') {
    event.waitUntil(syncSubmissions());
  }
});

async function syncSubmissions() {
  // Read queued submissions from IndexedDB and POST to server
  const db = await openSyncQueue();
  const pending = await db.getAll('submissions');
  for (const item of pending) {
    try {
      await fetch('/api/submissions', { method: 'POST', body: JSON.stringify(item) });
      await db.delete('submissions', item.id);
    } catch (e) { break; } // retry on next sync
  }
}
```

## Push Notifications

```javascript
self.addEventListener('push', (event) => {
  const data = event.data.json();
  event.waitUntil(
    self.registration.showNotification(data.title, {
      body: data.body, icon: '/icons/icon-192.png', badge: '/icons/badge.png',
      vibrate: [200, 100, 200], data: { url: data.url }
    })
  );
});
```

## Vite PWA Plugin Setup

```javascript
// vite.config.js
import { VitePWA } from 'vite-plugin-pwa';
export default { plugins: [VitePWA({ registerType: 'autoUpdate', manifest: { /* above */ } })] };
```

## Registration in App

```javascript
import { registerSW } from 'virtual:pwa-register';
const updateSW = registerSW({ onNeedRefresh: () => updateSW(true), onOfflineReady: () => console.log('Offline ready') });
```

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** Marel | **Thread:** T13 — ACAI V2
- **Dependencies:** QODER-DESIGN-TOKENS-002, QODER-WEB-IMPL-006
