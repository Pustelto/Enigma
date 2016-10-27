# Enigma

_Decypher web typography and vertical rhytm_

Enigma is small sass tool for better web typography. Its mixin and functions help you to ensure all text elements are in harmonious proportions, on same baseline and maintains consistent vertical rhythm.

Enigma is heavely inspired by [Modular Scale](http://www.modularscale.com/) from [Tim Brown](https://twitter.com/nicewebtype). If you want to know what Modular Scale is or need more information about web typography you should definetely check some of his talks.

Enigma doesn't come with fonts or typography templates, for ready made solutions you may check other tools (like [Gutenberg](https://matejlatin.github.io/Gutenberg/)). In Enigma it is up to you to setup it according your needs as every project is unique and it's typography should be treated as such. I build this tool for my need of easy and effective way how to use modular scales and different font-sizes with ease without all the difficult calculations for line height, font-size etc. It is perfect tool for keeping your vertical rhythm consistent and prepare good looking typography with very little effort.

All math is handled by Enigma. All you have to do is to put in few basic numbers and enjoy the results - harmonious font sizes and vertycal rhythm.

See [demo page](https://pustelto.github.io/Enigma/) and source files (`index.html` and `_base.scss`) to see how ease can you craft good typography.

## How to use it

Include the sass files from `dist/` folder into your project, add `_enigma.scss` to your main sass file and you are ready to go.

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

Enigma provide `enigma` mixin, which can be used to set most of your typography. It has several parameters and all of them are optional. So the easest use of the mixin would be `@include enigma();`. This would set your font size to the value of `base` settings. Mixin also sets coressponding line height.

`enigma` mixin has following syntax:

```scss
/* General syntax */
@include enigma([scale] [on (line-height | lh-scale at lh-ratio)] [with margin-top [margin-bottom] ] );

/* and real life example - side note from test page*/
@include enigma(-1 on -1 at 4/5 with 0 0);
```

#### Mixin parameters:

__scale__ - Integer, _Default: 0_

Represent position on the modular scale. This parametr is used to set `font-size` property and is mandatory only if other parameters are used as well. Default value is used if omitted. Default value is 0 (`base` size from settings).

__line-height__ - Number, _Default: no default value, parameter is left empty_

Real number which will be used as a value for `line-height` property. Must be preceded by `on` keyword. If not line-height parameter was specified (together with keyword `on`) then value of line-height is calculated automaticaly based on scale. This automatic calculation is what you usually want, so unless you need some specific line height you shouldn't be using this very often.

__lh-scale__ - Integer, _Default: no default, parameter must be always specified if used_

Must be used together with `lh-ration` otherwise expect buggy behavior or errors during compilation. Must be preceded by `on` keyword and followed by `at` keyword. This value represent fon-size (from modular scale) for which line height should be calculated. Usualy will be same as `scale` value.

__lh-ratio__ - Number, _Default: no default, parameter must be always specified if used_

Must be used together with `lh-scale` otherwise expect buggy behavior or errors during compilation. Must be preceded by `at` keyword. This value represent ration between default line-height (for body text) and line-height calculated by mixin. Eg. value `4/5` in real life example above means that 5 lines set by mixin will have height of 4 base lines. See side note in [demo page](https://pustelto.github.io/Enigma/) for visuall example.

__margin-top__ - Number | 'base', _Default: size of line-height unless specified otherwise_

Top margin of the element. Number is ration of base line. Eg. 1 equals to 1 base line, 0 set margin to 0. If not specified by `with` keyword top margin of 1 will be added automaticaly. So in order to have 0 margins you must wrote `@include enigma(1 with 0 0);`. Special value `base` will leave top margin unchanged (it won't reset the top margin if specifed at different place in CSS).

__margin-bottom__ - Number, _Default: size of line-height unless specified otherwise_

Bottom margin of the element. Number is ration of base line. Eg. 1 equals to 1 base line, 0 set margin to 0. If not specified by `with` keyword top margin of 1 will be added automaticaly. So in order to have 0 margins you must wrote `@include enigma(1 with 0 0);`. Bottom margin won't accept value `base`. If you don't want to override bottom margin, simply don't define it (eg. `@include enigma(1 with 1)`). However you have to define top margin, otherwise default margin will be set.

### Functions

Enigma functions are useful if you need setup some value directly (like margins for consistent vertical rhythm). On low level `enigma` mixin only parses parameters and call functions below with those parsed parameters.

#### enigmaLeading( $lvl )

This function returns multiple of base line height. `$lvl` parameter is number by which the base line height is multiplied.

Defaults: `$lvl`: 1 (one base line height)

#### enigmaSize( $lvl, $scale)

This function returns size based on value of scale. This function is most usefull for setting up font size, but it can be used elsewhere as well. `$lvl` parameter is level from modular scale and must be integer. `$scale` parameter is string with the name of scale which should be used for calculation ('alfa' or 'beta'). If the `$scale` is null then merged scale from alfa and beta will be used.

Defaults: `$lvl`: 0, `$scale`: null

#### enigmaLine( $lh-args, $scale)

Funtion return correct line-height (unitless number) for specified parameters. It won't be very probably useful outside of line-height calculations but feel free to use it in different scenarios as well. `$lh-args` is map of parameters to calculate proper line-height, see line height parameters at `enigma` mixin documentation.

Aside from `enigma` mixin there are these modifications: If you enter only integer number, line-height will be calculated as if this number is font size from scale. If you add keyword `real` after the number (can be with decimal point) that number will be used as is for `line-height` property.

`$scale` parameter is string with the name of scale which should be used for calculation ('alfa' or 'beta'). If the `$scale` is null then merged scale from alfa and beta will be used.

Defaults: `$lvl`: 0, `$scale`: null

## Things which may be added in the future:

- refactor project structure
- create proper project page
- Support for responsive typography (CSS lock for fluid typography, different sizes for different screen sizes)
- Consider optional use of margin/padding for spacing
- custom scale (font-sizes) - need to re-think it.

## Knows bugs

- Chrome 52 - rem in font-size is calculated only to 6px as minimum - this cause wrong line-height issue, but since font-size of 6px and lower is not usable it shouldn't be a problem (can be always overwritten with real keayword).
- Due to rounding of relative units vertical rhytm can be slightly off after severat text element of different sizes.


