# Fionn Lex field guide

Read, write and shift the 44-glyph Cryptographic Alphabet. Every drawing below is generated from the rules, so the guide and the system cannot drift apart.

## Reading a glyph

1. Count the circles, 1 to 4. This is the only base 4 digit.
2. Count the structure added to the grid: lines first, then rays, then boundaries. That gives the iteration, 1 to 11.
3. Glyph number = 4 × (iteration − 1) + circles. Letters are 1 to 26 and digraphs are 27 to 44.
4. Optional dot layer: each dot, filled clockwise from the lower-left quadrant, adds 44.

The tell: two circles form an infinity running upper-left to lower-right. The lower-left to upper-right form is the other half of the four-circle glyph, and marks someone who has not learned the code.

## The 44 glyphs

Dots shown

Codes are keyboard labels, unique per iteration, not drawings. Digraphs are a proposed set of 8 vowel and 10 consonant pairs in alphabetical order.

## Encode and decode

Encode text Decode codes Shift [x] Use digraph glyphs

The shift moves each glyph around the ring of 44, so a shifted glyph is still a valid glyph. Digraphs are used greedily when the box is checked. Spaces are shown as gaps, and punctuation and numerals are not yet defined.

Working draft. Open design choices: the final digraph set, whether the shift ring is 44 or 220 once dots are included, and whether digraphs are mandatory or optional in plaintext.