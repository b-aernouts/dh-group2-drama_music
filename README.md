# Drama and Music dataset cleaning
> (Introduction to Digital Humanities, KU Leuven 2026–2027)
> Based on dh-group2-prose/README by omaralbatran

This repository holds the cleaning of the **Music** and **Drama** part of the British Library "Microsoft Books"
metadata dataset, done in OpenRefine. It is part of the Group 2 project (Omar & Bert).

- **Source:** British Library, *Microsoft Books* digitised books metadata - https://doi.org/10.23636/1140
- **Input:** 1) `data/raw/MicrosoftBooks-Drama.xlsx`. It has x sheets, but only the main `Drama` sheet
  (x records) will be used: the subgenre sheets are subsets of it. 2) `data/raw/MicrosoftBooks-Music.xlsx`. It has x sheets, but only the main `Drama` sheet
  (x records) will be used: the subgenre sheets are subsets of it.

## Structure
| Path | Contents |
|---|---|
| `data/raw/` | Original file as downloaded. **Never modified.** |
| `data/interim/` | Versions exported from OpenRefine at each cleaning stage |
| `data/clean/` | Final cleaned Prose dataset, ready to merge |
| `openrefine/` | Exported OpenRefine operation histories (Undo/Redo → Extract → JSON) |

## Reproducing
1. Create an OpenRefine project from `data/raw/MicrosoftBooks-Drama.xlsx` or `data/raw/MicrosoftBooks-Music.xlsx`
2. Undo/Redo → Apply → paste the JSON files from `openrefine/` in order.
