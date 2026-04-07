# 🪑 Modern Chair

A sleek, interactive **product detail page** for a modern furniture item — built with pure **HTML & CSS**. This project showcases a visually polished UI with dynamic color selection, tabbed content switching, and a responsive layout, all without any JavaScript frameworks.

---

## 📸 Preview

| Details Tab | Description Tab | Color Variant |
|:-----------:|:---------------:|:-------------:|
| ![Details Tab](./images/details.png) | ![Description Tab](./images/description.png) | ![Taupe Variant](./images/color.png) |

> **Note:** Place the three screenshot images inside an `assets/` folder in the project root and name them `preview-details.png`, `preview-description.png`, and `preview-taupe.png`.

---

## 🎯 Project Objective

The goal of this project was to recreate a **high-fidelity product page UI** — the kind you'd find on a premium e-commerce furniture website — using only HTML and CSS. The challenge was to implement interactive behaviors (tab switching, color selection with live feedback) that are typically handled by JavaScript, relying instead on CSS's `:checked` pseudo-class and sibling combinators.

---

## ✨ Key Features

- **Live Color Selection** — Six fabric swatches (Crimson, Charcoal, Slate Blue, Sky Blue, Taupe, Olive) update the chair's cushion appearance in real time using CSS `input[type="radio"]` tricks — no JavaScript required.
- **Tabbed Content Panel** — Toggle between a *Description* prose view and a *Details* specs grid (dimensions + weight) using pure CSS tab logic.
- **Sale Price Display** — Original price shown with a strikethrough alongside the discounted price, styled for visual hierarchy.
- **Dimension Specs Grid** — Clean four-column layout displaying Length, Width, Height, and Weight with large numerals and subscript units.
- **Add to Cart Button** — A styled CTA button that adapts its color to match the currently selected fabric swatch.
- **Warm Gradient Background** — Full-viewport coral-to-salmon gradient that creates a cohesive, editorial product photography feel.
- **Zero JavaScript** — Every interactive element is powered purely by CSS (`:checked`, `~` sibling combinator, `:target`, `label` for elements).

---

## 🗂️ Project Structure

```
Modern-Chair/
└── 09 - Modern Chair/
    ├── index.html        # Main product page markup
    ├── style.css         # All styling, interactions, and color logic
    └── assets/
        └── chair.png     # Product image (dark wood frame chair)
```

The project lives inside a numbered folder (`09 - Modern Chair`) consistent with a series of UI challenge exercises.

---

## ⚙️ How It Works

### Color Switching (CSS-only)
Hidden `<input type="radio">` elements are paired with visible `<label>` swatches. When a swatch is selected, CSS sibling combinators (`~`) target the chair cushion element and swap its `background-color` or `background-image`. The "Add to Cart" button color is also updated to match.

```css
#color-blue:checked ~ .product-image .cushion {
  background-color: #4a90b8;
}
#color-blue:checked ~ .add-to-cart {
  background-color: #4a90b8;
}
```

### Tab Switching (CSS-only)
Two radio inputs control which content panel is visible — the description paragraph or the specs grid — using the same `:checked ~ sibling` pattern.

```css
#tab-details:checked ~ .tab-content .details { display: grid; }
#tab-details:checked ~ .tab-content .description { display: none; }
```

---

## 🧩 Challenges & Optimizations

### Challenge 1 — Interactive State Without JavaScript
**Problem:** Implementing color and tab switching without JS is not a common pattern and requires careful DOM structuring. The radio inputs must be siblings (or ancestors) of the elements they control — deeply nested markup breaks the sibling combinator.

**Optimization:** The entire interactive region was restructured so all `<input>` elements are placed high in the DOM, allowing `~` selectors to reach both the chair image and the button. This required rethinking the HTML hierarchy before writing a single line of CSS.

---

### Challenge 2 — Cushion Color Isolation
**Problem:** Changing the cushion color without affecting the chair frame meant the chair couldn't simply be one image — a solid `<img>` can't have part of it recolored via CSS.

**Optimization:** The cushion was isolated as a separate absolutely-positioned `<div>` layered on top of the chair image using `position: absolute`. CSS `border-radius` and careful sizing gave it an organic seat shape. This made per-color CSS rules clean and trivial to extend.

---

### Challenge 3 — Consistent Swatch Selection Feedback
**Problem:** Showing which swatch is currently active required a visible ring or highlight — but native radio inputs are styled inconsistently across browsers.

**Optimization:** All native radio inputs are hidden (`display: none`). The `<label>` elements act as the visible swatches. The active state is shown using a CSS `outline` or `box-shadow` ring applied when the associated input is `:checked`, giving full cross-browser control over appearance.

---

### Challenge 4 — Typography Scale for Specs
**Problem:** The spec numbers (80, 65, 90, 17.6) needed to feel large and dominant, while their units (cm, lbs) and labels (Length, Width…) needed to sit at a much smaller scale — a two-tier typographic hierarchy within one element.

**Optimization:** Each spec uses a `<span>` inside the number element for the unit suffix, styled with a significantly smaller `font-size` and `vertical-align: baseline`. The label sits in a separate `<p>` below. This keeps the HTML semantic while giving full typographic control in CSS.

---

## 🛠️ Tech Stack

| Technology | Usage |
|------------|-------|
| HTML5 | Semantic page structure, form inputs for state |
| CSS3 | Layout (Flexbox), interactions (`:checked`), gradients, transitions |

No build tools, no frameworks, no JavaScript — just a browser and a text editor.

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/HEYDEV001/Modern-Chair.git

# Navigate into the project folder
cd "Modern-Chair/09 - Modern Chair"

# Open in your browser
open index.html
```

Or simply drag `index.html` into any modern browser.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
