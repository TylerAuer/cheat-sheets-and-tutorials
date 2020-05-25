# CSS NOTES

## Random Bits

- The `transition: ` property goes on the original object not, for example, the `:hover` selector
- Only apply transitions to `transform` and `opacity` for performance reasons
- `backface-visibility: hidden;` is a bugfix for flash or small jump at end of transitions
- rem units are relative to the root font-size. So if you set the font at 1.5 rem and the root font-size is 10px, then the font is shown at 15px.
- *em* and *rem* units are based on font sizes which are useful for building responsive sites

## How CSS "Cascades"

The "Cascading" in the name, Cascading Style Sheets comes from the ways in which browsers read code and determine which styles to apply to an element.

Usually, an element has many styles applied to it. For example, an `<a>` element likely has a default style, a universal style, and a more specific style when the `<a>` appears in a `<button>` or in a `<nav>`

The browser prioritizes based on the following from top to bottom:

1. **Importance**
   *USER is you or your browser*
   *AUTHOR is the code sent from the server*   
   1. User !important
   2. Author !important
   3. Author declarations
   4. User declarations
   5. Default browser declarations
2. **Specificity** (Check for most applicable styles of each type, if tied go to next)
   1. Inline styles
   2. IDs
   3. Classes
   4. Elements and pseudo-elements
3. **Source Order** - Last style in code. Can be affected by where a selector is in a `.css` file or the order in which the files are loaded

## How CSS Values are Processed

- When a property has different declared values, the cascade determines which value is used
- Every property has a value, even if nothing is declared or inherited. The default, when no value is declared or inherited, is the initial value
- Everything is converted to pixels at render
- root font-size (usually 16px) is set by USER

### Relative Units

- **% units** are based on the parent elements calculated value
- **Fonts**
  - **em** *for font* - based on parent's font-size
  - **em** *for length* - based on the current element's font-size
  - **rem** - always uses the root font size as a refernce (for length or font-size)
- **Viewport Units**
  - **vh** - 1% of viewport height
  - **vw** - 1% of viewport width

### Inheritance

A way of propegating property values from parent elements to their children. Designed to make code more maintainable and **should be used whenever possible**.

Not all properties are inherated, need to check the specifications of each property. 

Any cascaded value (value assigned with CSS selector) takes precendence over inherated values.

The computed value is inherited, not the declared value. For example, if a parent element has the property: `line-height: 150%`, 150% is **not** passed, instead the value that 150% is computed to be is passed.


Properties related to text are generally inherated, but borders, margins, and padding are generally not -- that would be annoying.

Can use `inherit` keyword to force inheritence of a specific property. This is often used in lieu of universal selectors because universal selectors might mess up plugins or external style sheets. Ex:
```css
*,
*::before,
*::after {
  /* Forces inheritance */
  box-sizing: inherit;
}

body {
  /* Sets box sizing which is inherated by all children recursively */
  box-sizing: border-box;
}
```

### Converting px to rem

#### Why use rem?

By using rem units, we create an easy way to change the size of everything using the global font-size. This is really handy for media queries and adjusting for mobile. Also, rescales everything nicely when the user zooms in with the browser.

Since `rem` is based on the root font-size in the html selector, setting that to 10px makes it easy to convert anything from px to rem. Just divide any pixel measurement by 10. But, setting the default font-size as a pixel value is a **bad idea** because it overrides users' browsers settings. People with bad vision will often set the default font-size to be larger, so you want to use a % value here. Setting the font-size to 100% will make the default size 100% of the user's browser setting. So, setting this at 62.5% converts a common 16px default font-size to a 10px size. This % approach still allows the user to "zoom" in on the page.

**rems are not supported below IE9**

<<<<<<< HEAD
## Website Rendering: The Visual Formatting Model
=======
### Website Rendering: The Visual Formatting Model
>>>>>>> 8aade837692441219535e3129c0bd5f804213b2a

An algorithm that calculates boxes and determines the layout of these boxex for each element in the render tree, in order to determine the final layout of the page.

Takes into account:

- Dimensions of boxes: box model
- Box type: inline, block...
- Positioning scheme: floats, positioning
- Stacking Contents
- Other elements of the render tree
- Viewport size, image dimensions

### The Box Model

Each and every element on the web page can be scene as a rectangular box with width, height, padding, border, and margin. But, these are optional. A border, for example, is not required.

The area outside of the content area but inside the border is known as the padding. Background-color and Background-image do cover the padding areas.

Total width includes the border-left, padding-left, defined width, padding-rigth, border-right.

Using `box-sizing: border-box` redefines the width and height to include everything but the margin

### Box Types

The box type is defined by the display property. Ex: `display: flex` or `display: inline-block`. All elements have default properties. `block` is usually the default display property.

#### Block-Level Boxes

- Take up 100% of the parent's width
- Vertical, one after another
- Box-model applies as described above

#### Inline

- Content distributed in lines
- Occupies only content's space
- No line-breaks
- No heights and widths -- can't use these properties here
- Paddings and margins on horizontal

#### Inline-block

- Mix of block and inline
- Occupy only contents space (like inline)
- No line breaks (like inline)
- Box-model applies as show (like block-level)

### Positioning Schemes

#### Normal Flow

- Default scheme when not floated and no absolute positioned. Still used with `position: relative`
- Elements laid out according to their source order

#### Floats

- Removed from the normal flow
- Text and inline elements wrap around the floated element
- The container will not adjust its height to the element (`clearfix` is the fix for this)

#### Absolute Positioning

- Element is removed from the normal flow
- No impact on surrounding content or elements
- We use `top`, `bottom`, `left`, `right`

### Stacking Context

Are like layers to "paint" the stack. Most often adjusted with z-index, but others affect it to.

## CSS Architecture, Components, and BEM

**Component Driven Design** - Divide page into modular parts that makes up the interface. Components should be resusable and independent.

Have a structure for naming the classes. **BEM** is a way of naming CSS classes.

### Block Element Modifier (BEM)

A **block** is a standalone component that is meaningful on its own.

An **element** is part of a block that has no meaning on its own.

A **modifier** is a defferent version of a block or an element

Uses very low specificity classes. Here are the examples:

```CSS
.block {}
.block__element {}
.block__element--modifier {}
```

### Architecture

**7-1 Pattern** 7 different folders for partial Sass files, and 1 main Sass file (or other CSS preprocessor) to import all other files into a compiled CSS stylesheet.

- `base/` - basic product definitions
- `components/` - 1 file for each componet
- `layout/` - overall layout
- `pages/` - styles for specific pages
- `themes/` - if you want to have different themes
- `abstracts/` - variables and mixins
- `vendors/` - all 3rd party css