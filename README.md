# The Sudoku Lie Detector

A board with lies planted in it. Find them.

A solved sudoku gets sabotaged before you see it: digits changed or cells
swapped so rows, columns, or boxes break. Flag the cells you think are lying,
hit Expose, and the verdict tells you what you caught, what you missed, and
what you falsely accused.

## Play

Open `index.html` in a browser. Zero dependencies, no build step.

- Click a cell to flag it as a lie. Click again to unflag.
- **Expose** — reveal the lies and get the verdict.
- **Hint** — flags one uncaught lie for you.
- **Clear** — remove all flags.
- **New** — fresh board.

## Difficulty

| Level | Board | Lies |
|---|---|---|
| Warm-up | 4x4 | 1 single |
| Classic | 6x6 | 2 singles |
| Hard | 9x9 | 3 singles, spread so no two share a row, column, or box |
| Ruthless | 9x9 | 2 swaps (4 cells; rows and boxes stay valid, only columns break) |

## Scoring

+100 per lie caught. False accusations cost 25 each, capped at -50 per board.
Escaped lies just hurt your pride.

## How it works

- `genSolved` — backtracking solver generates a valid board at 4x4, 6x6, or 9x9.
- `plantLies` — two lie types. Singles: replace one cell's digit, which
  duplicates the new digit across its row, column, and box (three tells).
  Swaps: exchange two cells inside one box mini-row, so rows and boxes stay
  valid and only columns break. Up to 80 placement attempts per board.
- `expose` — compares flags against planted lies, scores, renders the verdict.

Single self-contained file by design: open and play.

*Built for the [SUNY New Paltz Math Club](https://new-paltz-math-club-website-43509a.gitlab.io/index.html).*
