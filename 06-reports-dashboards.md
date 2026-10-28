# 6. Creating Reports and Dashboards (12%)

> **In one sentence:** A report is a saved search you re-run with one click; a dashboard
> is a page of panels, each showing a search or report as a table or chart.

## 6.1 Save a search as a report

**Concept:** **Save As → Report**: title, description, content (Statistics table or
Visualization), optional Time Range Picker. Reports re-run each time they're opened unless
scheduled or accelerated.

**Report I saved:**

```spl
<the search>
```

<!-- screenshot: Save As Report dialog -->

## 6.2 Edit reports

**Concept:** Reports list → **Edit**: Description, Permissions, Schedule, Acceleration,
Clone, Embed, Delete. **Edit Search** changes the SPL. Permissions: run as Owner or User;
Private / This app / All apps; Read/Write per role.

<!-- screenshot -->

## 6.3 Reports that display statistics (tables)

**Concept:** Any transforming search → Statistics tab. Format via the column paintbrush
(precision, colour scales, data bars) and table settings.

**Query:**

```spl
index=<your_index> | stats count by <field> | sort -count
```

<!-- screenshot of a formatted table -->

## 6.4 Reports that display visualizations (charts)

**Concept:** Column, bar, line, area, pie, scatter, single value, gauge, map.

```spl
| chart count over <row_field> by <column_field>
| timechart span=1h count by <field>
```

- `timechart` puts `_time` on the X-axis (line/area over time).
- Pie charts show one series.
- **Pivot** (Datasets) builds charts point-and-click from a data model.

<!-- screenshots: one chart, one timechart -->

## 6.5 Create a dashboard

**Concept:** **Dashboards → Create New Dashboard**: title, ID, description, permissions.
Two frameworks: **Classic (Simple XML)** and **Dashboard Studio** (JSON).

## 6.6 Add a report to a dashboard

**Concept:** **Save As → Dashboard Panel** (new or existing). Panel = **inline search**
(SPL lives in the panel) or **report** (references the saved report; changes flow through).

## 6.7 Edit a dashboard

**Concept:** **Edit**: drag panels, add panels, add inputs (time picker, dropdown, text)
that pass tokens to searches, change visualizations, edit source, **Save**.

**My dashboard:**
<!-- screenshot of the finished dashboard; list its panels and the search behind each -->

| Panel | Type | Search |
| --- | --- | --- |
| | | |

---

### Self-check
1. Inline search panel vs. report panel — what's the difference?
2. Which command puts `_time` on the X-axis?
3. Name the two dashboard frameworks.
