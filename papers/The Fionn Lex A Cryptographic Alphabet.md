# The Fionn Lex: A Cryptographic Alphabet

Nov 3, 2026 · @Mo

The Fionn Lex is a 44-glyph symbol cipher built on one idea: circles carry the digit, and everything else counts steps. This paper explains the design and its reasoning, teaches a reader to read and write it, and lists what is still open.

## Status of this draft

- **Settled:** the core structure (4 circle states × 11 iterations = 44 glyphs), the circle placements, the iteration ladder, the dot layer, the validity rules and the layering idea.
- **Proposed, awaiting your confirmation:** the 18 digraphs, the ray and boundary order, and the keyboard codes used in the examples.
- **Open:** the shift ring size (44 or 220), whether digraphs are mandatory, how word breaks, punctuation and numerals are written, and the three-letter forms.

## 1. Abstract

Most cipher alphabets are a list of arbitrary shapes. The Fionn Lex is a rule. Every glyph is a count of circles (1 to 4) set on a grid that has been divided a fixed number of times, so a reader who knows the rule can rebuild the whole alphabet from memory, and a reader who does not know it sees only dense, near-identical marks.

The base alphabet is the 26 letters of the English alphabet plus 18 digraphs, 44 glyphs in all. An optional dot layer extends it to 220. Layered with a Caesar shift, it produces text that is gibberish to anyone holding only half the key. The design is built for fiction and play: the novel series and the Captain Quill games, where a found key is the story.

## 2. Design principles

1. **One digit, many steps.** The circles are the only base 4 digit. Everything else (lines, rays, boundaries, dots) is iteration, a counter that advances when the circle digit rolls over.
2. **Growth in a fixed order.** Structure is added in one sequence only. A glyph shows how far along the sequence it is, never a free combination of marks.
3. **Detail has a cost.** Each division of the grid halves the space left for circles. The system divides first, then adds marks that divide nothing (section 4).
4. **Legibility is a gradient.** Small scale, heavy pen lines and look-alike glyphs are intentional. Larger drawings read clearly; smaller ones demand a zoom, like a pointillist painting. The deeper a user goes, the harder the reading.
5. **Discovery over secrecy.** The system is not meant to resist a determined analyst. Its strength is that it needs a key, and the key has to be known or found. That is a story, not a flaw.
6. **Strict but learnable.** The ruleset is rigid, but anyone who learns it, however they learn it, can use it. A rushed reader makes mistakes in a world that pushes speed; a careful one does not.

## 3. Anatomy of a glyph

The grid has four quadrants, numbered clockwise from the lower-left: **1** lower-left, **2** upper-left, **3** upper-right, **4** lower-right. The first glyph, A, is a single circle in quadrant 1.

| Circles | Quadrants filled | Keyboard code | Notes |
| --- | --- | --- | --- |
| 1 | 1 | `o` | A’s circle, lower-left |
| 2 | 2 and 4 | `8` | The infinity: zoomed in, the two circles touch |
| 3 | 1, 2 and 4 | `8o` | The infinity plus the single circle |
| 4 | 1, 2, 3 and 4 | `88` | Two infinities, the full grid |

**The orientation tell.** The canonical infinity runs from the upper-left to the lower-right. The lower-left to upper-right form is the other half of the four-circle glyph. A forger who builds the two-circle glyph by adding a circle to A has borrowed a piece of a different glyph, and the wrong-way infinity gives them away.

## 4. The aicmí: eleven iterations

The Irish word *aicme* (plural *aicmí*) means a family or class, and is the term used for the groups of letters in Ogham. Here an aicme is one iteration: four glyphs, one for each circle count, that share the same structure. There are eleven.

| Iteration | Step added | Smallest region | Prefix | Glyphs |
| --- | --- | --- | --- | --- |
| 1 | Bare grid | 1 | (none) | A B C D |
| 2 | Horizontal line | 1/2 | `-` | E F G H |
| 3 | Vertical line (cross) | 1/4 | `+` | I J K L |
| 4 | Ray 1, top-right | 1/8 | `/` | M N O P |
| 5 | Ray 2, bottom-right | 1/8 | `<` | Q R S T |
| 6 | Ray 3, bottom-left | 1/8 | `/<` | U V W X |
| 7 | Ray 4, top-left | 1/8 | `><` | Y Z ae au |
| 8 | Bottom boundary | 1/8 | `_` | ch ck ee ei |
| 9 | Left boundary | 1/8 | `[` | eu ie ng oe |
| 10 | Top boundary | 1/8 | `¬` | oo pf ph qu |
| 11 | Right boundary (box closed) | 1/8 | `]` | rh sh th wh |

A **line** crosses the whole grid. A **ray** is a half-line from the centre, as a radius is to a diameter. The ray order (clockwise from the top-right) and boundary order (bottom, left, top, right) are proposed. The prefixes are keyboard labels, unique per iteration, not drawings.

**Why the sequence stops where it does.** A full grid is 1. One line across leaves 1/2; two intersecting lines leave 1/4; a ray in a quarter leaves 1/8. Each division buys the same four glyphs but halves the space, so the cost grows geometrically while the return stays flat: a classic case of diminishing returns. The four rays stop the halving at 1/8. The four boundaries and the four dots divide nothing, so they add eight more iterations at no further cost in space. That is why they come last.

## 5. The alphabet

Glyphs 1 to 26 are the letters A to Z. Glyphs 27 to 44 are 18 digraphs, **8 vowel and 10 consonant**, in alphabetical order. Sorting them has a purpose: once the 27th glyph begins, a solver who has found the shift can check it against the sorted run, so the order is reliable (after the shift).

**Where the digraphs come from.** The pool is every two-letter compound found in Latin, English and German: 86 pairs across digraphs, doubled letters and pairs whose value is not simply letter plus letter. Eighteen were chosen, favouring pairs found in more than one language, with *ae* and *oe* for Latin.

- **Vowel (8, proposed):** ae, au, ee, ei, eu, ie, oe, oo
- **Consonant (10, proposed):** ch, ck, ng, pf, ph, qu, rh, sh, th, wh

The full glyph table is in Appendix A.

## 6. Extending the system

**The dot layer.** When the lines and rays are used up, the next iteration method is the interior dot. The order of iteration is line, ray, then dot.

- Dots fill the quadrants clockwise from quadrant 1: dot 1 in quadrant 1, dot 2 in quadrants 1 and 2, and so on up to four.
- Each dot adds **+44** to the glyph number.
- A dot is a structural mark like a line or ray, independent of the circles.

Glyph number = 44 × dots + 4 × (iteration − 1) + circles, giving 4 × 11 × 5 = **220 glyphs**. Dots are hardest to read where they meet the infinity join; this is intentional.

**The all-ray house variant.** Splitting every full line into two rays and every boundary into two half-sides gives 16 steps, 17 iterations and 68 glyphs (340 with dots). Splitting a line adds a step but not a division, so neighbouring iterations differ only by a half-stroke and misreading becomes likely. It is therefore a hard-mode house rule, not part of the base system, and a table using it must say so, because the same drawing reads differently under different keys.

The tiers used in play are **Simplex** (the 44 glyphs), **Complex** (the dot layer) and **Quantex** (an in-development layer of hidden language dots and outside text keys).

## 7. Validity and tells

Because structure is added in one fixed order, many drawings are simply invalid. These are built-in error checks:

- Only 11 of the 1,024 possible line sets are valid. A left boundary with no bottom boundary is invalid.
- A dot set is valid only if it fills quadrants 1 to n in order.
- An infinity drawn lower-left to upper-right is the wrong form for the two-circle glyph.

These checks help a careful reader and catch a careless forger. They also tell a solver that a key is wrong, because a wrong key often produces invalid glyphs.

## 8. Layering ciphers

A Caesar shift applied beneath the glyph layer makes glyph-only decoding produce believable gibberish: every shifted glyph is still a valid glyph, so nothing on the page says which layer failed. The shift moves each glyph around a ring of 44 (the ring size, 44 or 220 once dots are included, is open). With 220, a shift of 44 changes only the dot count.

An honest note on strength. A single shift has few possible values, so the Caesar layer is a layer of discovery, not a hard lock. The glyph layer alone is a substitution cipher, so a patient analyst with enough text could break it by frequency counts. The system’s real defences are the key that must be found, the ordered structure, and the scale at which it has to be read.

## 9. A guide to reading

To read one glyph:

1. Count the circles, 1 to 4. Check the infinity direction.
2. Count the structure added to the grid (lines, then rays, then boundaries) to find the iteration.
3. Glyph number = 4 × (iteration − 1) + circles. Numbers 1 to 26 are letters; 27 to 44 are digraphs.
4. Add 44 for each dot, if the dot layer is in use.

To read a message, find the glyph numbers, subtract the shift (wrapping around the ring) and look up each result. Worked example, shift 3, in keyboard codes:

`8 -88 8o <8 /8o -88` and `><8 <8 /<o /8o -8o`

The codes are glyph numbers 2, 8, 3, 18, 15, 8, then 26, 18, 21, 15, 7. Subtract 3 and wrap: 43 (th), 5 (E), 44 (wh), 15 (O), 12 (L), 5 (E), then 23 (W), 15 (O), 18 (R), 12 (L), 4 (D). The gap between the groups marks a word break. The message reads **the whole world**. Note that the first glyph, B, stands for *th*: shifting wraps the digraphs into the letter slots, which is why the digraphs belong inside the ring.

## 10. A guide to writing

1. Split the plaintext into letters and digraphs. The working convention is to use a digraph glyph whenever one exists (so *th* is one glyph, not T and H); whether this is mandatory is open.
2. Find each unit’s glyph number: A = 1 through Z = 26, then the digraphs in alphabetical order, 27 to 44.
3. Add the shift and wrap around the ring of 44. Add 44 per dot if needed.
4. For each number, set the circles (number − 1, modulo 4, plus 1) and the iteration (the number − 1, divided by 4, rounded down, plus 1), then draw the structure for that iteration.
5. Draw large if the message must be readable, small if it is meant to demand a zoom.

The companion field guide does steps 1 to 4 automatically and draws the result.

## 11. In the story and at the table

- **The premise.** The alphabet is only as secret as its key. A found key card, a taught rule or a half-remembered order is a plot object, not just a puzzle.
- **The forger.** Because an invalid glyph is a tell, an NPC forger can be exposed by a careful solver: a wrong-way infinity, an out-of-order line, a skipped dot.
- **Loot.** A cipher card can be handed over as a physical prop, drawn at a deliberately small or heavy scale.
- **A difficulty ladder for play (suggested).** Plain glyphs (Simplex); add a Caesar shift; add the dot layer (Complex); use the all-ray house variant as hard mode; the Quantex layer once it is defined.

## 12. Open questions

1. Confirm or change the 18 digraphs, and the ray and boundary order.
2. Shift ring: 44, or 220 with dots.
3. Are digraphs mandatory in plaintext? If optional, one message has several valid encodings.
4. How are word breaks, punctuation and numerals written?
5. The three-letter forms (sch, chs, tch, ght and others) are not yet defined.
6. The Quantex layer and the colour-blend key mechanic need a fresh pass against the settled structure.
7. Half-side split points and order for the all-ray variant.

## Appendix A. Glyph reference

Each cell shows the glyph and its keyboard code. Glyph number = 4 × (row − 1) + circles.

| Iteration | Prefix | 1 circle | 2 circles | 3 circles | 4 circles |
| --- | --- | --- | --- | --- | --- |
| 1 | (none) | A `o` | B `8` | C `8o` | D `88` |
| 2 | `-` | E `-o` | F `-8` | G `-8o` | H `-88` |
| 3 | `+` | I `+o` | J `+8` | K `+8o` | L `+88` |
| 4 | `/` | M `/o` | N `/8` | O `/8o` | P `/88` |
| 5 | `<` | Q `<o` | R `<8` | S `<8o` | T `<88` |
| 6 | `/<` | U `/<o` | V `/<8` | W `/<8o` | X `/<88` |
| 7 | `><` | Y `><o` | Z `><8` | ae `><8o` | au `><88` |
| 8 | `_` | ch `_o` | ck `_8` | ee `_8o` | ei `_88` |
| 9 | `[` | eu `[o` | ie `[8` | ng `[8o` | oe `[88` |
| 10 | `¬` | oo `¬o` | pf `¬8` | ph `¬8o` | qu `¬88` |
| 11 | `]` | rh `]o` | sh `]8` | th `]8o` | wh `]88` |

## Appendix B. Terms

- **Aicme (plural aicmí):** one iteration; four glyphs sharing one structure.
- **Iteration:** a step in the fixed sequence of structure: lines, rays, boundaries, then dots.
- **Digraph:** a two-letter unit treated as one glyph.
- **Ray:** a half-line from the centre of the grid.
- **Ring:** the cycle of glyph numbers around which a shift wraps.
- **Seam:** the point (glyph 27) where the sorted digraphs begin after the letters.
- **Simplex, Complex, Quantex:** the base 44 glyphs, the dot layer, and the in-development layer of hidden language dots and outside text keys.
