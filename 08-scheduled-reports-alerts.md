# 8. Creating Scheduled Reports and Alerts (5%)

> **In one sentence:** A scheduled report runs on a timer and delivers results; an alert
> also runs on a timer (or in real time) but only acts when a condition is met.

## 8.1 Describe scheduled reports

**Concept:** Use them for regular email summaries, fast dashboards (panels show the cached
result), and moving heavy searches to quiet hours.

## 8.2 Configure scheduled reports

**Concept:** Reports → **Edit → Edit Schedule** → *Schedule Report*:
- **Schedule:** hourly, daily, weekly, monthly, or cron (`0 6 * * 1` = 06:00 every Monday)
- **Time range** each run covers
- **Schedule priority:** Default, Higher, Highest
- **Schedule window:** lets Splunk delay the run if busy
- **Trigger actions:** email, script, output to lookup, log event, webhook

**My scheduled report:**

| Setting | Value |
| --- | --- |
| Search | |
| Schedule / cron | |
| Time range | |
| Action | |

<!-- screenshot -->

## 8.3 Describe alerts

**Concept:** Alert = saved search + **trigger condition** + **actions**.

| Type | How it runs |
| --- | --- |
| Scheduled | Runs on a schedule, checks the condition each run |
| Real-time | Runs continuously; per-result or rolling window (e.g. 10 events in 5 min); heavier |

## 8.4 Create alerts

**Concept:** **Save As → Alert:**
1. Title, description, permissions (Private / Shared in App)
2. Type: Scheduled or Real-time
3. Trigger condition: number of results / hosts / sources, or **Custom** (`search count > 100`)
4. Trigger **Once** or **For each result**
5. **Throttle** to suppress repeats
6. Actions: Add to Triggered Alerts, email, log event, output to lookup, script, webhook

**My alert:**

```spl
<the search, e.g. failed logins grouped by source>
```

| Setting | Value |
| --- | --- |
| Type | |
| Condition | |
| Trigger | |
| Throttle | |
| Actions | |

<!-- screenshot -->

## 8.5 View fired alerts

**Concept:** **Activity → Triggered Alerts** lists fired alerts — only if the alert has the
**Add to Triggered Alerts** action. Severity: Info, Low, Medium, High, Critical. Records
expire (24 hours by default).

<!-- screenshot of my alert firing -->

---

### Self-check
1. Which action is required for an alert to show in Triggered Alerts?
2. Scheduled vs real-time alert — which uses more resources?
3. What does throttling do?
