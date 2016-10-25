# Enigma

_Decypher web typography and vertical rhytm_

Enigma is small sass tool for better web typography. Its mixin and functions help you to ensure all text elements are in harmonious proportions, on same baseline and maintains consistent vertical rhythm.

Enigma is heavely inspired by [Modular Scale](http://www.modularscale.com/) from [Tim Brown](https://twitter.com/nicewebtype). If you want to know what Modular Scale is or need more information about web typography you should definetely check some of his talks.

Enigma doesn't come with fonts or typography templates, for ready made solutions you may check other tools (like [Gutenberg](https://matejlatin.github.io/Gutenberg/)). In Enigma it is up to you to setup it according your needs as every project is unique and it's typography should be treated as such. I build this tool for my need of easy and effective way how to use modular scales and different font-sizes with ease without all the difficult calculations for line height, font-size etc. It is perfect tool for keeping your vertical rhythm consistent and prepare good looking typography with very little effort.

All math is handled by Enigma. All you have to do is to put in few basic numbers and enjoy the results - harmonious font sizes and vertycal rhythm.

## How to use it

Include the sass files from `dist/` folder and add `_enigma.scss` into your main sass file and you are ready to go.

Enigma offers few functions and one mixin to make setting up typography and vertycal rhythm easy. All you have to do is to give Enigma some basic settings for you project. (well you don't have to do it as Enigma have some defaults but if you really care about nice typography, then you will do it).

### Enigma settings

Enigma settings can be changed via SASS variable `$enigma`. This variable must defined after you load Enigma files. Full Enigma settings are (displayed values are defaults):

```SCSS
$enigma: (
    'root': 16px,
    'base': 16px,
    'unit': 1rem,
    'alfa': 1.5,
    'beta': null,
    'start': -3,
    'stop': 5,
    'line-shift': -7px,
    'line-color': #15ADE6
);
```

__root__ - font size at `:root` element, value equals 1rem

__base__ - basic font size used for main body text. This size will have position 0 at modular scale.

__unit__ - unit to calculate all sizes in, currently only rem is supported and tested.

__alfa__ - primary scale to calculate all sizes from

__beta__ - (_optional_) secondary scale, if both alfa and beta are defined modular scale is created by merging these two. If only alfa is defined, modular scale is same as alfa.

__start__ - smalles index of scale - used to improve performance (sass doesn't have to calculate too many sizes). In most cases, this property doesn't have to be changed.

__stop__ - larges index of scale - used to improve performance (sass doesn't have to calculate too many sizes). In most cases, this property doesn't have to be changed.

__line-shift__ - align debug grid lines to be exactly below text, not in the middle. This is used for initial development, and exact value must be find out for each project. Each font have different height of characters, even for same font size.

__line-color__ - color of debug grid lines. Any valid CSS color should work.

### Mixin
_TODO_

### Functions
_TODO_

## To-Do:

- Test page - show of different enigma uses and settings
- Proper documentation.
- refactor project structure
- Support for responsive typography (CSS lock for fluid typography, different sizes for different screen sizes)
- Consider optional use of margin/padding for spacing
- custom scale (font-sizes) - need to re-think it.

## Knows bugs

- Chrome 52 - rem in font-size is calculated only to 6px as minimum - this cause wrong line-height issue, but since font-size of 6px and lower is not usable it shouldn't be a problem (can be always overwritten with real keayword).
- Due to rounding of relative units vertical rhytm can be slightly off after severat text element of different sizes.


