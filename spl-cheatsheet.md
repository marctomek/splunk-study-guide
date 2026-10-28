# SPL Cheat Sheet

Every command the Core Certified User blueprint touches, with one working example.

## Searching

| What | Syntax |
| --- | --- |
| Both terms | `failed password` |
| Exact phrase | `"failed password"` |
| Wildcard | `fail*` |
| Boolean (UPPERCASE) | `(error OR fail*) NOT debug` |
| Field value | `status=404` |
| Not equal (field must exist) | `status!=200` |
| NOT (includes events without the field) | `NOT status=200` |
| Numeric compare | `bytes>5000` |
| List of values | `status IN (404, 500, 503)` |
| Index / sourcetype | `index=web sourcetype=access_combined` |
| Time in SPL | `earliest=-24h latest=now`, `earliest=-7d@d` |

## Shaping results

| Command | Example |
| --- | --- |
| `table` | `\| table _time clientip action status` |
| `fields` | `\| fields clientip action` / `\| fields - _raw` |
| `rename` | `\| rename clientip AS "Client IP"` |
| `dedup` | `\| dedup clientip` |
| `sort` | `\| sort -count, clientip` / `\| sort 0 -bytes` |
| `head` / `tail` | `\| head 10` |

## Transforming

| Command | Example |
| --- | --- |
| `top` | `\| top limit=5 product_name by categoryId showperc=f` |
| `rare` | `\| rare useragent` |
| `stats` | `\| stats count dc(clientip) AS visitors by status` |
| `chart` | `\| chart count over product_name by action` |
| `timechart` | `\| timechart span=1h count by status` |

## stats functions

`count` · `count(field)` · `dc(field)` · `sum()` · `avg()` · `min()` · `max()` ·
`list()` (all, ordered) · `values()` (unique, sorted)

## Lookups

| Command | Example |
| --- | --- |
| Read a lookup | `\| inputlookup products_lookup` |
| Enrich events | `\| lookup products_lookup productId OUTPUT product_name price` |
| Different field name | `\| lookup products_lookup productId AS pid OUTPUT product_name` |
| Write results | `\| outputlookup my_results.csv` |

## Numbers worth memorizing

| Fact | Value |
| --- | --- |
| Default time range | Last 24 hours |
| Interesting field threshold | ≥ 20% of events |
| `top` / `rare` default | 10 results |
| `sort` default limit | 10,000 (`sort 0` = no limit) |
| Job lifetime | 10 minutes (7 days when shared) |
| Boolean order | NOT → OR → AND |
| Default selected fields | host, source, sourcetype |
