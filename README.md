# Enigma

_Decypher web typography and vertical rhytm_

Enigma is small sass tool for better web typography. Its mixin and functions help you to ensure all text elements are in harmonious proportions, on same baseline and maintains consistent vertical rhythm.

Enigma is heavely inspired by [Modular Scale](http://www.modularscale.com/) from [Tim Brown](https://twitter.com/nicewebtype). If you want to know more about web typography you should definetely check some of his talks.

Enigma doesn't come with fonts or typography templates, for ready made solutions you may check other tools (like [Gutenberg](https://matejlatin.github.io/Gutenberg/)). In Enigma it is up to users to setup it according their needs as every page is different and it's typography should be treated as such. I build this tool for my need of easy and effective way how to use modular scales and different font-sizes with ease without all the difficult calculations for line height, font-size etc.

All this is handled by Enigma. All you have to do is to put in few basic numbers and enjoy the results - harmonious font sizes and harmonious vertycla rhytm.

## How to use it



### Mixin

### Functions



## To-Do:

- Test page - copy and tweak from Arbor
- Settings to work with different units.
- Proper documentation.
- Example page for the project.
- Support for responsive typography (CSS lock for fluid typography, different sizes for different screen sizes)
- Support for custom scale (list of font sizes without constant ration - mainly for use with enigmaLeading etc.)
- refactor project structure

## Knows bugs

- Chrome 52 - rem in font-size is calculated only to 6px as minimum - this cause wrong line-height issue, but since font-size of 6px and lower is not usable it shouldn't be a problem (can be always overwritten with real keayword).
- Due to rounding of relative units vertical rhytm can be slightly off after severat text element of different sizes.


