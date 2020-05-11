# CSS NOTES

## Random Bits

- The `transition: ` property goes on the original object not, for example, the `:hover` selector
- Only apply transitions to `transform` and `opacity` for performance reasons
- `backface-visibility: hidden;` is a bugfix for flash or small jump at end of transitions

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
