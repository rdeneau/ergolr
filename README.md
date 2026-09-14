# ErgolR

A French-first ergonomic keyboard layout for a 4×6 split column-staggered board, currently a **Keebart Sofle Choc Pro**.

ErgolR is a personal fork of [Ergo-L](https://ergol.org/): same core idea — an optimised letter arrangement plus a one-shot dead key for everything accented or typographic — reshaped for a 40-ish % split keyboard, and for the habits of an AZERTY touch typist who writes code all day.

![Base, NavNum, Symbol and 1dk layers](ergolr-layers.svg)

![Emoji layer](ergolr-emoji.svg)

## Inspirations

| Source | What it gave |
| --- | --- |
| [Ergo-L](https://ergol.org/) | The letter arrangement and the 1dk one-shot dead key that carries the accents. |
| [TailorKey](https://sites.google.com/view/tailorkey/moergo/go60) | The thumb clusters: editing keys on the left thumb, Space/Enter and the layer holds on the right. |
| [Glove80 / MoErgo](https://www.moergo.com/) | The previous incarnation of this layout, from which the 1dk, 2dk, Symbol and emoji layers were transcribed. |

## Where the code lives

The firmware is a QMK keymap in a Vial-QMK fork:

```
https://github.com/rdeneau/vial-qmk-keebart
  keyboards/keebart/sofle_choc_pro/keymaps/vial_rde/
```

This repository holds the design material: the Vial exports (`ergolrl-v*.vil`), the Glove80 source layout (`ergol-r_moergo.json`), the two SVG sheets above, and `TODO.md`, the running design log.

## Deviations from Ergo-L, and why

The letter core is Ergo-L. Everything below is a deliberate departure.

### Muscle memory from AZERTY wins

Twenty years of AZERTY is not worth re-learning away when the gain is marginal.

- **`x c v` stay side by side on the bottom row**, in that order, exactly where AZERTY puts them. Cut, copy and paste are chorded hundreds of times a day; moving them costs more than any letter-frequency gain returns.
- **`c` displaces `b`**, which moves up between `q` and `o`.
- **`= / +` sits at the end of the digit row**, where AZERTY has it.
- **`"` on 3 and `'` on 4** follow the AZERTY digit row instead of Ergo-L's `«` and `»`, which move down to the 1dk layer of that same row.

### A digit row rebuilt around what I actually type

- `$` on **1** rather than 4.
- `€` on **2** rather than 1.
- `(` and `)` on **6** and **7**, as a pair, rather than scattered; `&` and `^` are left to the Symbol layer.
- `@` on **8** rather than 9.
- `#` on **9** — a character I type constantly, naming C# and F#.
- `/` on **0**, though it is easier to reach in the Symbol layer, with `\` right underneath it.

### Two new key pairs

- `, ;` replaces `b` on the bottom row, mirroring `. :` on the other half.
- `- _` takes the slot `, ;` left free, between `g` and `k`.

### A 1dk layer that keeps room for symbols

It carries fewer accented characters than a full French set, which frees space for typography and box-drawing characters.
The common ones sit directly on their vowel (`à é î û`); the rest go left or right of it, wherever there is room — `æ` above `à` being the exception.
Special characters follow the same likeness rule: the quotes on the quote keys, `’` on the apostrophe, `°` next to `%`, `§` on `p` (as in *paragraph*), and a literal Tab character on the Tab key.

## Layers

| # | Name | Reached by | Holds |
| --- | --- | --- | --- |
| 0 | **Base** | — | The ErgolR letters, the digit row, the editing thumbs. |
| 1 | **NavNum** | `PrtScr` | F1–F12, navigation, Undo/Cut/Copy/Paste, a numeric keypad on the right half. |
| 2 | **Symbol** | `Space` | Brackets, operators, punctuation. |
| 3 | **1dk** | the `★` key | Accents and typography; Shift reaches the second glyph of each pair. |
| 4 | **Emoji** | tap `★` twice | Emoji, as the Glove80's third dead key. |

### Hold, double tap, and the way out

The two thumb-reachable layers behave the same way:

| Action on `PrtScr` / `Space` | Result |
| --- | --- |
| tap | `PrtScr` / a space |
| hold | NavNum / Symbol, for as long as the key is held (`MO`) |
| double tap | NavNum / Symbol locked (`TG`) |

`Esc` leaves a locked layer and returns to Base.
That is also what the RGB tells you: every layer lights the same static map, and **the `Esc` key alone says which layer is active** — white on Base, orange on NavNum, blue on Symbol, red on 1dk, violet on Emoji.
The `PrtScr` key stays orange and the right-thumb `Space` stays blue on every layer, as a reminder of which key reaches which.

### The backtick

On the Symbol layer the backtick is the plain AZERTY `AltGr+7`, which is a **dead** grave accent, and it behaves exactly as it does on a standard AZERTY ISO keyboard.

- Backtick then `Space` types one literal backtick.
- Backtick twice types a pair of them.

Nothing in the firmware pre-composes those sequences: the dead key is the intended behaviour, not a limitation to work around.

### Parallels between the layers

Several keys mean the same thing on every layer they appear on, which is most of what makes the layout memorable.

| Key | Base | 1dk | Symbol | NavNum |
| --- | --- | --- | --- | --- |
| left thumb `Alt` | `Alt` | `↔` / `⟺` |  — | — |
| left thumb ← | `Left` | `←` / `⇐` | — | — |
| left thumb → | `Right` | `→` / `⇒` | `_` | — |
| left thumb `Enter` | `Enter` | `↩` | — | — |
| inner `Enter` (right) | `Enter` | `↩` | — | — |
| right thumb `Space` | space | non-breaking space | *holds Symbol* | — |
| right thumb `↑` `↓` | `Up` `Down` | `↑` / `⇑`, `↓` / `⇓` | — | — |
| `.` `:` key | `.` `:` | `·` / `•` | `:` | numpad `.` |
| `- _` key | `-` `_` | `–` / `—` | — | numpad `3` |

The arrow keys give arrow characters, Enter gives the return arrow, Space gives the unbreakable space.
Nothing to memorise beyond "the 1dk layer says the same thing in Unicode".

## Shift, Caps Lock and Auto Shift

Every key carrying two glyphs picks the second one under **Shift or Caps Lock** — the digit row, `, ;`, `. :`, `- _`, and the whole 1dk layer, where Shift turns `à` into `À` and `«` into `❝`.

**Auto Shift** is on, so *holding* a key is a third way to reach that second glyph — no Shift needed.
It covers the letters (accented ones included, through the 1dk layer) and the dual-glyph keys of the digit row.

Caps Lock is handled explicitly rather than left to the host: the French Windows layout inverts the digit row under Caps Lock, and that inversion is undone so the pairs stay literal.

## The three lives of ErgolR

| # | Board | What the host needed |
| --- | --- | --- |
| 1 | Sofle | A Windows keyboard driver, generated with [Kalamine](https://github.com/OneDeadKey/kalamine) and installed on the machine. The layout lived in the OS. |
| 2 | Glove80 | No driver, but an AutoHotkey script for the special characters and the emoji. |
| 3 | Sofle (current) | Only [WinCompose](https://github.com/samhocevar/wincompose). Everything else lives in the firmware. |

The direction is the same each time: push the layout further down, from the OS into the keyboard, so that plugging the board into any machine is enough.

The current firmware still needs WinCompose installed, with its compose key on **Scroll Lock** — not Right Alt, which would swallow AltGr.
The host OS layout stays **French AZERTY**: the keyboard only ever sends raw scancodes, and the host turns them into the glyphs above.

## The two sheets

- `ergolr-layers.svg` — Base, NavNum, Symbol and 1dk on one picture, plus the two rotary encoders in the middle.
  Blue marks the key that holds Symbol, orange the key that holds NavNum, matching the RGB under the keys.
  Letter keys show the uppercase letter and the lowercase accented one: the two glyphs the other levels do not repeat.
- `ergolr-emoji.svg` — the Emoji layer, reached by tapping the red `★` key twice.
  Each emoji carries the name it has in `ergol-r_moergo.json`, and the corner of every key repeats the Base glyph it sits on.
