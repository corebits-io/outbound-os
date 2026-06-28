# Custom fields — YC AI Founders sequence

## Per-lead (columns in `leads-upload.csv` → mapped to sequencer variables)
| Variable | What it is | Example |
|---|---|---|
| `{{first_name}}` | Founder first name | Nishant |
| `{{company}}` | Company name | Docket |
| `{{problem}}` | The problem their product solves (for the "posting about {{problem}}" line) | flaky tests |

## Campaign-level (set once in the sequencer, same for everyone)
| Variable | What it is |
|---|---|
| `{{sender_name}}` | Your name |
| `{{sender_address}}` | Physical mailing address — required for CAN-SPAM |

> Emails are filled by `/find-verify-emails` at runtime — this public demo ships with the `email` column blank.
