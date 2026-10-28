# 7. Creating and Using Lookups (6%)

> **In one sentence:** A lookup is a reference table, usually a CSV, that Splunk joins
> onto events so a code in the log becomes a readable name or value.

## 7.1 Describe lookups

**Concept:** Lookups add fields at search time and **don't change indexed data**.
Types: CSV file (most common), KV store, external (script), geospatial.

## 7.2 Examine a lookup file example

The header row holds field names; one column matches a field already in the events.

```csv
productId,product_name,price
DB-SG-G01,Mediocre Kingdoms,24.99
DC-SG-G02,Dream Crusher,39.99
MB-AG-G07,Manganiello Bros.,39.99
```

**My lookup file:** _(sample I created for the lab — no copied data)_

```csv

```

## 7.3 Create a lookup file and a lookup definition

**Concept:** Two steps under **Settings → Lookups**:
1. **Lookup table files → New:** upload the CSV (name ends `.csv`)
2. **Lookup definitions → New:** name, type *File-based*, select the file. Searches use the definition name.

**Verify:**

```spl
| inputlookup <definition_name>
```

<!-- screenshot -->

## 7.4 Configure an automatic lookup

**Concept:** **Settings → Lookups → Automatic lookups → New:** definition, **sourcetype**,
input field (lookup ↔ event), output fields. Fields then appear on every event of that
sourcetype with no `lookup` command.

<!-- screenshot of the automatic lookup settings -->

## 7.5 Use the lookup in searches

**Query:**

```spl
index=<your_index> sourcetype=<st>
| lookup <definition_name> <match_field> OUTPUT <new_field_1> <new_field_2>
| stats count by <new_field_1>
```

<!-- screenshot -->

- Different field names: `| lookup <def> <lookup_field> AS <event_field> OUTPUT ...`
- `OUTPUT` overwrites existing fields; `OUTPUTNEW` only fills empty ones.
- `inputlookup` reads a lookup; `outputlookup` writes results to one.

---

### Self-check
1. Do lookups change indexed data?
2. Which two objects must exist before a CSV lookup can be used?
3. `OUTPUT` vs `OUTPUTNEW`?
