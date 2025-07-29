## CSS Basics

- `CSS (Cascading Style Sheets)`
- used to `style and visually format` HTML content on web pages.
- controls `layout`, `colors`, `fonts`, `spacing`, `animations`, `responsiveness`, and more.
- `Syntax:` Selector { property: value; }

```css
p {
  color: red;
}
```

---

## CSS Comments

- used to `add explanatory notes` in the CSS code.

```css
/* This is a comment */
```

---

## How to Add CSS

| **Aspect**          | **Inline**                          | **Internal**                       | **External**             |
| ------------------- | ----------------------------------- | ---------------------------------- | ------------------------ |
| **Written in**      | `style` attribute.                  | `<style>` in `<head>`.             | Separate `.css` file.    |
| **Syntax Example**  | `<h1 style="color:red;">Hello</h1>` | `<style>h1 {color: blue;}</style>` | `h1 { color: green; }`   |
| **Scope**           | Single element.                     | One page.                          | Multiple pages.          |
| **Reusability**     | ❌ None.                            | ❌ Page-specific.                  | ✅ Fully reusable.       |
| **Maintainability** | ❌ Poor.                            | ⚠️ Medium.                         | ✅ Best (centralized).   |
| **Performance**     | ⚠️ Slightly faster.                 | ⚠️ Loads with HTML.                | ✅ Cached, faster.       |
| **Best for**        | Quick fixes/testing.                | Single-page styles.                | Full sites/pro projects. |
| **Readability**     | ❌ Messy.                           | ⚠️ Better.                         | ✅ Clean separation.     |

---

## CSS Selectors

- Used to `select elements` to apply styles.

![css-selector](./assets/css-selector-1.jpg)
![css-selector](./assets/css-selector-2.jpg)
![css-selector](./assets/css-selector-3.jpg)

---

## Specificity Hierarchy Table

| **Selector Type**       | **Example**                | **Specificity Value** | **Explanation**                                                                                     |
| ----------------------- | -------------------------- | --------------------- | --------------------------------------------------------------------------------------------------- |
| **Inline styles**       | `<div style="color:red;">` | **1000**              | Applied directly to the element in the `style` attribute. **Always wins** over other selectors.     |
| **ID selectors**        | `#main`                    | **100**               | Each ID used in a selector adds 100 to the score.                                                   |
| **Class selectors**     | `.box`, `.active`          | **10**                | Each class, attribute selector (`[type="text"]`), or pseudo-class (`:hover`, `:nth-child`) adds 10. |
| **Attribute selectors** | `[type="checkbox"]`        | **10**                | Same level as classes.                                                                              |
| **Pseudo-classes**      | `:hover`, `:first-child`   | **10**                | Also add 10 to the score.                                                                           |
| **Element selectors**   | `div`, `p`, `h1`           | **1**                 | Each element or pseudo-element (`::before`, `::after`) adds 1.                                      |
| **Universal selector**  | `*`                        | **0**                 | Has **no effect** on specificity.                                                                   |
| **Combinators**         | `div > p`, `ul li`         | **0**                 | `>`, `+`, `~`, whitespace do not add to specificity.                                                |

### **Important Notes**

- **Inline styles** override everything except `!important`.

---

## CSS Pseudo-Class

- `targets an element` based on its `state, position, or characteristics` — but `without modifying the DOM`.

**Syntax:**

```css
selector:pseudo-class {
  property: value;
}
```

### **Categories of Pseudo-Classes**

### **1. User-Action Pseudo-Classes** (interaction states)

| Pseudo-Class     | Example                | Purpose                                            |
| ---------------- | ---------------------- | -------------------------------------------------- |
| `:hover`         | `a:hover`              | When a user hovers over an element.                |
| `:active`        | `button:active`        | When an element is being clicked.                  |
| `:focus`         | `input:focus`          | When an element is focused.                        |
| `:focus-visible` | `button:focus-visible` | When focus is visible (e.g., keyboard navigation). |
| `:focus-within`  | `div:focus-within`     | When an element or its children have focus.        |
| `:target`        | `#section:target`      | When an element matches the page URL fragment.     |

### **2. Structural Pseudo-Classes** (based on position/structure)

| Pseudo-Class           | Example                 | Purpose                                 |
| ---------------------- | ----------------------- | --------------------------------------- |
| `:first-child`         | `li:first-child`        | First child of its parent.              |
| `:last-child`          | `li:last-child`         | Last child of its parent.               |
| `:only-child`          | `p:only-child`          | Element that is the only child.         |
| `:nth-child(n)`        | `li:nth-child(2n)`      | Selects based on position (1st, 2nd…).  |
| `:nth-last-child(n)`   | `li:nth-last-child(1)`  | Counts from the end.                    |
| `:first-of-type`       | `p:first-of-type`       | First occurrence of an element type.    |
| `:last-of-type`        | `p:last-of-type`        | Last occurrence of an element type.     |
| `:nth-of-type(n)`      | `p:nth-of-type(2)`      | nth occurrence of a specific element.   |
| `:nth-last-of-type(n)` | `p:nth-last-of-type(1)` | Counts from the end for a type.         |
| `:only-of-type`        | `p:only-of-type`        | The only element of its type in parent. |
| `:empty`               | `div:empty`             | No children (text or elements).         |

### **3. Logical & Relational Pseudo-Classes**

| **Pseudo-Class**     | **Example**         | **Purpose**                                                                                        |
| -------------------- | ------------------- | -------------------------------------------------------------------------------------------------- |
| **`:is()`**          | `:is(h1, h2, h3)`   | Matches **any element** in a list of selectors. **Doesn’t increase specificity** of its arguments. |
| **`:where()`**       | `:where(article p)` | Similar to `:is()`, but **always has zero specificity**. Good for **scoped defaults**.             |
| **`:not()`**         | `p:not(.highlight)` | Matches elements **that do NOT match** a selector.                                                 |
| **`:has()`**         | `div:has(img)`      | Matches an element **that contains** another matching element. Works like a **parent selector**.   |
| **`:nth-child()`**   | `li:nth-child(2n)`  | Selects **specific children** (even, odd, nth index).                                              |
| **`:nth-of-type()`** | `p:nth-of-type(2)`  | Selects the **nth child** of a specific **element type**.                                          |
| **`:only-child`**    | `p:only-child`      | Selects an element if it’s the **only child** in its parent.                                       |
| **`:empty`**         | `div:empty`         | Selects elements with **no children or text**.                                                     |

### **4. State & Validation Pseudo-Classes**

| Pseudo-Class    | Example              | Purpose                            |
| --------------- | -------------------- | ---------------------------------- |
| `:checked`      | `input:checked`      | Selected checkboxes/radio buttons. |
| `:enabled`      | `input:enabled`      | Inputs that are enabled.           |
| `:disabled`     | `input:disabled`     | Disabled inputs.                   |
| `:required`     | `input:required`     | Required form fields.              |
| `:optional`     | `input:optional`     | Optional form fields.              |
| `:valid`        | `input:valid`        | Input value is valid.              |
| `:invalid`      | `input:invalid`      | Input value is invalid.            |
| `:in-range`     | `input:in-range`     | Input value within allowed range.  |
| `:out-of-range` | `input:out-of-range` | Input value outside allowed range. |
| `:read-only`    | `input:read-only`    | Input marked as read-only.         |
| `:read-write`   | `input:read-write`   | Input editable by the user.        |

### **5. Resource & Content Pseudo-Classes**

| Pseudo-Class | Example      | Purpose                                 |
| ------------ | ------------ | --------------------------------------- |
| `:root`      | `:root`      | Represents the document root (HTML).    |
| `:lang()`    | `p:lang(en)` | Matches elements by language attribute. |

---

## CSS Pseudo-Element?

- `targets a specific part of an element` — like the first letter, line, or adds content `before/after` it.
- e.g., the first letter, before/after content, etc.

**Syntax:**

```css
selector::pseudo-element {
  property: value;
}
```

> **Note:** Modern CSS uses **double colons `::`** for pseudo-elements to differentiate them from pseudo-classes (single colon `:`).

## **List of Common Pseudo-Elements**

| **Pseudo-Element**       | **Example**                   | **Purpose**                                    |
| ------------------------ | ----------------------------- | ---------------------------------------------- |
| `::before`               | `p::before`                   | `Inserts content before` an element’s content. |
| `::after`                | `p::after`                    | `Inserts content after` an element’s content.  |
| `::first-letter`         | `p::first-letter`             | Styles the `first letter` of text.             |
| `::first-line`           | `p::first-line`               | Styles the `first line` of text.               |
| `::selection`            | `p::selection`                | Styles text `highlighted by the user`.         |
| `::placeholder`          | `input::placeholder`          | Styles the `placeholder text` in inputs.       |
| `::marker`               | `li::marker`                  | Styles `list item markers` (e.g., bullets).    |
| `::backdrop`             | `dialog::backdrop`            | Styles the `backdrop` of a `<dialog>` element. |
| `::file-selector-button` | `input::file-selector-button` | Styles the `file upload button`.               |
| `::cue`                  | `video::cue`                  | Styles `WebVTT captions` in media elements.    |
| `::part()`               | `my-element::part(header)`    | Styles `parts of a shadow DOM` component.      |

### **`::before` & `::after`**

- Add **extra content** without modifying HTML.

```css
button::before {
  content: "🔥";
  margin-right: 5px;
}
button::after {
  content: " →";
}
```

---

### 🧠 Pseudo-Class vs Pseudo-Element

| **Aspect**                                          | **Pseudo-Class**                                                                     | **Pseudo-Element**                                                                                             |
| --------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **Definition**                                      | Represents a `state` or `condition` of an element.                                   | Represents a `part of an element` or `generated content`.                                                      |
| **Syntax**                                          | Uses a **single colon** `:`. <br>_Example:_ `a:hover`                                | Uses **double colons** `::`. <br>_Example:_ `p::before`                                                        |
| **Purpose**                                         | Used to style elements `based on interaction, position, or logical conditions`.      | Used to `style specific parts of an element` or `insert virtual content`.                                      |
| **Examples**                                        | `:hover`, `:first-child`, `:not()`, `:focus`                                         | `::before`, `::after`, `::first-letter`, `::placeholder`                                                       |
| **Does it create new content?**                     | **No** – It only changes styles based on state.                                      | **Yes** – Can **generate content** using `content:` (e.g., `::before`, `::after`).                             |
| **Can it style part of an element’s text/content?** | **No** – Targets whole elements only.                                                | **Yes** – Can target **specific portions** (first letter, first line, list markers).                           |
| **Common Use Cases**                                | - Highlight links on `:hover`<br>- Style first/last child<br>- Exclude with `:not()` | - Add icons/text using `::before`/`::after`<br>- Style first letters<br>- Customize placeholder & list markers |

---

## CSS Colors

- `Define the color of elements` using different formats.
- Types of CSS Color Values

| **Type**          | **Example**                   | **Range / Notes**                                           | **Use Case**                           |
| ----------------- | ----------------------------- | ----------------------------------------------------------- | -------------------------------------- |
| **Named Colors**  | `color: red;`                 | 140+ predefined names (`red`, `blue`, `teal`).              | Quick & simple colors.                 |
| **Hexadecimal**   | `#ff0000`                     | `#RRGGBB` (0–255 per channel). Supports shorthand (`#f00`). | Most common for solid colors.          |
| **RGB**           | `rgb(255,0,0)`                | `rgb(R,G,B)` where each is `0–255`.                         | Easy to work with digital colors.      |
| **RGBA**          | `rgba(255,0,0,0.5)`           | Adds **alpha** channel (`0–1`) for transparency.            | Semi-transparent colors.               |
| **HSL**           | `hsl(0,100%,50%)`             | Hue (0–360), Saturation (0–100%), Lightness (0–100%).       | Human-friendly color adjustments.      |
| **HSLA**          | `hsla(0,100%,50%,0.5)`        | HSL + **alpha** channel for transparency.                   | Smooth color transitions.              |
| **CurrentColor**  | `border-color: currentColor;` | Uses the **element’s text color**.                          | Maintain consistent color scheme.      |
| **Transparent**   | `background: transparent;`    | Fully transparent color.                                    | Remove color without removing element. |
| **System Colors** | `Canvas`, `CanvasText`        | New in CSS Color Module Level 4.                            | Match OS/system theme colors.          |

---

## CSS Background

- Set `background styles for elements`
- CSS Background Properties Table

| **Property**                              | **Example**                                                 | **Purpose**                                                                                                      |
| ----------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **`background-color`**                    | `background-color: #f0f0f0;`                                | Sets a **solid background color**.                                                                               |
| **`background-image`**                    | `background-image: url('img.jpg');`                         | Adds an **image** or **gradient** as a background.                                                               |
| **`background-repeat`**                   | `background-repeat: no-repeat;`                             | Controls if/how the image repeats (**repeat**, **repeat-x**, **repeat-y**, **no-repeat**, **space**, **round**). |
| **`background-position`**                 | `background-position: center top;`                          | Sets the **starting position** of the background image.                                                          |
| **`background-size`**                     | `background-size: cover;`                                   | Sets the **scaling** of the image (**auto**, **cover**, **contain**, or custom values).                          |
| **`background-attachment`**               | `background-attachment: fixed;`                             | Determines if the background **scrolls** with the content (**scroll**, **fixed**, **local**).                    |
| **`background-clip`**                     | `background-clip: content-box;`                             | Defines the **painting area** (**border-box**, **padding-box**, **content-box**, **text**).                      |
| **`background-origin`**                   | `background-origin: content-box;`                           | Sets **where the background image starts** (**border-box**, **padding-box**, **content-box**).                   |
| **`background-blend-mode`**               | `background-blend-mode: multiply;`                          | Blends background layers with a chosen **blend mode** (e.g., multiply, overlay).                                 |
| **`background`**                          | `background: url('img.jpg') no-repeat center/cover;`        | **Shorthand** to set multiple background properties in one line.                                                 |
| **`background-image: linear-gradient()`** | `background-image: linear-gradient(to right, red, yellow);` | Adds a **gradient** as a background.                                                                             |

---

## CSS Gradient

| **Type**                      | **Function**                  | **Example**                                                      | **Purpose / When to Use**                                                                                                                   |
| ----------------------------- | ----------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Linear Gradient**           | `linear-gradient()`           | `linear-gradient(to right, red, yellow)`                         | Creates a **smooth color transition in a straight line** (horizontal, vertical, diagonal). Ideal for **backgrounds, buttons, and banners**. |
| **Radial Gradient**           | `radial-gradient()`           | `radial-gradient(circle, red, yellow)`                           | Creates a **color blend radiating from a center point**. Good for **spotlight effects, highlights, or circular backgrounds**.               |
| **Conic Gradient**            | `conic-gradient()`            | `conic-gradient(from 90deg, red, yellow, blue)`                  | Creates a **circular color sweep around a center point**. Great for **charts, dials, or artistic circular patterns**.                       |
| **Repeating Linear Gradient** | `repeating-linear-gradient()` | `repeating-linear-gradient(45deg, red 0 10px, blue 10px 20px)`   | Repeats a **linear gradient pattern**. Useful for **stripes, textures, or patterned backgrounds**.                                          |
| **Repeating Radial Gradient** | `repeating-radial-gradient()` | `repeating-radial-gradient(circle, #fff 0 10px, #ccc 10px 20px)` | Repeats a **radial gradient pattern**. Perfect for **polka dots, circular textures, or layered radial effects**.                            |

---

## Border CSS

- Define the border around elements.

| **Property**                       | **Example**                               | **Purpose / When to Use**                                                                                               |
| ---------------------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **`border`** (shorthand)           | `border: 2px solid black;`                | Sets **width, style, and color** in one line. Quick border styling.                                                     |
| **`border-width`**                 | `border-width: 1px 2px 3px 4px;`          | Controls **thickness** (can set individually for top/right/bottom/left).                                                |
| **`border-style`**                 | `border-style: solid dashed none dotted;` | Controls **line style**: `solid`, `dashed`, `dotted`, `double`, `groove`, `ridge`, `inset`, `outset`, `none`, `hidden`. |
| **`border-color`**                 | `border-color: red green blue yellow;`    | Sets **color** for each side individually.                                                                              |
| **`border-radius`**                | `border-radius: 10px;`                    | Rounds **corners** of borders (for circles, pills, smooth edges).                                                       |
| **`border-top/right/bottom/left`** | `border-top: 3px solid red;`              | Controls **individual sides** of a border.                                                                              |
| **`border-image`**                 | `border-image: url(border.png) 30 round;` | Uses an **image as a border** (decorative frames).                                                                      |
| **`outline`** (related)            | `outline: 2px dashed blue;`               | Adds a **border-like highlight outside the box** (does not affect layout).                                              |

---

## Text CSS

- `Style the text within elements`

| **Property**                    | **Example**                       | **Purpose / When to Use**                                                                   |
| ------------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------- |
| **`color`**                     | `color: #333;`                    | Sets **text color**.                                                                        |
| **`text-align`**                | `text-align: center;`             | Aligns text **(left, right, center, justify)**.                                             |
| **`text-transform`**            | `text-transform: uppercase;`      | Converts text to **uppercase, lowercase, or capitalize**.                                   |
| **`text-decoration`**           | `text-decoration: underline;`     | Adds **underline, overline, line-through** or removes them.                                 |
| **`text-decoration-color`**     | `text-decoration-color: red;`     | Sets **color of underline/decoration**.                                                     |
| **`text-decoration-style`**     | `text-decoration-style: wavy;`    | Makes decoration **solid, dotted, dashed, double, wavy**.                                   |
| **`text-decoration-thickness`** | `text-decoration-thickness: 3px;` | Sets **thickness** of underline/decoration.                                                 |
| **`text-shadow`**               | `text-shadow: 2px 2px 5px gray;`  | Adds **shadow** for depth or glow effects.                                                  |
| **`text-indent`**               | `text-indent: 50px;`              | Indents the **first line of a paragraph**.                                                  |
| **`letter-spacing`**            | `letter-spacing: 2px;`            | Controls **space between letters**.                                                         |
| **`word-spacing`**              | `word-spacing: 5px;`              | Controls **space between words**.                                                           |
| **`line-height`**               | `line-height: 1.8;`               | Controls **vertical space between lines**.                                                  |
| **`white-space`**               | `white-space: nowrap;`            | Controls **how text wraps** (nowrap, pre, pre-line, pre-wrap).                              |
| **`word-break`**                | `word-break: break-word;`         | Handles **word-breaking in narrow spaces**.                                                 |
| **`overflow-wrap`**             | `overflow-wrap: break-word;`      | Similar to `word-break` but better for natural wrapping.                                    |
| **`direction`**                 | `direction: rtl;`                 | Sets text direction **(ltr, rtl)**.                                                         |
| **`writing-mode`**              | `writing-mode: vertical-rl;`      | Displays text **vertically or horizontally**.                                               |
| **`text-overflow`**             | `text-overflow: ellipsis;`        | Adds `...` for **truncated text** (used with `white-space: nowrap;` & `overflow: hidden;`). |

---

## Fonts CSS

- `Set the font styles for text`

| **Property**                | **Example**                                 | **Purpose / When to Use**                                        |
| --------------------------- | ------------------------------------------- | ---------------------------------------------------------------- |
| **`font-family`**           | `font-family: "Roboto", Arial, sans-serif;` | Sets the **typeface**. Always use **fallback fonts**.            |
| **`font-size`**             | `font-size: 16px;`                          | Sets **text size** (use `px`, `em`, `rem`, `%`).                 |
| **`font-weight`**           | `font-weight: 700;`                         | Controls **thickness** of text (`normal`, `bold`, `100–900`).    |
| **`font-style`**            | `font-style: italic;`                       | Makes text **italic or normal**.                                 |
| **`font-variant`**          | `font-variant: small-caps;`                 | Converts text to **small caps** (e.g., “CSS” → “ᴄss”).           |
| **`font-stretch`**          | `font-stretch: condensed;`                  | Adjusts **font width** (`ultra-condensed` to `ultra-expanded`).  |
| **`line-height`**           | `line-height: 1.6;`                         | Controls **spacing between lines** for readability.              |
| **`letter-spacing`**        | `letter-spacing: 1px;`                      | Adjusts **spacing between letters**.                             |
| **`word-spacing`**          | `word-spacing: 4px;`                        | Adjusts **spacing between words**.                               |
| **`font-variant-numeric`**  | `font-variant-numeric: tabular-nums;`       | Controls **numeric display** (e.g., lining, old-style, tabular). |
| **`font-kerning`**          | `font-kerning: normal;`                     | Adjusts **spacing between characters** based on font metrics.    |
| **`font-feature-settings`** | `font-feature-settings: "liga" 1;`          | Enables **OpenType features** (ligatures, stylistic alternates). |
| **`@font-face`**            | See below                                   | Allows **custom fonts** to be loaded.                            |

---

## Height and Width CSS

- `Define dimensions of elements`

| **Property**       | **Example**               | **Purpose / When to Use**                                                                                            |
| ------------------ | ------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **`width`**        | `width: 300px;`           | Sets the **horizontal size** of an element.                                                                          |
| **`height`**       | `height: 200px;`          | Sets the **vertical size** of an element.                                                                            |
| **`min-width`**    | `min-width: 150px;`       | Ensures the element **doesn’t shrink below** a certain width.                                                        |
| **`max-width`**    | `max-width: 600px;`       | Ensures the element **doesn’t grow beyond** a certain width.                                                         |
| **`min-height`**   | `min-height: 100px;`      | Ensures the element **doesn’t shrink below** a certain height.                                                       |
| **`max-height`**   | `max-height: 400px;`      | Ensures the element **doesn’t grow beyond** a certain height.                                                        |
| **`box-sizing`**   | `box-sizing: border-box;` | Defines how height/width are calculated (**content-box** = excludes padding/border, **border-box** = includes them). |
| **`aspect-ratio`** | `aspect-ratio: 16/9;`     | Keeps **proportional dimensions** for elements (good for images/videos).                                             |

---

## Box Model

- Every HTML element is treated as a `box`, and the `CSS Box Model` defines how that box is structured in terms of:

### 🔍 Visualization (text version)

```
┌───────────────────────────────────────────────┐← Margin
│ ┌───────────────────────────────────────────┐←--- Border
│ │ ┌───────────────────────────────────────┐←----- Padding
│ │ │       📝 Content (text, image, etc.) │ │ │
│ │ └───────────────────────────────────────┘ │ │
│ └───────────────────────────────────────────┘ │
└───────────────────────────────────────────────┘
```

---

### 🧮 Box Model Properties

| **Layer**   | **Purpose**                                               | **Example**          |
| ----------- | --------------------------------------------------------- | -------------------- |
| **Content** | The `actual content area` (text, images).                 | `width`, `height`    |
| **Padding** | Creates space `inside the box`, between content & border. | `padding: 10px;`     |
| **Border**  | The `visible line surrounding padding & content`.         | `border: 2px solid;` |
| **Margin**  | Creates `space between elements`.                         | `margin: 20px;`      |

### `box-sizing` CSS property

| **Property** | **Value**               | **Description**                                                                                             | **Width & Height Includes** | **Example**                                                               |
| ------------ | ----------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------- | ------------------------------------------------------------------------- |
| `box-sizing` | `content-box` (default) | The default value where only the content is included in the width and height. Padding & border are `extra`. | Content only                | Width: 200px → Final width = 200px (content) + padding + border           |
| `box-sizing` | `border-box`            | Width and height include `content, padding, and border`. Useful for predictable layouts.                    | Content + Padding + Border  | Width: 200px → Final width = 200px total, internally adjusts content size |

### 🛠️ Universal Reset

To avoid box model inconsistencies across browsers:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

---

## CSS Margin Collapsing

- Margin collapsing is a behavior in CSS where vertical margins of certain elements combine (collapse) into a single margin, rather than adding together.

| **Scenario**                     | **Description**                                                            | **Example / Notes**                                                                                      |
| -------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Adjacent vertical margins**    | When two block elements' top and bottom margins meet (stacked vertically). | A `<div>` with `margin-bottom: 20px` followed by a `<p>` with `margin-top: 30px` → Total margin = `30px` |
| **Parent and first/last child**  | Margin between parent and first/last child block element.                  | If parent has no padding/border/overflow set, margins may collapse.                                      |
| **Empty block elements**         | An element with no content, padding, border, or height.                    | The element's vertical margins collapse with its parent.                                                 |
| **Nested elements with margins** | Margin between nested child and parent (top or bottom) may collapse.       | Parent and child margin collapse only if no border/padding/overflow/inline content                       |

---

## Box and Text Shadow

- Add shadows to boxes or text.
- `Box-Shadow:` `box-shadow: x-offset y-offset blur-radius color;`
- `Text-Shadow:` `text-shadow: x-offset y-offset blur-radius color;`

```css
box-shadow: 2px 2px 5px gray;
text-shadow: 1px 1px 2px black;`
```

---

## CSS Units

- define `how sizes (like width, padding, font-size, etc.) are measured`.
- There are two main types:

### 🔸 1. `Absolute Units` (Fixed Size)

These units are `not affected` by parent or screen size. They're best for print or when pixel-perfect precision is needed.

| Unit | Full Form   | Relative To          | Notes                                                       |
| ---- | ----------- | -------------------- | ----------------------------------------------------------- |
| `px` | pixels      | Screen pixels        | Most common unit. 1px = 1 device pixel on standard screens. |
| `pt` | point       | 1/72 of an inch      | Mostly used in print stylesheets.                           |
| `pc` | pica        | 12 points (1/6 inch) | Used in print design.                                       |
| `in` | inch        | 2.54 cm              | Rarely used in web.                                         |
| `cm` | centimeters | Physical cm          | Not practical for responsive design.                        |
| `mm` | millimeters | Physical mm          | Also rare in web design.                                    |

🧠 `Use Case for `px`:` UI layout spacing, borders, font-size (when you need precision).

### 🔹 2. `Relative Units` (Flexible / Responsive)

Relative units `adapt to context`, such as parent size or user settings (accessibility). These are preferred for `responsive design`.

#### ✅ Font-relative Units:

| Unit  | Relative To                         | Use Case                             |
| ----- | ----------------------------------- | ------------------------------------ |
| `em`  | Parent element’s font size          | Nested font sizing, padding, spacing |
| `rem` | Root element’s font size (`<html>`) | Consistent sizing across app         |
| `%`   | Parent’s size                       | Widths, paddings, font-sizes         |
| `ex`  | x-height of the font                | Rarely used                          |
| `ch`  | Width of `0` character              | Fixed-width designs, inputs          |

#### 🔁 Viewport-relative Units:

| Unit   | Relative To               | Use Case                             |
| ------ | ------------------------- | ------------------------------------ |
| `vw`   | 1% of viewport width      | Fluid typography, responsive layouts |
| `vh`   | 1% of viewport height     | Full-screen sections                 |
| `vmin` | 1% of smaller of vw or vh | Maintain layout aspect ratio         |
| `vmax` | 1% of larger of vw or vh  | Maintain max-fit in container        |

#### ⏱ Newer Units (L3+):

| Unit         | Description                                                                |
| ------------ | -------------------------------------------------------------------------- |
| `lvw`, `lvh` | Large viewport width/height (ignores overlays)                             |
| `svw`, `svh` | Small viewport width/height (accounts for overlays like mobile browser UI) |
| `dvw`, `dvh` | Dynamic viewport width/height (updates on resize)                          |

> ✅ Use `dvh` instead of `100vh` to avoid mobile issues like address bars cutting off content.

---

## CSS Links

- Style different link states.
- `States:` `a:link`, `a:visited`, `a:hover`, `a:active`.

```css
a:hover {
  color: green;
}
```

---

## CSS List

- Style list elements.
- `Properties:` `list-style-type`, `list-style-image`, `list-style-position`.

```css
list-style-type: circle;
```

---

## CSS Table

- Style table elements.
- `Properties:` `border-collapse`, `border-spacing`, `caption-side`.

```css
table {
  border-collapse: collapse;
}
```

---

## CSS Position

The `position` property determines how an element is positioned in the document flow and how it responds to the top, right, bottom, and left properties.

---

### 🧱 All Position Values

| **Value**  | **Description**                                                                                   | **How It’s Used**                                                                      | **Example**                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `static`   | `Default positioning`. Elements flow normally in the document.                                    | Does not respond to `top`, `right`, `bottom`, or `left` properties.                    | `div { position: static; }` (default — no special positioning)                |
| `relative` | Offsets the element `relative to its normal position`.                                            | Can use `top`, `left`, `bottom`, `right` to shift. `Space remains reserved`.           | `div { position: relative; top: 10px; left: 20px; }`                          |
| `absolute` | `Removes the element` from the normal flow. Positioned relative to nearest `non-static` ancestor. | Takes reference from nearest parent with `position: relative`, `absolute`, or `fixed`. | `div { position: absolute; top: 10px; left: 20px; }` inside a relative parent |
| `fixed`    | `Fixed to the viewport`. Doesn't move on scroll.                                                  | Always relative to browser window. Useful for sticky headers, modals, etc.             | `div { position: fixed; bottom: 0; right: 0; }` (e.g., fixed footer button)   |
| `sticky`   | Behaves like `relative` until a threshold is met, then like `fixed`.                              | Needs `top`, `left`, etc. and a scrollable container.                                  | `div { position: sticky; top: 0; }` (e.g., sticky navbar on scroll)           |

---

### 🧱 Stack Order & `z-index`

- Only elements with `position` values of `relative`, `absolute`, `fixed`, or `sticky` create a `stacking context` with `z-index`.
- `z-index` works `only` on positioned elements.

```css
.box1 {
  position: relative;
  z-index: 10;
}

.box2 {
  position: absolute;
  z-index: 5;
}
```

🧠 Higher `z-index` means closer to the viewer (on top).

---

## CSS Overflow

- Specify how content that overflows the container is handled.

| **Property**          | **Values**                                  | **Purpose / Behavior**                                        |
| --------------------- | ------------------------------------------- | ------------------------------------------------------------- |
| **`overflow`**        | `visible` (default)                         | Content **overflows** outside the container.                  |
|                       | `hidden`                                    | **Clips** extra content (invisible).                          |
|                       | `scroll`                                    | Always shows **scrollbars** (even if not needed).             |
|                       | `auto`                                      | Shows **scrollbars only when needed**.                        |
| **`overflow-x`**      | `visible` \| `hidden` \| `scroll` \| `auto` | Controls **horizontal overflow**.                             |
| **`overflow-y`**      | `visible` \| `hidden` \| `scroll` \| `auto` | Controls **vertical overflow**.                               |
| **`overflow-inline`** | `visible` \| `hidden` \| `scroll` \| `auto` | Controls **inline-axis overflow** (useful for writing modes). |
| **`overflow-block`**  | `visible` \| `hidden` \| `scroll` \| `auto` | Controls **block-axis overflow**.                             |
| **`text-overflow`**   | `clip` \| `ellipsis`                        | Defines **how clipped text is displayed** (e.g., `...`).      |
| **`white-space`**     | `nowrap`                                    | Often used with `text-overflow` to **prevent wrapping**.      |

---

## CSS Media Query

Media Queries let you apply CSS `only when specific conditions` (like screen width, resolution, orientation) are met.

> `"If the screen is less than 768px wide, apply these styles."`

### 🔤 Basic Syntax

```css
@media media-type and (condition) {
  /* CSS rules go here */
}
```

### ✅ Example:

```css
@media screen and (max-width: 768px) {
  body {
    background-color: lightblue;
  }
}
```

### 📦 Media Types

| Media Type | Description                     |
| ---------- | ------------------------------- |
| `all`      | Default, applies to all devices |
| `screen`   | Screens (phones, laptops)       |
| `print`    | Print preview or printed docs   |
| `speech`   | Screen readers                  |

### Conditions

| **Media Type/Feature**   | **Description**                                              | **Example**                                                                         |
| ------------------------ | ------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| `min-width`              | Applies styles when **viewport width is ≥ value**            | `@media (min-width: 768px) { body { background: lightblue; } }`                     |
| `max-width`              | Applies styles when **viewport width is ≤ value**            | `@media (max-width: 600px) { h1 { font-size: 20px; } }`                             |
| `min-height`             | Applies styles when **viewport height is ≥ value**           | `@media (min-height: 800px) { .hero { padding: 100px; } }`                          |
| `max-height`             | Applies styles when **viewport height is ≤ value**           | `@media (max-height: 500px) { .menu { display: none; } }`                           |
| `orientation`            | Detects **device orientation** (landscape or portrait)       | `@media (orientation: landscape) { .video { width: 100%; } }`                       |
| `resolution`             | Detects screen **pixel density** (useful for retina screens) | `@media (min-resolution: 192dpi) { .logo { background-image: url(logo@2x.png); } }` |
| `aspect-ratio`           | Detects ratio of width to height                             | `@media (aspect-ratio: 16/9) { .video { height: auto; } }`                          |
| `hover`                  | Detects if device **supports hover**                         | `@media (hover: hover) { button:hover { background: blue; } }`                      |
| `pointer`                | Detects type of input device (fine, coarse, none)            | `@media (pointer: coarse) { .btn { padding: 20px; } }`                              |
| `prefers-color-scheme`   | Detects user’s **light/dark mode** preference                | `@media (prefers-color-scheme: dark) { body { background: #111; color: #eee; } }`   |
| `prefers-reduced-motion` | Detects user preference for **reduced animations**           | `@media (prefers-reduced-motion: reduce) { * { animation: none !important; } }`     |

```css
/* Portrait phones */
@media (max-width: 480px) {
  ...;
}

/* Landscape phones */
@media (min-width: 481px) and (max-width: 767px) {
  ...;
}

/* Tablets */
@media (min-width: 768px) and (max-width: 1023px) {
  ...;
}

/* Laptops & desktops */
@media (min-width: 1024px) {
  ...;
}
```

---

## CSS Transitions

### ✅ Used to animate changes from one state to another (e.g., hover, click).

### 🔹 Syntax:

```css
transition: property duration timing-function delay;
```

### 🔹 Example:

```css
.button {
  background: blue;
  transition: background 0.3s ease-in-out;
}

.button:hover {
  background: green;
}
```

### 🔹 Common Properties:

| Property                     | Description                                                           |
| ---------------------------- | --------------------------------------------------------------------- |
| `transition-property`        | What you want to animate (e.g., `all`, `opacity`, `transform`)        |
| `transition-duration`        | How long it takes (e.g., `0.5s`, `300ms`)                             |
| `transition-timing-function` | Speed curve (`ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier`) |
| `transition-delay`           | Wait time before starting                                             |

---

## CSS Animations

### ✅ Used for more complex, continuous, or multi-step animations.

### 🔹 Requires:

- `@keyframes` rule to define the animation
- `animation` properties to run it

### 🔹 Example:

```css
@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-30px);
  }
  100% {
    transform: translateY(0);
  }
}

.ball {
  animation: bounce 1s ease infinite;
}
```

---

### 🔹 Animation Properties:

| Property                    | Purpose                                               |
| --------------------------- | ----------------------------------------------------- |
| `animation-name`            | Name of the `@keyframes`                              |
| `animation-duration`        | How long the animation takes                          |
| `animation-timing-function` | Speed curve                                           |
| `animation-delay`           | Delay before it starts                                |
| `animation-iteration-count` | How many times (`1`, `infinite`)                      |
| `animation-direction`       | `normal`, `reverse`, `alternate`, `alternate-reverse` |
| `animation-fill-mode`       | `none`, `forwards`, `backwards`, `both`               |
| `animation-play-state`      | `running`, `paused`                                   |

---

### 🆚 Transition vs Animation

| Feature | `transition`                              | `animation`                           |
| ------- | ----------------------------------------- | ------------------------------------- |
| Trigger | Requires interaction (hover, focus, etc.) | Can run automatically                 |
| Steps   | One step (start → end)                    | Multiple steps (keyframes)            |
| Repeats | No                                        | Yes (`infinite`)                      |
| Delay   | Yes                                       | Yes                                   |
| Control | Less control                              | Full control (pause, direction, etc.) |

---

## CSS Display

The `display` property defines how an element is `visually formatted` in the document flow.

### 🔸 Common Values (Without Flex/Grid):

| Value                              | Description                                                          |
| ---------------------------------- | -------------------------------------------------------------------- |
| `block`                            | Takes full width, starts on a new line (e.g., `div`, `h1`)           |
| `inline`                           | Takes only the content width, doesn’t break line (e.g., `span`, `a`) |
| `inline-block`                     | Like `inline`, but allows setting `width`, `height`, `margin`, etc.  |
| `none`                             | Completely hides the element (no space reserved)                     |
| `table`, `table-row`, `table-cell` | Makes elements behave like a table (used before Grid)                |

---

### CSS Flexbox

Flexbox (`Flexible Box Layout`) is a `1D layout system` for arranging elements in `rows or columns`, allowing for `dynamic sizing, alignment, and spacing`.

> `Best for:` Toolbars, navigation bars, cards, buttons, grids (1D).

## **Flexbox Main Properties (Parent – `display: flex`)**

| **Property**          | **Values**                                                                                    | **Purpose**                                             |
| --------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **`display`**         | `flex` / `inline-flex`                                                                        | Turns an element into a **flex container**.             |
| **`flex-direction`**  | `row` (default), `row-reverse`, `column`, `column-reverse`                                    | Defines **main axis direction**.                        |
| **`flex-wrap`**       | `nowrap` (default), `wrap`, `wrap-reverse`                                                    | Controls **wrapping** of flex items.                    |
| **`flex-flow`**       | `<direction> <wrap>`                                                                          | **Shorthand** for `flex-direction` + `flex-wrap`.       |
| **`justify-content`** | `flex-start` (default), `flex-end`, `center`, `space-between`, `space-around`, `space-evenly` | Aligns items **along the main axis**.                   |
| **`align-items`**     | `stretch` (default), `flex-start`, `flex-end`, `center`, `baseline`                           | Aligns items **along the cross-axis**.                  |
| **`align-content`**   | `stretch`, `flex-start`, `flex-end`, `center`, `space-between`, `space-around`                | Aligns **multiple lines** of flex items (when wrapped). |

## **Flexbox Item Properties (Children)**

| **Property**      | **Values**                                                        | **Purpose**                                                         |
| ----------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| **`flex`**        | `flex: 1;` or `flex: 2 1 200px;`                                  | **Shorthand** for `flex-grow`, `flex-shrink`, `flex-basis`.         |
| **`flex-grow`**   | `0` (default), `1`, `2`…                                          | Defines **how much space an item can grow** relative to others.     |
| **`flex-shrink`** | `1` (default), `0`                                                | Defines **how much an item can shrink** when space is limited.      |
| **`flex-basis`**  | `auto` (default), `200px`                                         | Sets the **initial size** of a flex item before distributing space. |
| **`align-self`**  | `auto`, `flex-start`, `flex-end`, `center`, `baseline`, `stretch` | **Overrides `align-items`** for a single item.                      |
| **`order`**       | `0` (default), `1`, `2`…                                          | Changes the **visual order** of items.                              |

## **Example Flexbox Layout**

```css
.container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
.item {
  flex: 1 1 200px; /* grow, shrink, basis */
}
```

## **Visual Axis**

- **Main Axis:** Controlled by `flex-direction`.
- **Cross Axis:** Perpendicular to the main axis.

Example:

- `flex-direction: row` → Main axis = horizontal.
- `flex-direction: column` → Main axis = vertical.

## **Common Flexbox Use Cases**

- **Navigation bars** → `justify-content: space-between;`
- **Cards/Grids** → `flex-wrap: wrap;` + `flex-basis`.
- **Centering** → `justify-content: center; align-items: center;`.
- **Reordering items** → `order`.

## **Quick Flex Shorthands**

```css
flex: 1; /* grow:1, shrink:1, basis:0 */
flex: 0 0 100px; /* no grow, no shrink, fixed width */
```

## ![flex](./assets/flex.png)

---

## CSS Grid?

`CSS Grid` is a 2-dimensional layout system in CSS that allows you to layout items in `rows and columns`, making it perfect for `complex responsive designs`.

- Unlike Flexbox (1D), `Grid handles both rows & columns simultaneously`.
- **Best for:** **Page layouts, dashboards, galleries, and complex responsive designs.**

## **Grid Container Properties (Parent – `display: grid`)**

| **Property**                               | **Values / Example**                                | **Purpose**                                            |
| ------------------------------------------ | --------------------------------------------------- | ------------------------------------------------------ |
| **`display`**                              | `grid` / `inline-grid`                              | Turns an element into a **grid container**.            |
| **`grid-template-columns`**                | `grid-template-columns: 200px 1fr 2fr;`             | Defines **column sizes** (fixed, fraction `fr`, auto). |
| **`grid-template-rows`**                   | `grid-template-rows: 100px auto;`                   | Defines **row sizes**.                                 |
| **`grid-template-areas`**                  | `"header header" "sidebar main"`                    | Defines **named layout areas**.                        |
| **`grid-template`**                        | Combines **rows, columns, and areas** in shorthand. |                                                        |
| **`column-gap` / `row-gap`**               | `column-gap: 20px; row-gap: 10px;`                  | Sets spacing between **columns/rows**.                 |
| **`gap`**                                  | `gap: 20px;`                                        | Shorthand for row & column gap.                        |
| **`justify-items`**                        | `start` / `end` / `center` / `stretch`              | Aligns **grid items horizontally** in their cells.     |
| **`align-items`**                          | `start` / `end` / `center` / `stretch`              | Aligns **grid items vertically** in their cells.       |
| **`justify-content`**                      | `start` / `end` / `center` / `space-between`        | Aligns **the entire grid horizontally**.               |
| **`align-content`**                        | Same values as above                                | Aligns **the entire grid vertically**.                 |
| **`grid-auto-rows` / `grid-auto-columns`** | `grid-auto-rows: 150px;`                            | Defines size for **implicitly created rows/columns**.  |
| **`grid-auto-flow`**                       | `row` / `column` / `dense`                          | Controls **auto-placement of items**.                  |

## **Grid Item Properties (Children)**

| **Property**       | **Example**                            | **Purpose**                         |
| ------------------ | -------------------------------------- | ----------------------------------- |
| **`grid-column`**  | `grid-column: 1 / 3;`                  | Spans **columns** (`start / end`).  |
| **`grid-row`**     | `grid-row: 2 / 4;`                     | Spans **rows**.                     |
| **`grid-area`**    | `grid-area: header;`                   | Places an item in a **named area**. |
| **`justify-self`** | `start` / `end` / `center` / `stretch` | Aligns **one item horizontally**.   |
| **`align-self`**   | Same values as above                   | Aligns **one item vertically**.     |

## **Example: Basic Grid Layout**

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 1fr;
  grid-template-rows: 100px auto 50px;
  gap: 10px;
}

.item1 {
  grid-column: 1 / 4;
} /* Full-width header */
.item2 {
  grid-row: 2 / 4;
} /* Sidebar spanning 2 rows */
```

## **Using `grid-template-areas`**

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 80px auto 50px;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  gap: 10px;
}
.header {
  grid-area: header;
}
.sidebar {
  grid-area: sidebar;
}
.main {
  grid-area: main;
}
.footer {
  grid-area: footer;
}
```

## **Common Units in Grid**

- **`px`** → Fixed size.
- **`%`** → Relative to container.
- **`fr`** → Fraction of available space.
- **`auto`** → Size based on content.
- **`minmax()`** → Dynamic sizing (e.g., `minmax(200px, 1fr)`).
- **`repeat()`** → Repeat pattern (e.g., `repeat(3, 1fr)`).

## **Best Practices**

- Use **`fr`** for flexible layouts.
- Use **`minmax()`** for responsive grids.
- Use **named areas** for semantic layouts.
- Use **`auto-fit` / `auto-fill`** for dynamic grid columns.

### **Quick Auto-Fit Example (Responsive Cards)**

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

**Flexbox vs Grid:**

- **Flexbox:** 1D layout (row _or_ column).
- **Grid:** 2D layout (row **and** column).

## ![grid](./assets/grid.png)

---

## CSS Functions?

`CSS Functions` are expressions that return a value, often used inside property values. They can perform `calculations`, `color manipulations`, `transformations`, and more.

### 🧮 1. `calc()` — Calculations in CSS

```css
width: calc(100% - 60px);
```

✅ Supports basic math operations: `+`, `-`, `*`, `/`
✅ Works with different units (e.g., `% + px`)

> Useful for responsive layouts, dynamic spacing.

### 🎨 2. `var()` — CSS Variables

```css
:root {
  --main-color: #3498db;
}

.button {
  background: var(--main-color);
}
```

✅ Allows you to reuse values and build themes.
✅ Combine with `calc()` and fallbacks:

```css
padding: var(--spacing, 10px); /* fallback = 10px */
```

### 🎨 3. `rgb()`, `rgba()`, `hsl()`, `hsla()` — Colors

```css
background-color: rgb(255, 99, 71);
color: rgba(0, 0, 0, 0.6); /* with alpha */
background: hsl(120, 100%, 50%);
```

✅ `rgba` and `hsla` allow transparency
✅ HSL is great for theming & light/dark manipulation

### 📐 4. `url()` — External resources (e.g., images, fonts)

```css
background-image: url("bg.jpg");
font-face {
  src: url("myfont.woff2");
}
```

### 📏 5. `min()`, `max()`, and `clamp()` — Responsive Sizing

#### ✅ `min()`: Chooses the `smaller` of two values

```css
width: min(100%, 500px);
```

#### ✅ `max()`: Chooses the `larger` of two values

```css
width: max(50vw, 300px);
```

#### ✅ `clamp(min, preferred, max)`

```css
font-size: clamp(14px, 2vw, 24px);
```

> 💡 `clamp()` is great for responsive typography.

### 🌈 6. `linear-gradient()` & `radial-gradient()`

```css
background: linear-gradient(to right, #00f, #0ff);
background: radial-gradient(circle, #f00, #ff0);
```

✅ Creates smooth transitions between colors
✅ Can be layered and animated

### 🔁 7. `repeat()` — Grid template repetition

```css
grid-template-columns: repeat(3, 1fr);
```

> 💡 Saves you from writing `1fr 1fr 1fr`

### 📦 8. `attr()` — Attribute-based styling (only for `content`)

```css
a::after {
  content: attr(href);
}
```

> 💡 Limited support — works mostly in `content`

### 🧭 9. `translate()`, `scale()`, `rotate()` — Transform functions

```css
transform: translateX(20px) scale(1.2) rotate(45deg);
```

✅ Use in animations, hover effects, or UI transitions.

### 🌀 10. `cubic-bezier()` — Custom timing functions

```css
transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
```

✅ Creates smooth animations with custom easing.

### 📑 Summary Table

| Function            | Purpose                     |
| ------------------- | --------------------------- |
| `calc()`            | Math with mixed units       |
| `var()`             | CSS variables               |
| `rgb()`, `hsl()`    | Color definitions           |
| `url()`             | External assets             |
| `min()`/`max()`     | Responsive sizing           |
| `clamp()`           | Min-preferred-max sizing    |
| `repeat()`          | Grid repetition             |
| `attr()`            | Pulls attribute values      |
| `linear-gradient()` | Gradient backgrounds        |
| `transform()`       | 2D/3D transformations       |
| `cubic-bezier()`    | Custom easing in animations |

### ⚠️ Tips

- ✅ Combine `var()` with `calc()` and `clamp()` for powerful dynamic layouts.
- 🧪 Always test cross-browser support (some features like `attr()` have limits).
- 🎯 Use `clamp()` for fluid typography and layout padding/margins.

---
