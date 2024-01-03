# River crossing problem (with generalizations)

River with island in middle of river

## Variant: Jealous husbands problem

**If island cannot be bypassed:**

Number of crossings required: $8n - 6$

| $n$ | # of crossings |
| ---: | ---: |
| 1 | 2 |
| 2 | 10 |
| 3 | 18 |
| 4 | 26 |
| 5 | 34 |
| ... | ... |

**Solution template:**

For $n = 1$:

| Step | Src | Mid | Dest |
| :---: | :---: | :---: | :---: |
| (start) | ⏏️<br/>🟥🔴 | | |
| 1 | | ⏏️<br/>🟥🔴 | |
| 2 | | | ⏏️<br/>🟥🔴 |
| (end) | | | **DONE** |

For $n = 2$:

| Step | Src | Mid | Dest |
| :---: | :---: | :---: | :---: |
| (start) | ⏏️<br/>🟥🔴<br/>🟦🔵 | | |
| 1 | 🟦🔵 | ⏏️<br/>🟥🔴 | |
| 2 | ⏏️<br/>🟥<br/>🟦🔵 | 🔴 | |
| 3 | 🔵 | ⏏️<br/>🟥🔴<br/>🟦 | |
| 4 | ⏏️<br/>🟦🔵 | 🟥🔴 | |
| 5 | | ⏏️<br/>🟥🔴<br/>🟦🔵 | |
| 6 | | 🟦🔵 | ⏏️<br/>🟥🔴 |
| 7 | | ⏏️<br/>🟥<br/>🟦🔵 | 🔴 |
| 8 | | 🔵 | ⏏️<br/>🟥🔴<br/>🟦 |
| 9 | | ⏏️<br/>🟦🔵 | 🟥🔴 |
| 10 | | | ⏏️<br/>🟥🔴<br/>🟦🔵 |
| (end) | | | **DONE** |

For $n = 3$:

| Step | Src | Mid | Dest |
| :---: | :---: | :---: | :---: |
| (start) | ⏏️<br/>🟥🔴<br/>🟨🟡<br/>🟦🔵 | | |
| 1 | 🟨🟡<br/>🟦🔵 | ⏏️<br/>🟥🔴 | |
| 2 | ⏏️<br/>🟥<br/>🟨🟡<br/>🟦🔵 | 🔴 | |
| 3 | 🟥<br/>🟨<br/>🟦 | ⏏️<br/>🔴<br/>🟡<br/>🔵 | |
| 4 | ⏏️<br/>🟥<br/>🟨<br/>🟦🔵 | 🔴<br/>🟡 | |
| 5 | 🟦🔵 | ⏏️<br/>🟥🔴<br/>🟨🟡 | |
| 6 | 🟦🔵 | 🟨🟡 | ⏏️<br/>🟥🔴 |
| 7 | 🟦🔵 | ⏏️<br/>🟥<br/>🟨🟡 | 🔴 |
| 8 | 🟦🔵 | 🟡 | ⏏️<br/>🟥🔴<br/>🟨 |
| 9 | 🟦🔵 | ⏏️<br/>🟨🟡 | 🟥🔴 |
| 10 | ⏏️<br/>🟨<br/>🟦🔵 | 🟡 | 🟥🔴 |
| 11 | 🔵 | ⏏️<br/>🟨🟡<br/>🟦 | 🟥🔴 |
| 12 | ⏏️<br/>🟦🔵 | 🟨🟡 | 🟥🔴 |
| 13 | | ⏏️<br/>🟨🟡<br/>🟦🔵 | 🟥🔴 |
| 14 | | 🟡<br/>🔵 | ⏏️<br/>🟥🔴<br/>🟨<br/>🟦 |
| 15 | | ⏏️<br/>🔴<br/>🟡<br/>🔵 | 🟥<br/>🟨<br/>🟦 |
| 16 | | 🔵 | ⏏️<br/>🟥🔴<br/>🟨🟡<br/>🟦 |
| 17 | | ⏏️<br/>🟦🔵 | 🟥🔴<br/>🟨🟡 |
| 18 | | | ⏏️<br/>🟥🔴<br/>🟨🟡<br/>🟦🔵 |
| (end) | | | **DONE** |

**Template for general solution:**

START: n couples on source bank, boat on source bank, middle island and destination bank empty.
STEP 1: Move couple #1 to middle island.

Couple #(k) on middle island, boat on middle island.
Move couple #(k + 1) from source bank to middle island.
If couple #(k + 1) is not last couple on source bank:

- Move boy #(k) to source bank.
- Move girls #(k + 1) and #(k + 2) to middle island.
- Move girl #(k + 2) to source bank.
- Move boys #(k) and #(k + 1) to middle island.

If couple #(k + 1) is last couple on source bank:

- Move boy #(k) to source bank.
- Move boys #(k) and #(k + 1) to middle island.
- Move boy #(k + 1) to source bank.
- Move couple #(k + 1) to middle island.

Couples #(k) and #(k + 1) on middle island, boat on middle island.
Move couple #(k) from middle island to destination bank.
If couple #(k) is first couple to destination bank:

- Move couple #(k) to destination bank.
- Move boy #(k) to middle island.
- Move boys #(k) and #(k + 1) to destination bank.
- Move boy #(k + 1) to middle island.

If couple #(k) is not first couple to destination bank:

- Move boys #(k) and #(k + 1) to destination bank.
- Move girl #(k - 1) to island.
- Move girls #(k) and #(k - 1) to destination bank.
- Move boy #(k + 1) to island.

Move last couple to destination island.
DONE.
