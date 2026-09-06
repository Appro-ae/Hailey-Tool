# PM Flightdeck

A single-file task control tool for a product manager. It encodes the practices that hold up across the market, and checks your board against them every time you open it, instead of one more to-do list.

Open `pm-flightdeck/index.html` in any browser. No build, no install, no account. Tasks are saved in the browser, or synced through Claude when the same file is published as a Claude artifact.

## How work is organised

```
Project  (code, sponsor, objective, target date, status)
  └── Task  (title, why, category, status, RICE, due, Definition of Done …)
Category (Management, Billing, Product discovery, Delivery, Compliance, Stakeholder, or your own)
```

- **Projects** are containers. Create one from the Projects view or with `p`. Each shows progress, open, in-flight, overdue and blocked counts. The project selector in the top bar scopes every other view to one project, or to all.
- **Tasks** belong to a project and carry one category. Capture always lands in the selected project's backlog.
- **Categories** describe the kind of work, across projects. Add them in the Projects view, in Settings, or directly from the task form with "+ New category".

## What it does

| View | Job | Practice it encodes |
|---|---|---|
| **Projects** | Portfolio of projects with progress and risk counts, tasks without a project, category management | Work breakdown structure (PMBOK) |
| **Today** | The day's cockpit: at most three focus tasks, overdue items, due this week, items waiting on others | Most-important-tasks (Ivy Lee method), GTD daily review |
| **Board** | Six-column Kanban with WIP limits and age-in-column on every card, drag to move | Kanban (Anderson), Personal Kanban WIP of three |
| **Prioritise** | RICE ranking table with inline scoring, and an Eisenhower matrix with one-click I/U toggles | RICE (Intercom), Eisenhower matrix (Covey) |
| **Health check** | Fifteen rules run against the board (scoped to the selected project), each with its rationale and source, and a 0-100 score | Flow metrics, Definition of Done, outcomes over outputs, OKR alignment |
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
| Not under a project | Info | Work breakdown structure (PMBOK) |
| Title under three words | Info | Next-action thinking (Allen) |
| Backlog item untouched for a month | Info | Backlog refinement |
| Weekly review overdue | Info | GTD weekly review |

Score starts at 100. Critical costs 12 per finding, warning 5, info 2, capped at 30 per rule. Thresholds are editable in Settings.

The full reasoning behind each rule, in Rationale → Business base → Hypothesis → Experiment → Conclusion form, is in [`docs/best-practices.md`](docs/best-practices.md).

## Data

Two modes, chosen automatically by where the page runs:

| Mode | Where data lives | Persists across devices | Backend |
|---|---|---|---|
| **Hosted** (the Claude artifact link) | Claude's artifact database, server-side, one document per project and task | Yes, and live-updates in every open tab | Yes, provided by the Claude artifact platform (`db` capability) |
| **Local file** (opening `index.html`) | The browser's localStorage | No, one browser only | None |

Use *Settings & data → Export JSON backup* before clearing site data or changing device in local mode. Import JSON restores projects, tasks and settings.
- **Export CSV** produces Jira- and Sheets-friendly columns: Issue key, Project, Category, Summary, Description, Status, Priority, Due date, Labels, Objective, Stakeholder, RICE inputs and score, Created, Started, Done.
- **Import JSON** replaces the board with a previous backup.
- Example tasks (marked *Example*) load on first open so every view is legible. Remove them from Settings when you start real work.

## Keyboard

| Key | Action |
|---|---|
| `/` | Jump to the capture bar |
| `n` | New task |
| `p` | New project |
| `Esc` | Close the task drawer or settings |

## Layout of this repository

```
pm-flightdeck/index.html   the tool, one self-contained file
docs/best-practices.md     the research base behind every feature and rule
docs/sample-tasks.json     the example projects and tasks, regenerable from the page
```
