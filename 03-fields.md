# 3. Using Fields in Searches (20%)

> **In one sentence:** A field is a name=value pair Splunk pulls out of each event, like
> `status=404`; searching on fields is far more precise than searching on raw words.

## 3.1 Understand fields

**Concept:** Fields are extracted at **search time** (schema-on-read).

- **Default fields:** `host`, `source`, `sourcetype`, `index`, `_time`, `_raw` (leading `_` = internal)
- **Automatically extracted:** `key=value` pairs and fields defined for the sourcetype
- Field **names** are case-sensitive; field **values** are not

**Lab demo:** _what fields does this sourcetype have?_

```spl
index=<your_index> sourcetype=<st> | fieldsummary | table field count distinct_count
```

**Result:**
<!-- screenshot -->

## 3.2 Use fields in searches

**Concept:**
- `=` / `!=` any value; `<` `>` `<=` `>=` numbers
- Wildcards: `status=4*`
- `status IN (404, 500, 503)`
- Quote values with spaces: `product_name="Dream Crusher"`
- `index` + `sourcetype` + time are the most efficient filters

**Query — the `!=` vs `NOT` test:**

```spl
index=<your_index> status!=200
index=<your_index> NOT status=200
```

**Result:**

| Search | Event count |
| --- | --- |
| `status!=200` | |
| `NOT status=200` | |

**Why the counts differ:** `!=` only returns events that **have** the field.
`NOT` also returns events with **no** `status` field at all.

**Exam trap:** this is the single most tested fields question.

## 3.3 Use the fields sidebar

**Concept:**
- **Selected fields:** shown under every event (default `host`, `source`, `sourcetype`)
- **Interesting fields:** present in **≥ 20%** of events
- **All Fields** link to select more
- `a` = string, `#` = number; the number beside a field = distinct values
- Click a field: top 10 values, plus *Top values*, *Top values by time*, *Rare values*,
  and for numbers *Average/Max/Min over time*

**Result:**
<!-- annotated screenshot of the sidebar and a field window -->

---

### Self-check
1. Name the three default selected fields.
2. What % of events must contain a field for it to be "interesting"?
3. Is `Status=404` the same search as `status=404`?
