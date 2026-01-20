# QA Test Checklist - Social Proof Widget

A practical checklist to verify the Social Proof Widget app before considering the sprint done.

---

## Pre-Testing Setup

- [ ] App is deployed and running
- [ ] Test store is available with the app installed
- [ ] Have access to Shopify admin dashboard
- [ ] Browser DevTools ready for inspection

---

## 1. Code Quality Checks

Run these commands in the project root:

### TypeScript & Linting
```bash
# Type checking
npm run typecheck

# Linting
npm run lint
```

- [ ] TypeScript compiles without errors
- [ ] No ESLint errors or warnings
- [ ] No console errors in browser DevTools during app usage

---

## 2. Functionality Testing

### Widget Popup Display

- [ ] Popup appears on storefront pages
- [ ] Popup shows correct product/activity information
- [ ] Popup auto-dismisses after configured timeout
- [ ] Close button (X) dismisses popup immediately
- [ ] Popup respects position setting (bottom-left, bottom-right, top-left, top-right)

### Live Visitor Counter

- [ ] Counter appears on product pages
- [ ] Counter displays visitor count number
- [ ] Counter updates without page refresh
- [ ] Counter styling matches configured theme

### Demo Mode

- [ ] Demo mode toggle works in settings
- [ ] When enabled: shows simulated data on storefront
- [ ] When disabled: shows real data only (or nothing if no activity)

---

## 3. Admin UI Testing

### Dashboard (`/app`)

- [ ] Page loads without errors
- [ ] Statistics/metrics display correctly
- [ ] Navigation to settings works
- [ ] Any charts or graphs render properly

### Settings Page (`/app/settings`)

- [ ] Page loads without errors
- [ ] All form fields are interactive
- [ ] Toggle switches work (on/off states save)
- [ ] Position selector updates preview
- [ ] Color/theme options apply correctly
- [ ] Save button persists changes
- [ ] Changes reflect on storefront after save
- [ ] Form validation shows errors for invalid inputs

### Settings Persistence

- [ ] Refresh page - settings remain saved
- [ ] Log out and back in - settings persist
- [ ] Changes in admin reflect on storefront

---

## 4. API Testing

Replace `{shop}` with your test store domain (e.g., `test-store.myshopify.com`).
Replace `{productId}` with a valid product ID from your store.

### Settings Endpoint
```bash
curl "https://your-app-url.com/api/settings?shop={shop}"
```
- [ ] Returns 200 status
- [ ] Response contains widget configuration JSON
- [ ] Response includes: enabled, position, timing settings

### Counter Endpoint
```bash
curl "https://your-app-url.com/api/storefront/counter?shop={shop}&productId={productId}"
```
- [ ] Returns 200 status
- [ ] Response contains visitor count data
- [ ] Count is a valid number (>= 0)

### Activity Feed Endpoint
```bash
curl "https://your-app-url.com/api/storefront/activity?shop={shop}"
```
- [ ] Returns 200 status
- [ ] Response contains activity array
- [ ] Activities have required fields (type, timestamp, etc.)

### Demo Data Endpoint
```bash
curl "https://your-app-url.com/api/demo-data?type=activity&shop={shop}"
```
- [ ] Returns 200 status
- [ ] Response contains demo activity data
- [ ] Data format matches real activity format

### Error Handling
- [ ] Invalid shop parameter returns appropriate error
- [ ] Missing required params return 400 status
- [ ] Unauthorized requests handled gracefully

---

## 5. Mobile Testing

Test on actual devices or browser DevTools mobile emulation.

### Responsive Display

- [ ] Widget popup displays correctly on mobile viewport
- [ ] Popup doesn't overflow screen edges
- [ ] Text is readable without zooming
- [ ] Close button is tappable (adequate size)

### Touch Interactions

- [ ] Popup can be dismissed by tapping X
- [ ] No accidental dismissals from scroll
- [ ] Counter is visible and readable on product pages

### Test Viewports
- [ ] iPhone SE (375px width)
- [ ] iPhone 12/13 (390px width)
- [ ] Android medium (360px width)
- [ ] Tablet portrait (768px width)

---

## 6. Performance Testing

### Lighthouse Audit

Run Lighthouse in Chrome DevTools on a storefront page with widget:

- [ ] Performance score >= 70
- [ ] No render-blocking resources from widget
- [ ] Widget script size < 50KB (gzipped)

### Load Time Impact

- [ ] Page load time increase < 500ms with widget
- [ ] Widget doesn't block First Contentful Paint
- [ ] No layout shifts caused by widget (CLS)

### Network Requests

- [ ] Widget makes minimal API calls
- [ ] API responses are cached appropriately
- [ ] No failed network requests in DevTools

---

## 7. Theme Compatibility

Test widget on these Shopify themes:

### Dawn (Default Theme)
- [ ] Widget displays correctly
- [ ] No CSS conflicts
- [ ] Counter appears on product pages

### Debut (Popular Free Theme)
- [ ] Widget displays correctly
- [ ] No CSS conflicts
- [ ] Counter appears on product pages

### Store's Active Theme
- [ ] Widget displays correctly
- [ ] No CSS conflicts
- [ ] Counter appears on product pages

---

## 8. Edge Cases

- [ ] Widget handles empty activity (no recent purchases)
- [ ] Long product names truncate gracefully
- [ ] Special characters in names display correctly
- [ ] Widget works with product variants
- [ ] Multiple browser tabs don't cause issues

---

## Final Sign-Off

| Area | Status | Notes |
|------|--------|-------|
| Code Quality | [ ] Pass | |
| Functionality | [ ] Pass | |
| Admin UI | [ ] Pass | |
| API Endpoints | [ ] Pass | |
| Mobile | [ ] Pass | |
| Performance | [ ] Pass | |
| Theme Compatibility | [ ] Pass | |

**Tested By:** _______________
**Date:** _______________
**App Version:** _______________

---

## Notes

_Record any issues, observations, or follow-up items here:_

1.
2.
3.
