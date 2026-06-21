# The Pipeline (end to end)

```
                ┌─────────────────────────────────────────────┐
                │  THE BRAIN  (campaigns/<name>/ input files)  │
                │  offer · ICP · personas · value prop ·        │
                │  messaging · good/bad fit examples            │
                └───────────────────────┬─────────────────────┘
                                        │
   ┌────────────────────────────────────┼────────────────────────────────────┐
   ▼                                    ▼                                    ▼
[1 SOURCE]  ─▶  [2 PICK PERSON]  ─▶  [3 RESEARCH]  ─▶  [4 ENRICH+VALIDATE]
 find & qualify    who owns the       per-account &      free first, paid APIs
 accounts.csv      problem, why       patterns           only for gaps; validate
                   prospects.csv      research/*.md       prospects.csv (emails)
                                                              │
                                                              ▼
                                      [5 WRITE]  ─▶  [6 PUSH TO INSTANTLY]
                                      copy from         load leads + custom
                                      research,         fields, dry-run,
                                      per segment       approve, load
                                                              │
                                                              ▼
                                                   [7 FETCH + IMPROVE]
                                                   every 3–4 days: pull stats,
                                                   diagnose, change one thing,
                                                   repeat
```

**Each stage = one playbook in `playbooks/`. Run in order, checkpoint with the user, don't skip.**

The loop at the end (stage 7 → tweak → stage 5/6 again) is what makes it ever-improving: the system sees what isn't working and changes the copy, persona, or targeting one variable at a time.
