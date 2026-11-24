# One-week learning pilot

**Outcome** — Given a two-column spreadsheet, write a one-condition sum, explain which cells it tests and adds, and verify the result by hand.

**Time** — Allow about 15–25 minutes per day. Use any spreadsheet that supports `SUMIF`, or write the formulas on paper and check the totals by hand. Keep your scores and study notes in your own storage.

## Schedule

| Day | Activity | Finish with |
| --- | --- | --- |
| 1 | Take the baseline check below before using the reference, notes, or AI. | A baseline answer sheet and score. |
| 2 | Read the reference and create a note using the [study-note template](../templates/study-note.md). Check the Books total by hand. | One reviewed note linked to its source. |
| 3 | Use the [AI tutor prompt](../prompts/ai-tutor.md) to practice with the reference table. Try each question before requesting a hint. | One correction written in your own words. |
| 4 | Work out the total for Tools. Add a Tools row worth 4 and update the formula to include it. | A formula that returns 29 after the new row is included. |
| 5 | Close the notes. Recall the three arguments, the result for a missing category, and how you would check a total. Reopen your note and correct any gaps. | Three recall answers and one note update. |
| 6 | Use AI to draft three recall questions from one reviewed note. Check each question against the source before saving it. | Three verified questions and a note on what needed editing. |
| 7 | Take the final check without AI or notes, then score it. Compare with Day 1 and pick one thing to practice next. | A final score, one gap, and a next review date. |

## Baseline and final checks

For each check, write your answers before opening the answer key or running a formula in the spreadsheet. Use the displayed row numbers. Use commas or the argument separator required by your spreadsheet.

| Row | Baseline A | Baseline B | Final A | Final B |
| --- | --- | ---: | --- | ---: |
| 1 | Category | Amount | Category | Amount |
| 2 | Pens | 4 | Paper | 9 |
| 3 | Clips | 7 | Tape | 6 |
| 4 | Pens | 9 | Tape | 8 |
| 5 | Tape | 6 | Paper | 3 |

1. Write a formula to total **Pens** on Day 1 or **Tape** on Day 7.
2. Give the expected total and show the matching amounts.
3. Identify the range the condition tests and the range it sums.

Award one point per answer. Give the formula point for a valid `SUMIF` with the correct ranges and condition, the total point for the correct amounts and result, and the explanation point for correctly identifying both range roles. Record **baseline __/3**, **final __/3**, and **next practice __**.

<details>
<summary>Answer key — open after the check</summary>

- **Baseline:** `=SUMIF(A2:A5,"Pens",B2:B5)`. The total is 13 (4 + 9).
- **Final:** `=SUMIF(A2:A5,"Tape",B2:B5)`. The total is 14 (6 + 8).
- **Both:** `A2:A5` is tested for the category and `B2:B5` supplies the amounts.

</details>

## Reference

`SUMIF(criteria_range, criterion, sum_range)` tests each cell in the first range. For each match, it adds the corresponding value from the sum range. Use ranges of the same size. A category with no matches returns zero.

| Row | A | B |
| --- | --- | ---: |
| 1 | Category | Amount |
| 2 | Books | 12 |
| 3 | Tools | 20 |
| 4 | Books | 8 |
| 5 | Tools | 5 |
| 6 | Books | 5 |

`=SUMIF(A2:A6,"Books",B2:B6)` returns 25 (12 + 8 + 5).
