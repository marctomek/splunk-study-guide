# Splunk Core Certified User — Study Guide

My study notes for the **Splunk Core Certified User** exam, organized by the official
[exam blueprint](https://www.splunk.com/en_us/pdfs/training/splunk-test-blueprint-user.pdf).
Every concept is written in my own words and demonstrated with searches I ran myself in
hands-on lab environments.

## About the exam

| | |
| --- | --- |
| Questions | 60 |
| Time | 60 minutes (includes 3 minutes for the exam agreement) |
| Level | Entry level |
| Prerequisites | None |

## Domains

| # | Domain | Weight | Notes | Status |
| --- | --- | --- | --- | --- |
| 1 | Splunk Basics | 5% | [01-basics.md](01-basics.md) | ⬜ |
| 2 | Basic Searching | 22% | [02-searching.md](02-searching.md) | ⬜ |
| 3 | Using Fields in Searches | 20% | [03-fields.md](03-fields.md) | ⬜ |
| 4 | Search Language Fundamentals | 15% | [04-search-language.md](04-search-language.md) | ⬜ |
| 5 | Basic Transforming Commands | 15% | [05-transforming-commands.md](05-transforming-commands.md) | ⬜ |
| 6 | Creating Reports and Dashboards | 12% | [06-reports-dashboards.md](06-reports-dashboards.md) | ⬜ |
| 7 | Creating and Using Lookups | 6% | [07-lookups.md](07-lookups.md) | ⬜ |
| 8 | Creating Scheduled Reports and Alerts | 5% | [08-scheduled-reports-alerts.md](08-scheduled-reports-alerts.md) | ⬜ |

Domains 2–5 are 72% of the exam, so they get the most examples.

Quick reference: [spl-cheatsheet.md](spl-cheatsheet.md)

## How each topic is written

```
### <blueprint number> <topic>
Concept       — what it is, in plain words
Query         — an SPL search I ran
Result        — screenshot or short output from my lab
Why it works  — what each part of the query does
Exam trap     — the detail most likely to be tested
```

## Lab environment

Examples were run in cloud lab environments (TryHackMe) and on Splunk Enterprise with
Splunk's free tutorial data, so readers can reproduce them:

- Splunk Enterprise free trial: https://www.splunk.com/en_us/download/splunk-enterprise.html
- Tutorial data (`tutorialdata.zip`): see the *Search Tutorial* in Splunk Docs
- Boss of the SOC (BOTS) datasets: published by Splunk on GitHub

Lab screenshots are cropped to my own queries and results. This repo contains no room
answers, flags, or copied course material.

## Progress

- [ ] 1. Splunk Basics
- [ ] 2. Basic Searching
- [ ] 3. Using Fields in Searches
- [ ] 4. Search Language Fundamentals
- [ ] 5. Basic Transforming Commands
- [ ] 6. Reports and Dashboards
- [ ] 7. Lookups
- [ ] 8. Scheduled Reports and Alerts
- [ ] Self-check passed (see end of each file)
- [ ] Exam booked
