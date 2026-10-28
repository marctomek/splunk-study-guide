# 2. Basic Searching (22%)

> **In one sentence:** You type terms into the search bar, pick a time range, and Splunk
> returns matching events newest first, with a timeline showing when they happened.

## 2.1 Run basic searches

**Concept:**
- `failed password` → both words (AND is implied)
- `"failed password"` → exact phrase
- `fail*` → wildcard
- Boolean operators must be **UPPERCASE**: `AND`, `OR`, `NOT`. Evaluated `NOT` → `OR` → `AND`; use parentheses.
- Search terms are case-insensitive; **field names are case-sensitive**.

**Query:**

```spl
index=<your_index> (fail* OR error) NOT debug
```

**Result:**
<!-- screenshot: images/02-basic-search.png -->

**Why it works:**
<!-- explain each part -->

**Exam trap:** lowercase `and`/`or` are treated as search terms, not operators.

## 2.2 Set the time range

**Concept:** The time range picker is the biggest performance lever because data is stored
by time. Default: **Last 24 hours**. Presets, relative, real-time, date range, date & time
range, advanced. In SPL, `earliest=` / `latest=` override the picker.

**Query:**

```spl
index=<your_index> earliest=-7d@d latest=@d
```

**Result:**
<!-- screenshot -->

**Exam trap:** `@d` snaps to the start of the day.

## 2.3 Identify the contents of search results

**Concept:** Tabs: **Events**, **Patterns**, **Statistics**, **Visualization** (the last two
fill only with transforming commands). Each event shows `_time`, raw text, and `host`,
`source`, `sourcetype`.

**Result:**
<!-- annotated screenshot of the results page -->

## 2.4 Refine searches

**Concept:** Click a term in an event → *Add to search*, *Exclude from search* (`NOT term`),
or *New search*. More specific = faster.

**Before / after:**

```spl
index=<your_index>
index=<your_index> sourcetype=<st> NOT status=200
```

**Result:**
<!-- event counts before and after -->

## 2.5 Use the timeline

**Concept:** Click a bar to filter, drag to select a range, double-click to zoom in;
*Zoom out* / *Zoom to selection*. Zooming filters returned results; it doesn't re-run the search.

**Result:**
<!-- screenshot of a spike on the timeline -->

## 2.6 Work with events

**Concept:** Expand an event (`>`) to see all fields. *Event Actions → Show Source* shows
surrounding raw lines. Views: **List**, **Raw**, **Table**.

**Result:**
<!-- screenshot of an expanded event -->

## 2.7 Control a search job

**Concept:** Every search is a job: **Pause**, **Stop** (keeps results so far),
**Finalize**, **Cancel**.

| Mode | Behaviour |
| --- | --- |
| Fast | Field discovery off; fastest |
| Smart (default) | Field discovery on for event searches, off for transforming searches |
| Verbose | All fields and events; slowest |

**Job Inspector** shows execution cost. **Activity → Jobs** lists jobs. Finished jobs are kept
**10 minutes** by default; sharing extends to **7 days**.

**Lab demo:** run the same search in Fast and Verbose mode and compare.

| Mode | Run time | Fields shown |
| --- | --- | --- |
| Fast | | |
| Verbose | | |

## 2.8 Save search results

**Concept:** **Job** menu: edit job settings (lifetime, sharing), send to background, inspect,
delete. **Export** as CSV, JSON, XML, raw. **Save As:** Report, Alert, Dashboard Panel, Event Type.

**Result:**
<!-- screenshot: Job menu / export dialog -->

---

### Self-check
1. Which Boolean operator is evaluated first?
2. What is the default time range?
3. Which search mode turns off field discovery?
4. How long is a job kept by default? When shared?
