
# Shoplane Compatibility Report

A detailed browser and device compatibility audit for the Shoplane e-commerce website.  
🔗 [Live Site](https://shoplane-by-lassie.netlify.app)

## ✅ Tested Browsers & Devices
- Chrome, Firefox, Edge, Safari (Mac & iOS)
- Desktop, tablet, mobile modes

---

## Issues Found

### 1. ✅ Fixed – Missing viewport `<meta>`
- **What:** No scaling on mobile  
- **Fix:**  
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1">
  ```

### 2. ✅ Fixed – Content overflow at ≤375px
- **Symptoms:** Horizontal scroll  
- **Fix:**  
  ```css
  body { overflow-x: hidden; }
  .product-card, img { max-width: 100%; box-sizing: border-box; height: auto; }
  ```

### 3. ✅ Fixed – Nav toggle unreliable on iOS
- **Symptoms:** Menu stays open  
- **Fix:** Improved JS toggle logic and added link listeners  
  ```js
  const toggleNav = () => document.body.classList.toggle("nav-open");
  document.querySelector(".nav-toggle").addEventListener("click", toggleNav);
  document.querySelectorAll(".nav-link").forEach(el =>
    el.addEventListener("click", toggleNav)
  );
  ```

### 4. ✅ Fixed – Missing alts & broken images
- **Symptoms:** Console warnings  
- **Fix:** Added `alt` attributes and verified image paths

### 5. ✅ Fixed – Small touch targets
- **Symptoms:** Hard to tap on mobile  
- **Fix:**  
  ```css
  .slider-button {
    min-width: 44px;
    min-height: 44px;
    touch-action: manipulation;
  }
  ```

---

## Recommendations
- Normalize CSS for cross-browser consistency
- Enhance accessibility with semantic HTML & ARIA
- Lazy-load and responsive images
- Use `event.composedPath()` and polyfills
- Automate testing with BrowserStack or Lighthouse

## 🔍 Lighthouse Audit (Optional)
> You can add your scores here after running Lighthouse in Chrome DevTools.
