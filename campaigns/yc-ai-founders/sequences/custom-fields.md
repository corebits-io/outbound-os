# Custom fields — YC AI Founders sequence

## Per-lead (columns in `leads-upload.csv` → mapped to sequencer variables)
| Variable | What it is | Example |
|---|---|---|
| `{{first_name}}` | Founder first name | Jeffrey |
| `{{companyName}}` | Company name | Confident AI |
| `{{trigger}}` | The **specific, true** opener observation (from research) | Saw DeepEval crossed 10k stars |
| `{{problem}}` | The problem their product solves (for the Reddit/LinkedIn line) | shipping LLM features without real evals |

## Campaign-level (set once in the sequencer)
| Variable | What it is |
|---|---|
| `{{sender_name}}` | Your name |
| `{{sender_address}}` | Physical mailing address — required for CAN-SPAM |

> `{{trigger}}` is the line that makes it human — never leave it blank or generic. Emails are filled by `/find-verify-emails` at runtime; this public demo ships with the `email` column blank.
