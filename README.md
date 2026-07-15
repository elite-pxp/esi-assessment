# Educator Strength Index™

The Educator Strength Index (ESI) is a browser-based, 40-statement self-reflection assessment. It calculates one primary educator-strength result, displays its color identity, and prepares that text for a GoHighLevel form.

## How the assessment works

Each statement is answered on a five-point scale:

| Answer | Value |
| --- | ---: |
| Strongly Disagree | 1 |
| Disagree | 2 |
| Neutral | 3 |
| Agree | 4 |
| Strongly Agree | 5 |

The 40 statements are divided evenly across five categories. Each category contains eight questions, so every category score can range from 8 to 40.

| Color | Category | Questions |
| --- | --- | --- |
| Blue | Relationship Builder | 2, 6, 11, 15, 19, 24, 28, 37 |
| Green | Innovative Educator | 1, 9, 14, 22, 29, 30, 35, 39 |
| Red | Inspirational Leader | 7, 8, 12, 16, 27, 31, 32, 33 |
| Gold | Strategic Planner | 3, 10, 13, 17, 21, 23, 34, 36 |
| Purple | Growth Champion | 4, 5, 18, 20, 25, 26, 38, 40 |

## How one result is selected

The assessment always returns exactly one primary result.

1. Add the eight answer values assigned to each category.
2. Rank the five category totals from highest to lowest.
3. The category with the highest total is the primary result.
4. If two or more totals are tied, compare how many `5` responses each tied category received. The category with more `5` responses wins.
5. If still tied, compare the number of `4` responses, then `3`, then `2`, then `1`.
6. If the score and complete response-intensity pattern are still identical, use this fixed final order:
   1. Relationship Builder (Blue)
   2. Innovative Educator (Green)
   3. Inspirational Leader (Red)
   4. Strategic Planner (Gold)
   5. Growth Champion (Purple)

The last rule is only a deterministic technical fallback. It prevents identical response patterns from producing multiple results.

### Example

If the totals are:

- Relationship Builder: 31
- Innovative Educator: 27
- Inspirational Leader: 25
- Strategic Planner: 29
- Growth Champion: 33

The result is `Growth Champion (Purple)` because 33 is the highest score.

The page may still display all five scores as a transparent breakdown, but those scores are not additional results.

## Auto-populated result format

The read-only form field named **Educator Strength Result** receives one text value:

- `Relationship Builder (Blue)`
- `Innovative Educator (Green)`
- `Inspirational Leader (Red)`
- `Strategic Planner (Gold)`
- `Growth Champion (Purple)`

## Assessment flow

1. The participant answers all 40 statements.
2. A three-second calculation screen appears.
3. The single primary result and five-score breakdown are displayed.
4. The result text is automatically mapped into the embedded GoHighLevel result field.
5. The participant enters their contact information and submits the form.
6. GoHighLevel receives the prefilled result and can send the configured workflow email.

The assessment page also includes a **How scoring works** FAQ dialog in the top bar and footer. It explains the same one-result calculation and color identities directly to participants.

## GoHighLevel form structure

Create these fields in this order:

1. **Educator Strength Result**
   - Contact custom field
   - Single Line text
   - Required
   - Visible
   - No default value
2. **Full Name**
   - Standard name field
   - Required
3. **Email Address**
   - Standard email field
   - Required
4. **School**
   - Dropdown: Austell, Mableton, Other
5. **Position**
   - Dropdown: Teacher, Lead Teacher, Assistant Teacher, Director, Assistant Director, Administrator, Other
6. **Years of Experience**
   - Dropdown: Less than 1 year, 1 to 2 years, 3 to 5 years, 6 to 10 years, 11 to 15 years, 16 years or more
7. **Confirmation**
   - Required checkbox
   - `I confirm that I answered the assessment honestly and completed all 40 statements.`
8. **Submit button**
   - `Send My Results`

The connected GoHighLevel form uses:

- Form ID: `0S0jyfclu3SockPSSiLn`
- Result custom-field ID: `ngUeLYN7ddhssOjLvEwI`
- Result custom-field key: `contact.educator_strength_result`
- Form prefill parameter: `single_line_773jh`

The assessment adds the calculated result to the iframe URL using the prefill parameter. For example, `single_line_773jh=Growth Champion (Purple)` populates the GHL result field before submission. Email delivery still depends on an active GoHighLevel workflow triggered by this form submission.

## Run locally

The project is a static HTML application and does not require Node.js or a database.

From the project directory, run:

```bash
python3 -m http.server 4173
```

Then open:

```text
http://localhost:4173/
```

The assessment uses `index.html`, so it loads at the domain root locally and on production hosting.

## Current files

- `index.html` — complete assessment interface and scoring logic
- `README.md` — calculation, hosting, and integration documentation

## Important note

This assessment is a professional self-reflection tool. If its results will be used for hiring, promotion, formal evaluation, or other high-impact decisions, the questionnaire and tie-breaking method should be reviewed and validated by a qualified assessment professional.
