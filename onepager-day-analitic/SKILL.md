---
name: onepager-day-analitic
description: Create a one-page PDF presentation from a market_day_analitic JSON result file. Use when the user asks to turn market_day_analitic.json into a one-page presentation, a one-pager, or a daily market slide with bar charts for the top gainers and top losers. Read market_day_analitic.json as the input contract and produce a PDF file named day_presentation.pdf.
---

# Onepager Day Analitic

## Overview

Create a single-page presentation in PDF format from `market_day_analitic.json`. Present the session date, a short market summary, and two bar charts: one for the leaders of growth and one for the leaders of decline.

## Example User Requests

- Use $onepager-day-analitic and turn market_day_analitic.json into a PDF.
- Create a one-page presentation from the daily market analytics JSON.
- Build a one-pager with gainers and losers charts.
- Make a daily market slide and save it as PDF.

## Required Outcome

Always deliver:

1. A PDF file named `day_presentation.pdf`.
2. Exactly one page.
3. A headline with the market name and session date.
4. A short summary based on the `overview` field.
5. A bar chart for top gainers.
6. A bar chart for top losers.
7. A compact source block if source links are available.

## Input Contract

- Read `market_day_analitic.json`.
- Expect the schema described in `references/input-schema.md`.
- If required fields are missing, stop and report which fields are missing instead of inventing data.

## Workflow

1. Read and validate `market_day_analitic.json`.
2. Extract the session date, overview, top gainers, top losers, and sources.
3. Build a one-page layout with a clear visual hierarchy.
4. Place gainers and losers in separate bar charts.
5. Use positive color for gainers and negative color for losers.
6. Keep labels readable and avoid overcrowding.
7. Export the final result to `day_presentation.pdf`.

## Layout Rules

- Keep everything on one page.
- Use a title area at the top with market name and session date.
- Place the short summary under the title.
- Put the gainers chart on the left or top.
- Put the losers chart on the right or bottom.
- Add a small footer with source names or links if space allows.

## Chart Rules

- Build vertical or horizontal bar charts depending on what best preserves legibility.
- Show exactly 5 gainers and 5 losers if available.
- Label each bar with ticker and percentage change.
- Sort gainers from highest to lowest change.
- Sort losers from largest decline to smallest decline.
- Use consistent scale formatting for both charts.

## Writing Rules

- Keep the summary brief.
- Do not add investment advice.
- Do not claim causes that are not present in the input data.
- Preserve the exact session date from the JSON.

## Edge Cases

- If fewer than 5 gainers or losers are present, render only the available rows and state that the input was incomplete.
- If source arrays are empty, omit the footer source block.
- If the PDF generator requires an intermediate format such as HTML or PPTX, generate it only as a temporary artifact and keep `day_presentation.pdf` as the final output.

## References

- Use `references/input-schema.md` for the expected JSON fields.
- Use `references/layout-guide.md` for the recommended one-page structure.

