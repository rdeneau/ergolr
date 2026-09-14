# ErgolR

A French-first ergonomic keyboard layout for a 4×6 split column-staggered board, currently a **Keebart Sofle Choc Pro**.

ErgolR is a personal fork of [Ergo-L](https://ergol.org/): same core idea — an optimised letter arrangement plus a one-shot dead key (1dk) for everything accented or typographic — reshaped for a 40-ish % split keyboard, and for the habits of an AZERTY touch typist who writes code all day.

![Base, NavNum, Symbol and 1dk layers](ergolr-layers.svg)

![Emoji layer](ergolr-emoji.svg)

## Inspirations

- [Ergo-L](https://ergol.org/) letter arrangement and its 1dk one-shot dead key that carries the accents.
- [Glove80 / MoErgo](https://docs.moergo.com/glove80-user-guide/) Keypad/Lower layer, its hold tap principle to access layers - see the ErgoLR [layout](https://my.moergo.com/glove80/#/search?tags=ergo-lr)
- [TailorKey](https://sites.google.com/view/tailorkey/moergo/go60) AutoShift, its Symbol layer, its F-Key combos

## Where the code lives

This repository holds the design material. The firmware is a QMK keymap in a [Vial-QMK fork](https://github.com/rdeneau/vial-qmk-keebart/keyboards/keebart/sofle_choc_pro/keymaps/vial_rde/).

## Deviations from Ergo-L, and why

The letter core is Ergo-L. Everything below is a deliberate departure.

### Muscle memory from AZERTY wins

Twenty years of AZERTY is not worth re-learning away when the gain is marginal.

- **<kbd>x</kbd> <kbd>c</kbd> <kbd>v</kbd> stay side by side on the bottom row**, in that order, exactly where AZERTY puts them. Cut, copy and paste are chorded hundreds of times a day; moving them costs more than any letter-frequency gain returns.
- **<kbd>c</kbd> displaces <kbd>b</kbd>**, which moves up between <kbd>q</kbd> and <kbd>o</kbd>.
- **<kbd>= / +</kbd> sits at the end of the digit row**, where AZERTY has it.
- **<kbd>"</kbd> on <kbd>3</kbd> and <kbd>'</kbd> on <kbd>4</kbd>** follow the AZERTY digit row instead of Ergo-L's `«` and `»`, which move down to the 1dk layer of that same row.

### A digit row rebuilt around what I actually type

- `$` on <kbd>1</kbd> rather than <kbd>4</kbd>.
- `€` on <kbd>2</kbd> rather than <kbd>1</kbd>.
- `(` and `)` on <kbd>6</kbd> and <kbd>7</kbd>, as a pair, rather than scattered; `&` and `^` are left to the Symbol layer.
- `@` on <kbd>8</kbd> rather than <kbd>9</kbd>.
- `#` on <kbd>9</kbd> — a character I type constantly, naming C# and F#. Its 1dk gives `♯`, the music sharp sign those two names are actually pronounced with.
- `°` on <kbd>0</kbd>, taking the slot `/` used to hold: the slash is easier to reach on the Symbol layer, with `\` right underneath it.

### Three new key pairs

- <kbd>, / ;</kbd> replaces <kbd>b</kbd> on the bottom row, mirroring <kbd>. / :</kbd> on the other half.
- <kbd>- / _</kbd> takes the slot <kbd>, / ;</kbd> left free, between <kbd>g</kbd> and <kbd>k</kbd>.
- <kbd>? / !</kbd> ends the right outer column, under <kbd>* / µ</kbd>, where a second <kbd>Backspace</kbd> would only have duplicated the thumb.

### A 1dk layer that keeps room for symbols

It carries fewer accented characters than a full French set, which frees space for typography and box-drawing characters.
The common ones sit on their own vowel: `é` on <kbd>e</kbd>, `î` on <kbd>i</kbd>, `û` on <kbd>u</kbd>, `à` on <kbd>a</kbd>.
<kbd>a</kbd> is the exception twice over. `â` cannot take the key above it — that one has to stay <kbd>Shift</kbd> — so it moves one row further up, onto <kbd>q</kbd>; and `æ`, evicted from that slot, lands on <kbd>f</kbd>, right after the run of e-s.
Special characters follow the same likeness rule: the quotes on the quote keys, `’` on the apostrophe, `‰` next to `%`, `§` on <kbd>p</kbd> (as in *paragraph*) with `¶` next to it on <kbd>w</kbd>, `♯` on <kbd>#</kbd>, `÷` on <kbd>d</kbd> (as in *divide*), and a literal Tab character on the <kbd>Tab</kbd> key.

## Layers

| #   | Name       | Reached by    | Holds                                                                        |
| --- | ---------- | ------------- | ---------------------------------------------------------------------------- |
| 0   | **Base**   | <kbd>Esc</kbd>           | The ErgolR letters, the digit row, the editing thumbs.                       |
| 1   | **NavNum** | <kbd>PrtScr</kbd>        | F1–F12, navigation, Undo/Cut/Copy/Paste, a numeric keypad on the right half. |
| 2   | **Symbol** | <kbd>Space</kbd>         | Brackets, operators, punctuation.                                            |
| 3   | **1dk**    | the <kbd>★</kbd> key     | Accents and typography; Shift reaches the second glyph of each pair.         |
| 4   | **Emoji**  | tap <kbd>★</kbd> twice   | Emoji, as the Glove80's third dead key; the digit row holds the keycaps.     |

### Hold, double tap, and the way out

The two thumb-reachable layers behave the same way:

| Action on <kbd>PrtScr</kbd> / <kbd>Space</kbd> | Result                                                 |
| ---------------------------------------------- | ------------------------------------------------------ |
| tap                                            | <kbd>PrtScr</kbd> / a space                            |
| hold                                           | NavNum / Symbol, for as long as the key is held (`MO`) |
| double tap                                     | NavNum / Symbol locked (`TG`)                          |

<kbd>Esc</kbd> leaves a locked layer and returns to Base.
That is also what the RGB tells you: every layer lights the same static map, and **the <kbd>Esc</kbd> key alone says which layer is active** — white on Base, orange on NavNum, blue on Symbol, red on 1dk, violet on Emoji.
The <kbd>PrtScr</kbd> key stays orange and the right-thumb <kbd>Space</kbd> stays blue on every layer, as a reminder of which key reaches which.

### The backtick

On the Symbol layer the backtick is the plain AZERTY <kbd>AltGr</kbd>+<kbd>7</kbd>, which is a **dead** grave accent, and it behaves exactly as it does on a standard AZERTY ISO keyboard.

- <kbd>\`</kbd>+<kbd>Space</kbd> → backtick literal
- <kbd>\`</kbd>+<kbd>\`</kbd> → double-backtick

Nothing in the firmware pre-composes those sequences: the dead key is the intended behaviour, not a limitation to work around.

`^` and `~` are the opposite call.
They are dead keys on AZERTY too — <kbd>AltGr</kbd>+<kbd>9</kbd> and <kbd>AltGr</kbd>+<kbd>2</kbd> — but nothing on this layout needs `ê` or `ñ` from them, the 1dk layer already owns the accented letters.
So the firmware taps the space itself and one tap types one character.

### Parallels between the layers

Several keys mean the same thing on every layer they appear on, which is most of what makes the layout memorable.

| Key                                      | 1dk                             |
| ---------------------------------------- | ------------------------------- |
| **Arrows**                               |                                 |
| <kbd>Alt</kbd> <kbd>←</kbd> <kbd>→</kbd> | `↔` / `⟺`, `←` / `⇐`, `→` / `⇒` |
| <kbd>↑</kbd> <kbd>↓</kbd>                | `↑` / `⇑` • `↓` / `⇓`           |
| **Typo**                                 |                                 |
| <kbd>Enter</kbd>                         | `↩`                             |
| <kbd>Space</kbd>                         | `NBSP` non-breaking space       |
| <kbd>. / :</kbd>                         | `·` (middle-dot) / `•` (bullet) |
| <kbd>- / _</kbd>                         | `–` (EN dash) / `—` (EM dash)   |

The arrow keys give arrow characters, Enter gives the return arrow, Space gives the unbreakable space.
Nothing to memorise beyond "the 1dk layer says the same thing in Unicode".

## Shift, Caps Lock and Auto Shift

Every key carrying two glyphs picks the second one under **<kbd>Shift</kbd> or <kbd>Caps Lock</kbd>** — the digit row, <kbd>, / ;</kbd>, <kbd>. / :</kbd>, <kbd>- / _</kbd>, <kbd>? / !</kbd>, and the whole 1dk layer, where Shift turns `à` into `À` and `«` into `❝`.

**Auto Shift** is on, so *holding* a key is a third way to reach that second glyph — no Shift needed.
It covers the letters (accented ones included, through the 1dk layer) and the dual-glyph keys of the digit row.
It stays on under the other modifiers, which is what makes <kbd>Ctrl</kbd>+hold <kbd>p</kbd> reach <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, and <kbd>Win</kbd>+hold <kbd>,</kbd> open the Windows emoji picker.

**Double tap <kbd>Shift</kbd>** switches <kbd>Caps Lock</kbd> on; once it is on, a single tap switches it back off.
A tap here means a press and release with no other key in between, so a <kbd>Shift</kbd> used as a modifier never triggers it.

Caps Lock is handled explicitly rather than left to the host: the French Windows layout inverts the digit row under Caps Lock, and that inversion is undone so the pairs stay literal.

## The three lives of ErgolR

| #   | Board           | What the host needed                                                                                                                                                                                                                            |
| --- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Sofle           | A Windows keyboard US driver, generated with [Kalamine](https://github.com/OneDeadKey/kalamine) and installed on the machine. The layout lived in the OS. Connect to a remote machine (e.g., with RDP) and you end up with a QWERTY keyboard 🫤. |
| 2   | Glove80         | No driver, but an [AutoHotkey (AHK) v2](https://www.autohotkey.com/v2/) script for the special characters and the emoji.                                                                                                                        |
| 3   | Sofle (current) | Only [WinCompose](https://github.com/samhocevar/wincompose). Everything else lives in the firmware.                                                                                                                                             |

The direction is the same each time: push the layout further down, from the OS into the keyboard, so that plugging the board into any machine is enough.

The current firmware still needs WinCompose installed, with its compose key on <kbd>Scroll Lock</kbd> — not <kbd>Alt Gr</kbd> (a.k.a. "Right Alt"), although ErgolR does not need to expose this key.
The host OS layout stays **French AZERTY**: the keyboard only ever sends raw scancodes, and the host turns them into the glyphs above.

## The two sheets

- `ergolr-layers.svg` — Base, NavNum, Symbol and 1dk on one picture, plus the two rotary encoders in the middle.
  Blue marks the key that holds Symbol, orange the key that holds NavNum, matching the RGB under the keys.
  Letter keys show the uppercase letter and the lowercase accented one: the two glyphs the other levels do not repeat.
- `ergolr-emoji.svg` — the Emoji layer, reached by tapping the red <kbd>★</kbd> key twice.
  Each emoji carries the name it has in the original MoErgo layout, and the corner of every key repeats the Base glyph it sits on.
