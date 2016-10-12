# Enigma

_Decypher web typography and vertical rhytm_

Enigma is small sass tool for better web typography. Its mixin and functions help you to ensure all text elements are in harmonious proportions, on same baseline and maintains consistent vertical rhythm.

Enigma is heavely inspired by [Modular Scale](http://www.modularscale.com/) from [Tim Brown](https://twitter.com/nicewebtype). If you want to know what Modular Scale is or need more information about web typography you should definetely check some of his talks.

Enigma doesn't come with fonts or typography templates, for ready made solutions you may check other tools (like [Gutenberg](https://matejlatin.github.io/Gutenberg/)). In Enigma it is up to you to setup it according your needs as every project is unique and it's typography should be treated as such. I build this tool for my need of easy and effective way how to use modular scales and different font-sizes with ease without all the difficult calculations for line height, font-size etc. It is perfect tool for keeping your vertical rhythm consistent and prepare good looking typography with very little effort.

All math is handled by Enigma. All you have to do is to put in few basic numbers and enjoy the results - harmonious font sizes and harmonious vertycla rhythm.

## How to use it

- include sass
- setup (setting desc)
- what to use (mixin and functions)

### Mixin
description

### Functions
description

## To-Do:

- Test page - only typography cleanup is remaining (dashes quotes etc.), udělat JS zobrazování stylů( aby hned viděli, jak je to nastavené, vysvětlení)
- Proper documentation.
- Support for responsive typography (CSS lock for fluid typography, different sizes for different screen sizes)
- Consider optional use of margin/padding for spacing

## Knows bugs

- Chrome 52 - rem in font-size is calculated only to 6px as minimum - this cause wrong line-height issue, but since font-size of 6px and lower is not usable it shouldn't be a problem (can be always overwritten with real keayword).
- Due to rounding of relative units vertical rhytm can be slightly off after severat text element of different sizes.


