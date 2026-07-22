---
name: qoder-bilingual-rtl-016
description: "css --font-heading: 'IBM Plex Sans Arabic', 'Inter', sans-serif; --font-body: 'Tajawal', 'Inter', sans-serif; --font-accent: 'Readex Pro', sans-serif;"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Bilingual AR/EN Typography & RTL Layout System

## Font Stack Configuration

```css
--font-heading: 'IBM Plex Sans Arabic', 'Inter', sans-serif;
--font-body: 'Tajawal', 'Inter', sans-serif;
--font-accent: 'Readex Pro', sans-serif;
```

Load fonts via Google Fonts:
```html
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@400;500;600;700&family=Tajawal:wght@400;500;700&family=Readex+Pro:wght@400;500;600;700&display=swap" rel="stylesheet">
```

## ArabicTypography Component (React)

```tsx
interface ArabicTypographyProps {
  text: string;
  size: 'xs' | 'sm' | 'base' | 'md' | 'lg' | 'xl' | '2xl';
  weight?: '400' | '500' | '600' | '700' | 'bold';
  className?: string;
  lang?: 'ar' | 'en';
}

const sizeMap = {
  xs: '0.75rem', sm: '0.875rem', base: '0.9375rem',
  md: '1rem', lg: '1.125rem', xl: '1.25rem', '2xl': '1.5rem'
};

const ArabicTypography: React.FC<ArabicTypographyProps> = ({ text, size, weight = '400', className, lang }) => {
  const isArabic = lang === 'ar' || /[\u0600-\u06FF]/.test(text);
  return (
    <span className={className} lang={isArabic ? 'ar' : 'en'} dir={isArabic ? 'rtl' : 'ltr'}
      style={{
        fontFamily: isArabic ? 'var(--font-body)' : 'var(--font-heading)',
        fontSize: sizeMap[size], fontWeight: weight,
        lineHeight: isArabic ? '1.8' : '1.5',
      }}>
      {text}
    </span>
  );
};
```

## RTL Layout Rules

```css
/* Automatic RTL mirroring */
[dir="rtl"] .sidebar       { border-right: none; border-left: 1px solid var(--border); }
[dir="rtl"] .active-item   { border-left: 3px solid var(--accent); border-right: none; }
[dir="rtl"] .action-btn    { transform: translateX(-4px); }  /* reverse hover direction */
[dir="rtl"] .message-user  { border-bottom-left-radius: 4px; border-bottom-right-radius: 12px; }
[dir="rtl"] .message-asst  { border-bottom-right-radius: 4px; border-bottom-left-radius: 12px; }

/* Use logical properties wherever possible */
.margin-start  { margin-inline-start: 1rem; }
.padding-end   { padding-inline-end: 1rem; }
```

## Bilingual Label Pattern

Every UI label should carry both languages:
```tsx
const labels = {
  generateReport: { en: 'Generate Report', ar: 'إنشاء تقرير' },
  automateTask:   { en: 'Automate Task',   ar: 'أتمتة المهمة' },
  scheduleTrend:  { en: 'Schedule Trend',  ar: 'جدولة الاتجاه' },
  uploadFile:     { en: 'Upload File',      ar: 'رفع ملف' },
};
```

## Language Detection

Auto-detect text direction at render time:
```javascript
const isArabic = (text) => /[\u0600-\u06FF]/.test(text);
const setDirection = (el, text) => {
  el.dir = isArabic(text) ? 'rtl' : 'ltr';
  el.lang = isArabic(text) ? 'ar' : 'en';
};
```

## Key Implementation Notes

- Set `<html dir="rtl" lang="ar">` at document root for full RTL mode
- Use `text-align: start` instead of `text-align: left`
- Numbers and Latin text remain LTR within RTL context (`unicode-bidi: embed`)
- Test with both `dir="rtl"` and `dir="ltr"` on every component
- Arabic text needs ~20% more vertical line-height than Latin text

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** Marel | **Thread:** T13 — ACAI V2
- **Dependencies:** QODER-DESIGN-TOKENS-002
