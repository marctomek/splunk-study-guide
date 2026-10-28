# 5. Basic Transforming Commands (15%)

> **In one sentence:** Transforming commands turn events into a table of numbers, and
> that table feeds every chart and dashboard.

Transforming commands put results on the **Statistics** and **Visualization** tabs.
`top`, `rare`, `stats`, `chart`, `timechart` are all transforming.

## 5.1 top

**Concept:** Most common values with `count` and `percent`. Default **10** results.

| Argument | Effect |
| --- | --- |
| `limit=N` | Number of values (`0` = all) |
| `by field` | Top values per group |
| `countfield=` / `percentfield=` | Rename output columns |
| `showcount=f` / `showperc=f` | Hide a column |
| `useother=t` | Add an OTHER row |

**Query:**

```spl
index=<your_index> sourcetype=<st> | top limit=5 <field> showperc=f
```

**Result:**
<!-- screenshot -->

## 5.2 rare

**Concept:** Least common values. Same arguments and default (10) as `top`.

**Query:**

```spl
index=<your_index> sourcetype=<st> | rare <field>
```

**Result:**
<!-- screenshot -->

**Why it's useful:** rare values are often the interesting ones in security (an unusual
user agent, a one-off source IP).

## 5.3 stats

| Function | Returns |
| --- | --- |
| `count` | Number of events |
| `count(field)` | Events that have that field |
| `dc(field)` | Distinct count |
| `sum(field)` | Total |
| `avg(field)` | Mean |
| `min()` / `max()` | Smallest / largest |
| `list(field)` | All values, with duplicates, in order |
| `values(field)` | Unique values, sorted |

**Query:**

```spl
index=<your_index> sourcetype=<st>
| stats count AS Events dc(<user_or_ip_field>) AS "Unique sources" values(<field>) AS Values by <group_field>
```

**Result:**
<!-- screenshot -->

**Exam traps:**
- `top` adds percent, sorts descending, limits to 10; `stats count by x` returns every value with no percent.
- `values()` is unique and sorted; `list()` keeps duplicates and order.

---

### Self-check
1. Default number of results for `top` and `rare`?
2. Which function returns a distinct count?
3. How do you rename a `stats` output column?
