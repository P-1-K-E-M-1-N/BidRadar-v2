# Airtable Schema — BidRadar

Build exactly this, nothing more. Update this file whenever the schema changes.

## CUSTOMERS

| Field | Type |
|---|---|
| name | Single line text |
| email | Email |
| company | Single line text |
| trade_naics_codes | Multiple select |
| state | Single line text |
| service_radius | Number (miles) |
| keywords | Long text (comma-separated) |
| certifications | Multiple select (SDVOSB, 8(a), HUBZone, WOSB, etc.) |
| min_contract_value | Currency |
| max_contract_value | Currency |
| status | Single select: trial / active / churned |
| stripe_id | Single line text |

## OPPORTUNITIES

| Field | Type |
|---|---|
| notice_id | Single line text (primary, unique) |
| title | Single line text |
| agency | Single line text |
| naics | Single line text |
| response_deadline | Date |
| place_of_performance | Single line text |
| posted_date | Date |
| description_excerpt | Long text |
| url | URL |
| set_aside_type | Single select |

## MATCHES

| Field | Type |
|---|---|
| customer | Link to CUSTOMERS |
| opportunity | Link to OPPORTUNITIES |
| match_score | Number (0–100) |
| match_reasoning | Long text |
| included_in_digest | Checkbox |
| digest_date | Date |

Write rule (enforced in Make, not Airtable): only create a MATCHES record when `match_score ≥ 70` AND `eligibility_flag ≠ "ineligible"`.

## DIGEST_LOG

| Field | Type |
|---|---|
| customer | Link to CUSTOMERS |
| date_sent | Date |
| bids_included | Number |
| opened | Checkbox (if tracked) |
