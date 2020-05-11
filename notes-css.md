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

