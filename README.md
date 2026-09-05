# PM Flightdeck

A single-file task control tool for a product manager. It encodes the practices that hold up across the market, and checks your board against them every time you open it, instead of one more to-do list.

Open `pm-flightdeck/index.html` in any browser. No build, no install, no account. Tasks are saved in the browser, or synced through Claude when the same file is published as a Claude artifact.

## What it does

| View | Job | Practice it encodes |
|---|---|---|
| **Today** | The day's cockpit: at most three focus tasks, overdue items, due this week, items waiting on others | Most-important-tasks (Ivy Lee method), GTD daily review |
| **Board** | Six-column Kanban with WIP limits and age-in-column on every card, drag to move | Kanban (Anderson), Personal Kanban WIP of three |
| **Prioritise** | RICE ranking table with inline scoring, and an Eisenhower matrix with one-click I/U toggles | RICE (Intercom), Eisenhower matrix (Covey) |
| **Health check** | Fourteen rules run against the whole board, each with its rationale and source, and a 0-100 score | Flow metrics, Definition of Done, outcomes over outputs, OKR alignment |
| **Metrics** | Throughput per week, cycle time with 85th percentile, aging work in progress, work by quadrant and by objective | Actionable Agile metrics (Vacanti), Little's Law |
| **Weekly review** | Nine-step ritual checklist, an auto-generated status report, review history | GTD weekly review, Scrum retrospective cadence |

Every task carries the fields a PM needs and no more: title (verb + object), the outcome it moves, the objective it serves, status, important and urgent flags, RICE inputs, target date, stakeholder, tags, a Definition of Done checklist, and a named blocker when it is waiting.

## The health check

The check is the part that makes the tool opinionated. Each rule is a documented practice turned into a test:

| Rule | Severity | Source |
|---|---|---|
| Overdue task never re-planned | Critical | Kanban explicit policies |
| WIP limit exceeded | Critical | Little's Law, Personal Kanban |
| In progress with no update past the stale threshold | Warning | Aging WIP (Vacanti) |
| Blocked without a named blocker | Warning | Kanban blocker clustering |
| Blocked longer than the escalation threshold | Warning | Kanban service delivery review |
| No outcome stated | Warning | Outcomes over Output (Seiden), The Build Trap (Perri) |
| In progress with no target date | Warning | Commitment point, time-boxing |
| Done with an open Definition of Done item | Warning | Scrum Guide |
| More than 40% of open work is "Do first" | Warning | Eisenhower matrix (Covey) |
| Committed (Next) but no RICE score | Info | RICE (Intercom) |
| Not linked to an objective | Info | OKRs (Doerr) |
| Title under three words | Info | Next-action thinking (Allen) |
| Backlog item untouched for a month | Info | Backlog refinement |
| Weekly review overdue | Info | GTD weekly review |

Score starts at 100. Critical costs 12 per finding, warning 5, info 2, capped at 30 per rule. Thresholds are editable in Settings.

The full reasoning behind each rule, in Rationale → Business base → Hypothesis → Experiment → Conclusion form, is in [`docs/best-practices.md`](docs/best-practices.md).

## Data

- **Local mode** (opening the file): stored in the browser's localStorage. Use *Settings & data → Export JSON backup* before clearing site data or changing device.
- **Synced mode** (published as a Claude artifact with the `db` capability): stored with the page and updated live across every place you open it.
- **Export CSV** produces Jira- and Sheets-friendly columns: Issue key, Summary, Description, Status, Priority, Due date, Labels, Objective, Stakeholder, RICE inputs and score, Created, Started, Done.
- **Import JSON** replaces the board with a previous backup.
- Example tasks (marked *Example*) load on first open so every view is legible. Remove them from Settings when you start real work.

## Keyboard

| Key | Action |
|---|---|
| `/` | Jump to the capture bar |
| `n` | New task |
| `Esc` | Close the task drawer or settings |

## Layout of this repository

```
pm-flightdeck/index.html   the tool, one self-contained file
docs/best-practices.md     the research base behind every feature and rule
docs/sample-tasks.json     the example data set, regenerable from the page
```
