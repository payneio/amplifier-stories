# Mobile Testing Checklist

Use this checklist to validate responsive behavior across devices and browsers.

## Quick Test URLs

After deploying to GitHub Pages, test each URL:

```
https://robotdad.github.io/amplifier-module-stories/
https://robotdad.github.io/amplifier-module-stories/cortex-amplifier-presentation.html
https://robotdad.github.io/amplifier-module-stories/shadow-environments-deck.html
(etc.)
```

---

## Device Matrix

Test on at least one device from each category:

| Category | Device | Viewport | Browser |
|----------|--------|----------|---------|
| **Phone (small)** | iPhone SE | 375×667 | Safari |
| **Phone (large)** | iPhone 15 Pro | 393×852 | Safari |
| **Phone (Android)** | Pixel 7 | 412×915 | Chrome |
| **Tablet (portrait)** | iPad | 768×1024 | Safari |
| **Tablet (landscape)** | iPad | 1024×768 | Safari |
| **Desktop (small)** | MacBook Air | 1280×800 | Chrome |
| **Desktop (large)** | iMac | 1920×1080 | Firefox |

---

## Per-Deck Checklist

For each presentation, verify:

### Layout & Typography
- [ ] **Title slide**: Headline doesn't overflow, scales smoothly
- [ ] **Body text**: Readable without zooming (≥14px equivalent)
- [ ] **Code blocks**: Horizontal scroll if needed, no clipping
- [ ] **Cards/grids**: Stack vertically on phone, grid on tablet+
- [ ] **Spacing**: Padding scales down gracefully
- [ ] **No horizontal scroll** on body (except code blocks)

### Navigation
- [ ] **Nav dots**: Touch-friendly size (≥44px touch area)
- [ ] **Swipe navigation**: Works on touch devices
- [ ] **Keyboard navigation**: Left/right arrows work
- [ ] **Slide counter**: Visible and readable
- [ ] **"More Stories" link**: Accessible on all sizes

### Interactions
- [ ] **Tap/click slide**: Advances to next
- [ ] **No double-tap zoom**: `user-scalable=yes` but content fits
- [ ] **Safe areas**: Content not hidden by notch/home indicator
- [ ] **Orientation change**: Adapts smoothly (no reload needed)

### Visual Fidelity
- [ ] **Gradients**: Render correctly (no banding)
- [ ] **Borders/shadows**: Visible but not oversized
- [ ] **Icons/emojis**: Display correctly (system font fallback)
- [ ] **Colors**: Sufficient contrast on all backgrounds

---

## Browser-Specific Checks

### Safari iOS
- [ ] `100dvh` works (accounts for address bar)
- [ ] `-webkit-tap-highlight-color` is suppressed
- [ ] `env(safe-area-inset-*)` respected
- [ ] No rubber-banding issues on slides

### Chrome Mobile
- [ ] Touch events work (swipe navigation)
- [ ] Dark mode doesn't break colors
- [ ] Address bar hide/show doesn't break layout

### Firefox
- [ ] CSS `clamp()` supported
- [ ] Grid layouts work correctly
- [ ] Touch navigation functional

---

## Automated Tests (CLI)

Run these commands to catch obvious issues:

```bash
# Check for remaining fixed pixel values (should be minimal)
grep -c "font-size: [0-9]*px" docs/*.html | grep -v ":0$"

# Check for inline styles (should be none for font-size)
grep -c 'style="[^"]*font-size:[^"]*"' docs/*.html | grep -v ":0$"

# Verify viewport meta tag exists
grep -l 'viewport' docs/*.html | wc -l
# Should equal total HTML file count

# Check for dvh support
grep -c "100dvh" docs/*.html
```

---

## Lighthouse Audit

For each deck, run Lighthouse and check:

1. **Performance**: ≥90 score
2. **Accessibility**: ≥90 score
3. **Best Practices**: ≥90 score
4. **SEO**: ≥80 score (presentations are less SEO-focused)

Key metrics:
- **LCP** (Largest Contentful Paint): < 2.5s
- **CLS** (Cumulative Layout Shift): < 0.1
- **FID** (First Input Delay): < 100ms

```bash
# Run Lighthouse CLI (if installed)
npx lighthouse https://robotdad.github.io/amplifier-module-stories/ \
  --output=html --output-path=./lighthouse-report.html
```

---

## Common Issues & Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| Text too small | Can't read on phone | Use `clamp()` with larger min |
| Cards don't stack | Horizontal scroll on phone | Use `auto-fit` grid |
| Nav dots too small | Hard to tap | Add `min-width: 16px` on touch |
| Layout shift | Content jumps on load | Set explicit dimensions |
| Address bar issues | Content cut off | Use `100dvh` not `100vh` |

---

## Sign-off

| Deck | Phone | Tablet | Desktop | Tester | Date |
|------|-------|--------|---------|--------|------|
| index.html | ☐ | ☐ | ☐ | | |
| cortex-amplifier-presentation.html | ☐ | ☐ | ☐ | | |
| shadow-environments-deck.html | ☐ | ☐ | ☐ | | |
| ecosystem-audit-deck.html | ☐ | ☐ | ☐ | | |
| session-forking-deck.html | ☐ | ☐ | ☐ | | |
| cost-optimization-deck.html | ☐ | ☐ | ☐ | | |
| deliberate-development-deck.html | ☐ | ☐ | ☐ | | |
| lazy-module-activation-deck.html | ☐ | ☐ | ☐ | | |
| notifications-deck.html | ☐ | ☐ | ☐ | | |
| attention-firewall-deck.html | ☐ | ☐ | ☐ | | |
| superpowers-deck.html | ☐ | ☐ | ☐ | | |
| vibecoding-deck.html | ☐ | ☐ | ☐ | | |
