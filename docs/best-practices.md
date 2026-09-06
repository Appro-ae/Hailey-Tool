# Best practices behind PM Flightdeck

Every feature and health rule in the tool traces back to a practice with a documented origin and market adoption. This document follows one structure for each: **Rationale → Business base → Hypothesis → Experiment → Conclusion**, so a rule can be challenged and replaced with evidence rather than opinion.

Sources are the primary publications named below. Where a claim is a practitioner heuristic rather than a measured result, it is labelled as such. No figures are quoted that the sources do not contain.

---

## 1. Capture everything, decide later (GTD)

**Rationale.** Open loops held in memory compete for attention with the work in front of you. A trusted capture point removes that load.

**Business base.** Allen, *Getting Things Done* (2001): capture, clarify, organise, reflect, engage. Adopted in personal productivity systems across Todoist, Things, OmniFocus and Notion templates. The "next action must start with a verb" rule comes from the same source.

**Hypothesis.** A one-field capture bar that always files into Backlog, plus a title rule enforced by the health check, will produce a backlog that can be triaged in the weekly review rather than one that is re-read every day.

**Experiment.** Count captures per week and the share still in Backlog after 30 days (the *Backlog item untouched for a month* rule). If the share stays above roughly a third, the triage cadence is the problem, not the capture.

**Conclusion in the tool.** Capture bar on every view; Backlog is the only landing column; *Vague task title* and *Backlog untouched* rules.

## 2. Limit work in progress (Kanban, Little's Law)

**Rationale.** Cycle time = work in progress ÷ throughput (Little's Law). With throughput fixed by capacity, the only lever on how long anything takes is how much is started.

**Business base.** Anderson, *Kanban: Successful Evolutionary Change for Your Technology Business* (2010): visualise, limit WIP, manage flow, make policies explicit. Benson and Barry, *Personal Kanban* (2011): two rules, visualise your work and limit WIP, with three as the recommended personal limit. Jira, Trello, Linear and Azure Boards all expose column WIP limits.

**Hypothesis.** A visible limit on In progress, Blocked and In review, with an over-limit column highlighted, forces a "what do I stop" conversation before a "what do I start" one, and median cycle time falls.

**Experiment.** Track median and 85th-percentile cycle time on the Metrics view over four to six weeks with limits enforced against a prior period without. A drop in the 85th percentile with stable throughput confirms the hypothesis.

**Conclusion in the tool.** Per-column WIP limits (default 3 / 3 / 3, Next 6), the *WIP limit exceeded* rule, and the Today tile that shows WIP against the combined limit.

## 3. Watch aging work, not only finished work (Actionable Agile)

**Rationale.** Cycle time is only known after an item finishes. Age of items still in progress is the leading indicator; by the time an item is the longest ever it is too late.

**Business base.** Vacanti, *Actionable Agile Metrics for Predictability* (2015): the four flow metrics (WIP, cycle time, throughput, work item age) and the use of percentiles rather than averages for forecasting. Kanban University's *Kanban Maturity Model* uses the same set.

**Hypothesis.** Showing each open item's age against the historical 85th-percentile cycle time surfaces at-risk work days before it is overdue.

**Experiment.** Compare the share of items that end up overdue between items flagged as aged and those not. If flagged items are not more likely to run late, the threshold is wrong.

**Conclusion in the tool.** Age-in-column on every card, the *Aging work in progress* chart with the P85 reference line, the *Stale work in progress* rule, and the *Aged work in progress* tile.

## 4. Score before you commit (RICE)

**Rationale.** A PM's queue is contested by stakeholders. A shared formula moves the argument from "who shouts loudest" to inputs that can be disputed one at a time.

**Business base.** McBride, "RICE: Simple prioritization for product managers", Intercom blog (2016). Score = Reach × Impact × Confidence ÷ Effort, with impact on a 0.25 to 3 scale and confidence at 100 / 80 / 50%. Widely adopted in Productboard, Aha! and airfocus as a built-in framework. ICE (Ellis, Sean, GrowthHackers) is the lighter-weight cousin; RICE was chosen because Reach is a real number and Confidence is a stated assumption, both of which invite evidence.

**Hypothesis.** Items in Next carry a score, and the ranked order of Next is followed, so work with higher expected value per effort ships first.

**Experiment.** At each weekly review, compare the order work actually started against the RICE order. Repeated deviation with no documented reason is either a bad scoring input or a hidden stakeholder rule.

**Conclusion in the tool.** RICE inputs on every task, a live score in the drawer, an editable ranking table, and the *Committed but not scored* rule that only fires on Next, since scoring the whole backlog is waste.

## 5. Separate important from urgent (Eisenhower matrix)

**Rationale.** Urgent work is pushed at a PM all day. Important work, discovery, strategy, stakeholder alignment, has no deadline and gets starved unless it is scheduled.

**Business base.** Covey, *The 7 Habits of Highly Effective People* (1989), Habit 3: the time-management matrix, attributed to Eisenhower. The advice is to spend most time in Quadrant II (important, not urgent).

**Hypothesis.** When more than about 40% of open work is both important and urgent, the PM is in fire-fighting mode and something upstream (planning horizon, stakeholder expectation) needs to change. The 40% threshold is a practitioner heuristic, not a measured constant; treat it as a starting point to tune.

**Experiment.** Track the quadrant distribution week over week on the Metrics view. A falling Quadrant I share with stable throughput is the signal that planning has improved.

**Conclusion in the tool.** Important and urgent flags on every task, colour stripe by quadrant on every card, the matrix view with one-click toggles, and the *Too much "Do first"* rule.

## 6. Say which outcome the task moves (outcomes over outputs)

**Rationale.** Product teams get measured on what shipped, not on what changed. A task that cannot state the metric or decision it moves is output for its own sake.

**Business base.** Seiden, *Outcomes Over Output* (2019); Perri, *Escaping the Build Trap* (2018); Cagan, *Inspired* (2nd ed., 2018) on empowered teams solving problems rather than delivering features. Doerr, *Measure What Matters* (2018) on linking work to objectives and key results.

**Hypothesis.** Requiring a "why" line and an objective link on every task makes the weekly review answer whether time was spent on what was declared to matter, and removes tasks that cannot be justified.

**Experiment.** Count tasks removed or merged at weekly review because no outcome could be written. A non-zero count every week means the rule is earning its place.

**Conclusion in the tool.** The *Why* field with a prompt, the objective picker fed from Settings, *No outcome stated* and *Not linked to an objective* rules, and the open-work-by-objective table on Metrics.

## 7. Done means the Definition of Done (Scrum)

**Rationale.** "Done" with open items is hidden work that returns as a surprise. A checklist agreed up front is the only honest definition.

**Business base.** Schwaber and Sutherland, *The Scrum Guide* (2020): the Definition of Done as a formal description of the state of the increment. Adopted as done-checklists in Jira, Asana and Linear.

**Hypothesis.** A per-task checklist, and a rule that flags Done tasks with unchecked items, reduces work that reopens after closure.

**Experiment.** Track how many Done items are moved back to an open column in the four weeks after adoption versus before.

**Conclusion in the tool.** A Definition of Done checklist on every task and the *Done with an open checklist item* rule.

## 8. Name the blocker, chase it daily (Kanban blocker management)

**Rationale.** A PM's blocked items almost always wait on a person. Unnamed blockers cannot be chased, escalated or clustered to find the systemic cause.

**Business base.** Anderson (2010) on blocker clustering and explicit policies; Kanban service delivery reviews as the escalation cadence. Daily stand-up practice in Scrum surfaces impediments daily.

**Hypothesis.** Requiring a named blocker at the moment of blocking, and listing blocked items on the Today view, shortens time in the Blocked column.

**Experiment.** Median days in Blocked, before and after.

**Conclusion in the tool.** Saving a task as Blocked requires a blocker; the *Waiting on others* panel on Today; *Blocked without a stated blocker* and *Blocked for too long* rules with an editable threshold (default three days, a practitioner heuristic).

## 9. Three most important tasks per day

**Rationale.** A day with seven priorities has none. Choosing a small set the night before or first thing removes decision cost during the day.

**Business base.** The Ivy Lee method (1918, documented by Lee for Bethlehem Steel; widely retold, including by Clear, *Atomic Habits*, 2018) sets six; the modern MIT variant used by Leo Babauta (*Zen Habits*) and by Allen's daily review settles on three. Three is a heuristic, not a measured optimum.

**Hypothesis.** A hard cap of three focus tasks, with the cap enforced in the interface, raises the completion rate of the chosen tasks.

**Experiment.** Share of focus tasks completed the day they were chosen, tracked over four weeks.

**Conclusion in the tool.** The Focus flag, the Today panel, a cap of three enforced when focusing from a list, and the *Do first, not yet in focus* prompt.

## 10. A weekly review that is a ritual, not a hope

**Rationale.** Any task system decays without a fixed moment to re-plan dates, prune the backlog, chase blockers and choose the next focus.

**Business base.** Allen (2001), the Weekly Review as the "critical success factor" of the system. Scrum's sprint review and retrospective serve the same cadence at team level.

**Hypothesis.** A checklist that must be completed before the review is recorded, plus an auto-generated status report, makes the review happen and makes stakeholder updates cheap enough to send every week.

**Experiment.** Weeks with a recorded review versus weeks without, against the health score trend. If the score does not move with review adherence, the rules are measuring the wrong things.

**Conclusion in the tool.** The nine-step ritual, the generated report, the review history table, and the *Weekly review overdue* rule.

## 11. Every task rolls up to a project (work breakdown structure)

**Rationale.** A PM runs several streams at once. Without a container, status reporting is a manual sort, and tasks that belong to nothing escape every review.

**Business base.** PMI, *A Guide to the Project Management Body of Knowledge* (PMBOK): the work breakdown structure, in which every work package rolls up to a deliverable. Jira's project → epic → issue hierarchy, Asana's project → section → task and Linear's project → issue all enforce the same containment.

**Hypothesis.** A required project on every task, a per-project progress and risk card, and a scope selector that filters every view make project-level status a by-product of daily task hygiene rather than a separate weekly effort.

**Experiment.** Time to produce a project status update before and after. The generated weekly report, scoped to a project, should replace the manual version.

**Conclusion in the tool.** Projects with code, sponsor, objective, target date and status; the Projects view; the scope selector in the top bar; and the *Not under a project* rule.

## 12. Categorise by kind of work, not by project

**Rationale.** A project tells you *what for*; a category tells you *what kind*. The second dimension answers a question the first cannot: is management and billing work crowding out discovery and delivery?

**Business base.** Activity-based time allocation in consulting utilisation reporting; Cagan (*Inspired*, 2018) on the split between discovery and delivery; the Kanban practice of work-item types with their own policies.

**Hypothesis.** Tracking open work by category across projects surfaces an unhealthy mix within two weekly reviews.

**Experiment.** The *Open work by category* table on Metrics, week over week. A rising share of Management and Stakeholder with flat Delivery is the signal to renegotiate meeting load.

**Conclusion in the tool.** A creatable category list, one category per task, category chips on every card, and the category breakdown on Metrics.

---

## How the health score is built

Score = 100 − Σ min(30, findings × weight), with weight 12 for critical, 5 for warning, 2 for info. The cap per rule stops one noisy rule (for example twenty untouched backlog items) from hiding a single critical finding. Weights are a design choice, not a measured result; if the score fails to correlate with how the week actually went, adjust them in the `RULES` weights in `pm-flightdeck/index.html`.

## What was deliberately left out

- **MoSCoW.** Overlaps with RICE and the Eisenhower matrix; a third prioritisation lens dilutes the other two.
- **Story points and velocity.** Team metrics. For an individual PM, throughput and cycle time in calendar days are simpler and harder to game.
- **Dependencies between tasks.** Replaced by a named blocker in free text. A dependency graph is worth adding only once blocked items regularly wait on other tasks rather than on people.
- **Time tracking.** Age in column already captures elapsed time; effort spent is rarely the constraint for a PM.
