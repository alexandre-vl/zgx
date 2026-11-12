---
section: performance
---
- **A long list scrolled under a resting pointer hit-tests in time that doesn't grow with its rows** (zgx): each hit test searched a long column's rows but first checked, row by row, that their boxes ran down in order and that none outside the search reached past its neighbours, every time: 34 instructions a row, so a scroll view of 7,000 rows paid 0.2M instructions for each hover test as it scrolled. A container now remembers that its rows passed (`ROWS_VERIFIED`) until one of them or its children change, which the existing invalidation walk clears; a translation of the container itself keeps it. A wheel-scrolled frame of 7,000 keyed rows costs 0.011M instructions in zgx's core rather than 0.185M (1,000 rows: 0.036M), the same as at 1,000.
