# Input Schema

The input file is `market_day_analitic.json`.

Required fields:

- `market`
- `session_date`
- `overview`
- `top_gainers`
- `top_losers`

Expected list item fields for `top_gainers` and `top_losers`:

- `ticker`
- `company`
- `change_pct`
- `liquidity_value`
- `commentary_note`

Optional fields:

- `calendar_reference_date`
- `used_latest_completed_session`
- `liquidity_metric`
- `sources`

Validation rules:

- `session_date` must be shown exactly as provided.
- `top_gainers` and `top_losers` should each contain up to 5 items.
- `change_pct` should be numeric.
- Missing required fields should stop the workflow with an explicit error message.

