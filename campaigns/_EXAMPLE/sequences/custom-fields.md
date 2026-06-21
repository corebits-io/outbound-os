# Custom fields — Segment A sequence

> ⚠️ FICTIONAL SAMPLE. Every `{{variable}}` the sequence uses, and where its value comes from.
> The push step (Playbook 06) needs one column per variable in the upload file.

| Variable | What it is | Source | Example value |
|---|---|---|---|
| `{{first_name}}` | Prospect first name | `prospects.csv` → `first_name` | Sarah |
| `{{company}}` | Company name | `prospects.csv` → `company` | FlowMetrics |
| `{{observation}}` | The specific, true hook (full phrase) | per-account `research/<domain>.md` | hiring 3 CSMs right now |
| `{{observation_short}}` | Short version for the subject line | derived from `{{observation}}` | the 3 CSM hires |
| `{{peer_example}}` | A comparable (fictional/anonymized) customer for proof | value-prop file / sales-approved list | a similar PLG analytics team |
| `{{sender_name}}` | Your sending identity | infrastructure / sender settings | Alex Rivera |
| `{{sender_title}}` | Sender title | sender settings | Founder |
| `{{sender_address}}` | Physical mailing address (compliance) | your company details | 123 Example St, City, ST |

**Notes**
- `{{observation}}` and `{{observation_short}}` are the personalization that makes this not-generic — they must be true and per-account. Never ship a row with these blank; fall back to a segment-safe line or drop the lead.
- `{{peer_example}}` must be a real, reference-approved customer in a live campaign. In this sample it's kept generic on purpose.
- `{{sender_address}}` + the unsubscribe line in the footer are compliance requirements, not optional.
