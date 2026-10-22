# Agentic Engineering Periodic System: agent reference

Revision 2026.4.1. 40 live elements as a list: the column and the row are fields. Read the model and its reading rules first; they decide how a test is judged. A suggestion from this reference is never a permission (reading rule 5).

# How to read the table

The table is one drawing of a model. An element sits in a cell because of where
its test is checked and what it does, not because the grid needed filling.

## Rows: four loops, each with its own clock

| Row          | The loop          | Its clock        | What the row is about                                                        |
| ------------ | ----------------- | ---------------- | ---------------------------------------------------------------------------- |
| Task         | the run loop      | minutes to hours | one agent run: what it starts from and what it hands back                    |
| Change       | the change loop   | hours to days    | one change to the code, from plan to merge                                   |
| System       | the setup loop    | weeks            | what every run passes through: repository, harness, tools, pipeline, sandbox |
| Organisation | the decision loop | months           | what a team or company decides for everyone, and keeps up                    |

Each outer loop sets the rules the inner one runs under. What grows down the
rows is the loop's period, its leverage and the cost of a mistake. It is not the
person: a junior's week and a principal's week both touch all four loops. The
rows are never levels.

An element sits in the loop where its observable test is checked.

## Columns: one loop that repeats in every row

Fundamentals · Shaping · Context · Delegation · Verification · Diagnosis ·
Security · Adoption

Read left to right, every row is the same loop at a wider reach: understand the
code, decide what to build and how carefully, give the agent its context, hand
the work over, verify what came back, find why it failed, inside a security
boundary, then spread what works. Diagnosis feeds the next round of Shaping, so
the loop closes.

**AI products** is a separate block: software that contains a model is a
different system from software built with agents. It sits apart and is read on
its own, the way chemistry prints the f-block apart.

## Empty cells

A cell may stay empty. An **open** gap means nothing belongs at that reach. A
**predicted** gap means the model says an element should exist there; it is
shown with a working name and gets an ID only when it has an observable test and
evidence for it. A freed cell is never refilled just to keep the grid full.

## How an element earns a cell

1. **Distinct**: it says something no other element says.
2. **Observable**: a colleague could check its test on your repository or your
   work.
3. **Honest**: the test claims no more than the evidence supports.
4. **Placed**: its column names its function, and its row the loop where the
   test is checked.
5. **Lasting**: its name and test survive the next tool or model change. No
   tool, vendor or protocol names in element names.
6. **Activities**: they say what to do, when, and what makes it due.
7. **Sourced**: published sources fit the claim.

An idea that applies an existing element becomes an extension (`ae-030.01`) and
takes no cell of its own.

## What an element says

- **Problem**: the recurring situation it answers and how that goes wrong. The
  problem outlasts tools and models.
- **Seen on your own code when**: the observable test. It decides.
- **Applies when**: the condition under which the element applies. Without it,
  the element applies to every build that uses coding agents.
- **Adds work without helping when**: one intervention that is redundant once
  every clause of the test is met. It guides the choice of the next action. It
  never cancels a clause or makes a test not applicable.
- **Activities**: what to do, how often, and what makes it due at once.
- **Read with**: typed relations. _Complements_: each answers a different part
  of the situation. _Tell apart from_: easy to confuse, and the reason says how
  to tell them apart. _Prerequisite_: the first makes the second possible. Each
  relation names when it matters, why, and its limit.

## How to check it, clause by clause

Many tests join requirements that need different evidence. Those tests are split
into clauses, and each clause names where its evidence lives:

| Kind        | What counts                                                                                             |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| Repository  | an artifact or executable check in the repository or its history                                        |
| Run         | a record of a run or session the agent could not write; a summary written afterwards is a claim         |
| Environment | the deployed system, runner or managed settings; where something must be refused, a refused planted try |
| Person      | a person's act or understanding, recorded where the agent cannot write                                  |
| Over time   | repeated outcomes across runs, releases or a period                                                     |

Every clause is a verbatim part of the test. A split makes a test easier to
read, never easier to pass. A test is met only when every clause is.

Where a check can be pinned, it should be: a finding located by a live check
becomes an executable check that runs from then on. The activities name the
pinned form where one exists.

**Absent or can't tell.** Something is absent only when a repository artifact is
missing within the scope you inspected. Any other missing evidence is can't
tell.

## Reading the table for a decision

These rules apply whenever the table informs a recommendation, whether a person
or an agent reads it.

1. **An observation is not a diagnosis.** One sighting (a fallback page, a
   failed run, a missing file in one checkout) is recorded as what was seen. It
   becomes a finding about the build only with evidence of the kind the
   element's clauses name.
2. **Missing, hard to find, inadequate.** Before recommending that something be
   added, check whether it exists but is hard to find or use, or exists and does
   not do its job. The three lead to different work: create it, make it easier
   to reach, or improve it. Where it is unknown which holds, say so.
3. **Missing public evidence is not a missing practice.** What a repository, a
   website or another public view does not show may exist in a record outside
   the inspected scope; that is can't tell.
4. **The plan comes first.** Read the build's existing plan and its agreed
   priorities before reading the table. A suggestion from the table is ranked
   against them, and dropping an agreed priority needs a stated reason. More
   suggestions are not a better reading.
5. **A suggestion is not a permission.** Nothing in the table authorizes reading
   secrets, running a workload, changing a gate or widening rights. The task and
   the policy that governs it decide what may be done; a reader keeps a useful
   possible action apart from an action it is authorized to take.

## Elements

### ae-001 Read unfamiliar code (Rc)

- Column: Fundamentals. Row: Task.
- Problem: An agent is asked to change code nobody on the team can explain, so nobody can tell whether its change is right.
- Seen on your own code when: You can explain unfamiliar code, yours or the agent's, before you ask an agent to change it.
- How to check it, clause by clause:
  - "You can explain unfamiliar code, yours or the agent's, before you ask an agent to change it" (Person): Checked live: you explain the code in your own words before delegating. Its pinned form is characterization tests you read and accepted
- Adds work without helping when: Reading in full code the task does not touch: the test asks you to explain the code being changed, not the whole codebase.
- Activities:
  - practice: Every task that touches code you cannot yet explain. Due at once when: A change lands in an unfamiliar module, library or concept
  - practice: First two weeks an agent works on an existing codebase, read-only. Due at once when: The team brings an agent to an existing codebase
  - review: Every sprint. Due at once when: Nobody can explain a merged agent change
  - practice: Before an agent changes code you cannot yet explain: pin its current behaviour with characterization tests that you read and accept (the agent may write them); they keep the explanation as an executable record. Due at once when: A change lands in code nobody on the team can explain
- Related: ae-013.

### ae-010 Tests that pin behaviour (Tb)

- Column: Fundamentals. Row: Change.
- Problem: The agent changes behaviour by mistake and nothing fails, so the regression is found by users, or not at all.
- Seen on your own code when: When the agent changes behaviour by mistake, a test fails: you can show a regression the tests caught.
- Adds work without helping when: Pinning behaviour that is meant to change, or code that is about to be deleted: the test blocks the intended change and is rewritten soon after.
- Activities:
  - practice: Every bug fix and every behaviour change
  - setup: Once per repository, enforced in CI on every pull request. Due at once when: The test runner or its configuration changes
  - review: Nightly mutation run on changed code, where a tool exists. Due at once when: The gate or test configuration changes
  - practice: Every refactor or bug fix: the agent may not change the tests that pin behaviour; a test change in such a change is refused
  - review: Every test the agent wrote during the task: it counts once it fails on a planted defect
  - review: Every test the agent removes: a removal map points, for each assertion it carried, to the surviving test that still asserts it
  - review: Per test, kept current: flakiness measured; an agent's addition to the quarantine list waits for a named approver; a quarantined test still runs on a schedule outside the agent's loop and leaves quarantine only with a named cause. Due at once when: A test fails without a change
  - review: Every change that moves code or adds a directory tree, file type or pipeline stage: each guard and analysis states what it covers, and a planted violation in the new place turns it red; a run that skipped part of its input reports not verified, never clean. Due at once when: Code moves, or a new tree, file type or stage arrives
- Read with:
  - Complements ae-013.01 Rehearse the real path, when acceptance behavior includes an integration or real dependency transition. A local regression and a real-path rehearsal provide different observations. Limit: Do not claim all changes require the same broad end-to-end test.
- Related: ae-022.

### ae-019 Name the trade-off (Tr)

- Column: Fundamentals. Row: System.
- Problem: The agent adds a dependency, a data store or a remote call as a side effect of the task, and the team inherits its cost without anyone having chosen it.
- Seen on your own code when: Before code is written, the plan names the design choices the agent made (a new dependency, data store, remote call or boundary) and what each costs, and a person accepts them.
- How to check it, clause by clause:
  - "Before code is written, the plan names the design choices the agent made (a new dependency, data store, remote call or boundary)" (Repository): A plan dated before the first commit of the change, naming its design choices
  - "what each costs" (Repository): The cost of each named choice, in the same plan
  - "a person accepts them" (Person): An acceptance by a person, recorded where the agent cannot write, before the code
- Adds work without helping when: The plan adds no new dependency, data store, remote call or boundary: listing the costs of choices already made and in place adds reading without a decision.
- Activities:
  - practice: Every plan, before the agent writes code
  - decision: Before each consequential design choice. Due at once when: The agent adds a dependency, data store, remote call or boundary
  - review: Every pull request, decision list read before the diff
- Related: ae-012.

### ae-028 Design for change (Dc)

- Column: Fundamentals. Row: Organisation.
- Problem: Each agent change is acceptable on its own, but over months changes touch more modules and add more complexity, and the code gets harder to change for people and agents alike.
- Seen on your own code when: At fixed points the team measures a representative change: it still touches only the modules it should, and complexity and static-analysis findings per change, read beside its size, have not risen since the baseline.
- Adds work without helping when: Treating the fixed-point measurement as a gate on single changes: the per-pull-request check guards each change, the fixed points read the trend, and one noisy change is not a trend.
- Activities:
  - setup: Once per repository, before the agent's first task
  - practice: Every pull request: complexity, duplication and static-analysis findings in the touched files may not grow against main; growth needs a named approver. Due at once when: An agent change adds much more code than the fix needs
  - review: At day 90 and day 180, then at each release. Due at once when: A representative change touches more modules than at baseline
- Related: ae-019.

### ae-007 Problem before prompt (Pb)

- Column: Shaping. Row: Task.
- Problem: The agent starts on a vague request, builds something plausible, and nobody can say whether it is done, because done was never stated.
- Seen on your own code when: You can state the problem and the done criterion before the agent starts.
- Adds work without helping when: Writing a formal problem statement for a request whose done criterion is already plain in the request itself, such as a typo fix with the check that shows it.
- Activities:
  - practice: Every task, before the first prompt
  - decision: Before each run that will be left unattended. Due at once when: An agent is about to run without someone watching
- Read with:
  - Prerequisite for ae-012 Plan, then run, when a larger task needs an approved plan before execution. A plan needs a stated problem and completion condition to organize work. Limit: This procedure does not invent plan approval or redefine either test.
- Related: ae-004, ae-003.

### ae-016 Prototype to learn (Pt)

- Column: Shaping. Row: Change.
- Problem: Code written to answer a question slides into the product without the plan and review the real build would get, or the question it was meant to answer is never written down.
- Seen on your own code when: A prototype starts with a stated question, and its end is recorded: what it taught, and whether it was thrown away or rebuilt through the normal plan and review. The prototype's own branch never merges.
- Applies when: Applies when the work included a prototype: code written to answer a question and meant to be thrown away. A feature branch or an approximation alone is not a prototype.
- Adds work without helping when: The question can be answered by reading the documentation or by a small test: a prototype with its own branch and record is more than the question needs.
- Activities:
  - practice: Every prototype, before the first prompt
  - decision: When the prototype has answered its question. Due at once when: The question is answered or its time box runs out
- Related: ae-034.

### ae-025 One-way doors (Dw)

- Column: Shaping. Row: System.
- Problem: An agent takes a step that cannot be undone (deleting data or history, publishing, sharing data for training) without anyone having decided that it may.
- Seen on your own code when: The steps that cannot be undone (deleting data or version history, publishing, letting a provider train on your data) are listed for the repository; each names the role that approves it, and the approval lands in a record the agent cannot write.
- Adds work without helping when: Asking a person to approve a step that is not on the one-way list, that version control or a tested backup out of the run's reach fully reverses, and that no policy requires approval for: approvals on reversible steps teach people to approve without reading. Approvals a policy requires stay.
- Activities:
  - decision: Before each step that cannot be undone. Due at once when: Deleting data or version history, printing, publishing IDs, letting a provider train on data
  - setup: Once per repository, re-checked when the tool set changes. Due at once when: A new deploy command, CLI or MCP server is added
  - practice: Every decision that comes with options
  - setup: Once per repository: the forge refuses force pushes and branch or remote deletion for the agent's identity
  - setup: Once per data store the agent can reach: its backups sit where the agent's credentials cannot delete them, and a restore has been tested. Due at once when: The agent gets a credential for a new data store, or the store's backup setup changes

### ae-034 Decide what to build (Wb)

- Column: Shaping. Row: Organisation.
- Problem: Agents make building cheap, so features get built because they can be, without a user problem behind them or a date on which anyone checks whether they helped.
- Seen on your own code when: Each feature you build starts from a user problem and a stop criterion agreed before building, and you check the evidence on the agreed date after it ships.
- How to check it, clause by clause:
  - "Each feature you build starts from a user problem" (Repository): A written user problem for each feature, dated before the build
  - "a stop criterion agreed before building" (Repository, Person): The stop criterion, dated before building, and who agreed it
  - "you check the evidence on the agreed date after it ships" (Over time, Person): A dated check of the evidence on or after the agreed date
- Adds work without helping when: Fixes and upkeep that restore agreed behaviour: a stop criterion and a check date are for new features, not for keeping what exists working.
- Activities:
  - decision: Before each feature is approved
  - review: After each feature ships, on a date set when it was approved. Due at once when: The agreed stop evidence shows up
  - practice: At the start of each new feature area, and at least once a quarter: a day or more in the customer's setting

### ae-002 Instructions file (In)

- Column: Context. Row: Task.
- Problem: Every session starts by rediscovering how the project builds, tests and names things, and the agent repeats the same mistakes because nothing it reads at the start says otherwise.
- Seen on your own code when: The repository has a short, current instructions file that the agent actually follows.
- Adds work without helping when: Adding lines for what the agent already does right without them, or for rules a hook or check already enforces: they add length without changing behaviour, and a file that keeps growing stops being current.
- Activities:
  - setup: Once per repository, checked in CI on every change. Due at once when: A new coding tool or IDE plugin is adopted
  - practice: When the same written failure reason recurs in the task log (ae-014), never by habit
  - review: Every retrospective, reading the file's diff. Due at once when: A new model, tool version or framework release ships
  - setup: Once per instruction or context document: it names the paths it describes, and a check warns when those paths change and the document does not
  - review: At each model change: a few held-back tasks run with and without the file; a rule whose removal changes nothing is deleted, and one that makes results worse is removed at once. Due at once when: A new model or tool version ships, or the file passes its line ceiling
- Read with:
  - Tell apart from ae-011 Curated context, when a worker lacks or ignores needed information. Task-specific sources and persistent repository rules have different scopes. Limit: Do not add permanent prose for every one-off omission.
- Related: ae-029.

### ae-011 Curated context (Cu)

- Column: Context. Row: Change.
- Problem: The agent works from whatever it happens to find, misses a constraint written down elsewhere and rebuilds something that already exists.
- Seen on your own code when: Each task names the sources the agent needs (files, documents, constraints), and the session shows it read them and did not rebuild what already exists.
- Adds work without helping when: Listing sources for a task whose context is all in the files it changes, or adding loosely related documents: they fill the context without informing the work.
- Activities:
  - setup: Once per repository. Due at once when: A tool, MCP server or memory feature is added
  - practice: Every task: scope named in the plan, fresh session
  - review: Every reviewed agent change. Due at once when: The change missed a constraint or rebuilt something that exists
- Read with:
  - Tell apart from ae-002 Instructions file, when a worker lacks or ignores needed information. Task-specific sources and persistent repository rules have different scopes. Limit: Do not add permanent prose for every one-off omission.

### ae-011.01 Context budget (Cb)

- Column: Context. Row: Change.
- Extends: ae-011 Curated context.
- Problem: A long session degrades: the agent repeats itself, loses constraints it was given, and the work after that point quietly gets worse, while what it calls done may rest on steps nobody checked.
- Seen on your own code when: Long work is split into fresh sessions at planned points, each with a written handover a person has read; a session that repeats itself or drops a stated constraint ends early, with the same handover.
- How to check it, clause by clause:
  - "Long work is split into fresh sessions at planned points" (Run): Session records showing the planned split points
  - "each with a written handover a person has read" (Repository, Person): The handover notes kept with the change, and who read them
  - "a session that repeats itself or drops a stated constraint ends early, with the same handover" (Run): A session record ending early on repetition or a dropped constraint
- Adds work without helping when: Splitting short work that fits comfortably in one session and shows none of the signs: a planned handover then costs more than it saves.
- Activities:
  - setup: Once per repository: the agent drafts the handover note, and a person reads it before the next session starts from it; for an unattended run the note reaches the next run only through a reviewed change
  - practice: Every long task: handover, then a fresh session. Due at once when: The agent repeats itself, drops a stated constraint, or the session was compacted
  - practice: Every handover: the files changed since the task began, listed from git, never from the agent's summary
  - practice: Every handover note stays with the change it belongs to, so the next session and a later audit read the same note
  - practice: Every handover of unfinished or unverified work: the next session first checks the inherited code against the request and its evidence, then repairs it or restarts from the base; a fresh session on an unchecked tree is not a restart. Due at once when: Work is handed over before it is verified, or a result is claimed late in a long session
- Read with:
  - Tell apart from ae-023 Stop and roll back, when long work requires context renewal and execution limits. Session handover and enforced run termination solve different problems. Limit: Restarting a session does not establish cancellation or credential revocation.
- Related: ae-012.

### ae-020 Skills and tools (Sk)

- Column: Context. Row: System.
- Problem: The model, tools and skills behind the agent change under the team without notice, and skills pile up whether or not they help, so results drift and nobody can say why.
- Seen on your own code when: The model, the coding tool and the skills, plugins and tool servers the agent uses are pinned to a version and reviewed like code: delegated work names its model (no automatic choice or fallback), and a skill stays only while runs with and without it show that it helps.
- How to check it, clause by clause:
  - "The model, the coding tool and the skills, plugins and tool servers the agent uses are pinned to a version" (Repository, Environment): Lockfiles and configuration in the repository, and the versions actually installed on each machine or runner
  - "reviewed like code" (Repository): Changes to those pins go through the same review as code
  - "delegated work names its model (no automatic choice or fallback)" (Repository, Run): Task records or runner configuration naming the model, and run records showing no automatic choice or fallback
  - "a skill stays only while runs with and without it show that it helps" (Over time): Repeated comparison runs with and without each skill, kept current as skills and models change
- Adds work without helping when: Comparing runs with and without a skill nobody relies on: removing it is cheaper than measuring it.
- Activities:
  - setup: Once per tool. Due at once when: A new skill, tool server or plugin is proposed
  - practice: Every upgrade of a skill, server or plugin. Due at once when: A dependency update changes a skill shipped inside a package
  - review: Every quarter: pinned versions and the end dates of the pinned model and tools. Due at once when: A new model ships, or a tool gets new access
  - review: Each check that must run every time: in a hook or the pipeline, not only in a skill the agent may or may not pick
  - review: Every new or changed skill: the same held-back tasks run with and without it, with the whole skill library installed; a skill that does not help, or takes its neighbours' tasks, is not installed, and one that stops helping is removed
- Related: ae-029.

### ae-020.01 Tool design (Td)

- Column: Context. Row: System.
- Extends: ae-020 Skills and tools.
- Problem: An agent calls a tool wrongly or gives up after an error, because the description, schema or error message does not tell it what to do next.
- Seen on your own code when: A tool you build for agents has a clear description and schema, and its errors tell the agent what to do next: a session shows it recovering from one.
- Applies when: Applies when the work built a tool whose intended user is an agent: a tool server, an agent-facing command or a context generator made for agents. A command line with machine-readable output counts only when it was built for agents to call.
- Adds work without helping when: Polishing the description and errors of a tool the agent already calls correctly and recovers from: the session that shows the recovery is the evidence, more wording is not.
- Activities:
  - setup: Once per tool: description, schema and error messages written for the agent
  - practice: Every new tool: watch the agent use it on real tasks, then change the tool before the prompt. Due at once when: The agent calls the tool wrongly or gives up after an error

### ae-029 Harness as code (Hc)

- Column: Context. Row: Organisation.
- Problem: Each project and person runs a different, unreviewed variant of the agent setup, so the checks and approvals a merge passes depend on who made it.
- Seen on your own code when: The team's shared harness (instructions, skills, hooks) has a named owner and changes only through reviewed changes, every project goes through the same checks and approvals to merge, and what must hold sits in hooks or managed settings that no project or personal file can loosen.
- How to check it, clause by clause:
  - "The team's shared harness (instructions, skills, hooks) has a named owner" (Repository): The harness in its own place with a named owner
  - "changes only through reviewed changes" (Repository, Person): Review records by a person on every change to the harness
  - "every project goes through the same checks and approvals to merge" (Environment): The merge rules of every project, compared
  - "what must hold sits in hooks or managed settings that no project or personal file can loosen" (Environment): Managed settings or hooks above the project, and a project or personal file that tries to loosen them without effect
- Adds work without helping when: Building shared ownership and managed settings for a setup one person uses in one project: start when a second team or coding tool adopts it.
- Activities:
  - setup: Once per organisation, then kept by a named owner. Due at once when: A second team or another coding tool adopts the setup
  - practice: Every change to the shared harness, as a reviewed diff
  - decision: Before the first shared rollout. Due at once when: A team, coding tool or unattended run is added
  - review: At every framework release and model change. Due at once when: A new model or a major framework version ships
  - review: At each model change or shared-harness release: the same held-back tasks run under each project's setup; the results agree within the noise, or the difference is traced to a named override
  - review: Each shared-harness release: a planted loosening in a project file and in a personal file changes nothing
- Related: ae-002, ae-020.

### ae-003 Small slices (Sl)

- Column: Delegation. Row: Task.
- Problem: A task comes back as a change too large for one person to review, so it is merged on trust or not really reviewed.
- Seen on your own code when: Each task you hand over fits into one change a person can review.
- Adds work without helping when: Splitting a mechanical change that a check verifies completely (a rename, a formatter run, a regenerated file), where its size does not make review harder.
- Activities:
  - practice: Every task handed to an agent: one thin vertical slice, one pull request. Due at once when: A change grows past what one person can review or explain: split it
  - setup: Once per repository: an issue template or planning skill that cuts thin vertical slices
  - review: At each team measurement: change size per delivered slice against the dated baseline. Due at once when: Agent pull requests run larger than the team's usual size
- Read with:
  - Tell apart from ae-021 Parallel agents, when a change is being split and concurrent execution is considered. Reviewable size does not establish independent parallel parts. Limit: Do not add concurrency when the shared assumptions cannot be separated.
- Related: ae-013.

### ae-012 Plan, then run (Pl)

- Column: Delegation. Row: Change.
- Problem: Larger work starts without an agreed plan, so the agent decides the shape of the solution alone and the person finds out at review, when changing course is expensive.
- Seen on your own code when: Larger work starts from a plan you approved, and the agent works through it.
- Adds work without helping when: Small, reversible changes within one session whose done criterion already fixes the approach: a plan there only restates the task.
- Activities:
  - practice: Every larger change: a person approves the plan, with a red acceptance test. Due at once when: Work spans sessions, is handed off, or carries high stakes
  - setup: Once per coding tool: during planning, a file write through a shell command is refused by a deny rule or the sandbox; the planning mode never counts as the plan approval; no timer approves a plan. Due at once when: The coding tool or its plan mode changes version
  - practice: Every commit of planned work: plan and built code reconciled. Due at once when: The implementation departs from the approved plan
  - practice: Every plan before approval: each requirement names where it comes from (the request, a record in the workspace, or an assumption), and the approver reads the assumptions. Due at once when: The request leaves requirements open
- Read with:
  - Needs first ae-007 Problem before prompt, when a larger task needs an approved plan before execution. A plan needs a stated problem and completion condition to organize work. Limit: This procedure does not invent plan approval or redefine either test.
- Related: ae-013, ae-019.

### ae-021 Parallel agents (Pa)

- Column: Delegation. Row: System.
- Problem: Several agents work at once on overlapping code, and their changes collide at merge, or pass one by one and fail together.
- Seen on your own code when: Before agents work in parallel, the plan names what keeps their work apart: separate files, separate layers behind a stable interface, or a set order in which the changes land. Where nothing does, the work runs in sequence, and changes that run together pass the checks together.
- Adds work without helping when: The work fits in sequence within the time available: running it in parallel then adds coordination without saving time.
- Activities:
  - setup: Once per repository: one worktree and branch per agent, each in its own sandbox
  - practice: Every merge: checks run on a branch up to date with main or in a merge queue. Due at once when: Several agents reach the release path at once: queue it
  - decision: Once per team: how many agents one person runs at a time. Due at once when: The ship queue backs up or reviews start slipping
  - review: Every new parallel setup: measured against one agent on the same held-back tasks (accepted runs, tokens, time, integration rework)
- Read with:
  - Tell apart from ae-003 Small slices, when a change is being split and concurrent execution is considered. Reviewable size does not establish independent parallel parts. Limit: Do not add concurrency when the shared assumptions cannot be separated.
- Related: ae-003, ae-022.

### ae-030 Agentic lifecycle (Lc)

- Column: Delegation. Row: Organisation.
- Problem: Agents spread into the stages of the work one tool at a time, and nobody can say which decisions still belong to named people.
- Seen on your own code when: The team has a written map of its stages that names, for each, whether agents work there and which decisions stay with named people, and the agent cannot record those decisions itself.
- Adds work without helping when: Redrawing the map for a new tool inside a stage already mapped: the map changes when agents enter a stage or a decision moves, not when a tool changes.
- Activities:
  - decision: Once per team: which stages agents run and which decisions stay with named people. Due at once when: A new model, coding tool or task class is adopted
  - review: Every release and model change: a written pruning pass over the team's agent rules
  - practice: Every incident review: did agent code or change volume outrun review and testing
  - review: Each audit cycle: the decision log is read for decisions recorded on a person's behalf
  - decision: Once per team: who follows releases of models, coding tools and security advisories, and starts the reviews whose trigger they are. Due at once when: The person who follows them leaves or changes role
- Related: ae-031.

### ae-030.01 Govern who builds (Gw)

- Column: Delegation. Row: Organisation.
- Extends: ae-030 Agentic lifecycle.
- Problem: A person who is not an engineer changes code through an agent, and the change merges without the engineer who owns that code having seen it.
- Seen on your own code when: A non-engineer's account cannot push to a protected branch, and its agent's pull request cannot merge without the engineering owner of every path it touches; a test account that tries both is refused both times.
- Applies when: Applies when people who are not engineers can change the repository through an agent, or are about to. Not applicable only when every contributor is known to be an engineer; when the contributors are unknown, it is can't tell.
- Adds work without helping when: Adding reviewers whom no policy requires and who do not know the touched code: the code owners' review is what the test asks for. Reviewers a policy requires stay.
- Activities:
  - decision: Before anyone outside engineering launches an agent on product code. Due at once when: A new role or team asks to build with agents
  - setup: Once per repository, kept current as roles change
  - review: Once at setup, then whenever permissions or roles change: the planted push and the planted pull request again. Due at once when: Branch protection, code owners or the role list changes

### ae-004 Evidence before done (Ev)

- Column: Verification. Row: Task.
- Problem: An agent declares success, but its claim cannot be connected to the acceptance criteria and the output of a relevant check.
- Seen on your own code when: Every "done" comes with evidence tied to the acceptance criteria: the command that ran and its output; a check that could not run or errored is reported as "not verified", never as done.
- How to check it, clause by clause:
  - "Every "done" comes with evidence tied to the acceptance criteria" (Run): The run's own record of each done, against criteria written before the run; a summary written afterwards is a claim
  - "the command that ran and its output" (Run): The command log or CI output itself, kept where the agent cannot write
  - "a check that could not run or errored is reported as "not verified", never as done" (Run): Run records in which a failed or skipped check appears as not verified
- Adds work without helping when: Rerunning a deterministic check whose command and output are already tied to each criterion, with nothing changed in between: the rerun adds reading, not certainty. Where results vary from run to run, repeated runs are evidence.
- Activities:
  - practice: Every task: the command, its output and the commit or run it belongs to. Due at once when: An agent says "done"
  - setup: Once per repository: one gate command and a task log the agent cannot write, with three outcomes: passed, failed, not verified
  - review: At each team measurement point: re-run the cited evidence of three logged tasks at random. Due at once when: Before the team widens the tasks agents may run without a person watching each run
- Read with:
  - Complements ae-022 Independent gates, when acceptance depends on a check outside the producer claim. Evidence identity and acceptance authority are distinct questions. Limit: Evidence presence alone does not establish independent control.
  - Tell apart from ae-005 Trace the run, when an agent reported done and the result fails. Evidence before done asks whether the done claim carried evidence tied to the acceptance criteria; Trace the run asks where the run went wrong, checked against a record the agent could not write. Limit: Both can be missing at once; evidence for the claim does not locate the failure, and a located failure does not repair the claim.
- Related: ae-013.

### ae-013 Review the diff (Rd)

- Column: Verification. Row: Change.
- Problem: The review reads the agent's description of the change instead of the change, so whatever the description leaves out is accepted unseen.
- Seen on your own code when: The review reads the change itself. The agent's description of it is a claim.
- Adds work without helping when: Reading in full a change that the team's decision (ae-031) leaves to a check: reading everything everywhere thins the attention the decision reserves for the code that needs it.
- Activities:
  - practice: Every agent pull request in a tier where a person must read (ae-031): the person who launched the agent reads the diff and checks behaviour first, then a person other than the launcher approves; an agent's approval never counts. Due at once when: A machine review or agent summary comes with the change
  - setup: Once per repository: approvals bind to the tested diff and a later push dismisses them
  - setup: Once per repository: an agent pull request approved only by the person who launched it cannot merge; a planted one proves it
- Read with:
  - Tell apart from ae-022 Independent gates, when a change has been reviewed carefully and is about to merge. Review the diff is about what the review reads; Independent gates is about who gives the merge verdict and whether the agent can change, skip or pass it. Limit: A careful review does not make the acceptance independent, and an independent gate does not read the change.
- Related: ae-031, ae-022.

### ae-013.01 Rehearse the real path (Rh)

- Column: Verification. Row: Change.
- Extends: ae-013 Review the diff.
- Problem: The tests pass, but the change breaks a real user journey through a dependency, a transition or an interruption that no test exercises.
- Seen on your own code when: Before a change that alters a user journey is accepted, the journey, named in advance, runs against a deployment of that change and its real dependencies, crossing the transitions named with it and one plausible interruption or failure. The record names the environment and deployed revision, the steps, what was observed and what was not verified. Test data stays apart from real user data.
- Adds work without helping when: Rehearsing every interruption one can imagine: one plausible interruption or failure on the named journey is the bar, and the rest belongs in tests once a rehearsal finds something.
- Activities:
  - setup: Once per repository: a way to deploy a change with its real dependencies (a preview or a release candidate), and a test namespace kept apart from real user data. Due at once when: A new backing service, device class or deployment target is added
  - practice: Every change that alters a user journey: the named journey runs on a deployment of that change, crossing its named transitions and one interruption, and the record is kept with the change. Due at once when: A change touches storage, a time boundary, a network path or a device-specific feature
  - review: After every defect that reached a preview or users while the suite was green: the journey list gains the path it took. Due at once when: A release defect escapes the test suite
  - practice: Every named journey that hands the user to a third-party service: the rehearsal follows it to its last effect on that user (a list subscription, a message, a charge, a record kept), observed in the third party's own record, and the record names the effects not observed. Due at once when: A journey ends in or passes through a third-party service
- Read with:
  - Complements ae-010 Tests that pin behaviour, when acceptance behavior includes an integration or real dependency transition. A local regression and a real-path rehearsal provide different observations. Limit: Do not claim all changes require the same broad end-to-end test.
- Related: ae-004, ae-010.

### ae-022 Independent gates (Ga)

- Column: Verification. Row: System.
- Problem: The agent whose work is judged can also change, skip or pass the check that judges it, so a green result says nothing about the work.
- Seen on your own code when: The merge verdict comes from the pipeline: it runs the check on the committed tree in a clean checkout and posts the result under its own identity; the agent can neither change, skip nor pass that check on its own, a required check that was skipped or did not finish blocks the merge, and every change to the check is reviewed by a person.
- How to check it, clause by clause:
  - "The merge verdict comes from the pipeline" (Environment): The branch rule or merge setting that requires the pipeline's result
  - "it runs the check on the committed tree in a clean checkout" (Repository, Run): The pipeline definition (in the repository, or in the CI system where it lives there) and a run of it
  - "posts the result under its own identity" (Run): A posted result whose author is the pipeline, not a person or the agent
  - "the agent can neither change, skip nor pass that check on its own" (Environment): A planted attempt by the agent's identity to change, skip or pass the check, refused
  - "a required check that was skipped or did not finish blocks the merge" (Environment): A planted skipped run of a required check (a fork, a bot or a run condition), refused at merge
  - "every change to the check is reviewed by a person" (Person, Repository): Review records by a person on every change to the pipeline or its checks
- Adds work without helping when: Adding a second pipeline or verifier when the existing check already runs on the committed tree under its own identity and the agent cannot change it: duplication adds cost, not independence.
- Activities:
  - setup: Once per repository: gate files protected, required check accepted only from CI
  - practice: Every change: the gate runs in CI on the committed tree and decides the merge
  - review: Once a year: plant failures, a skipped required check and a verdict tamper in a throwaway branch. Due at once when: The pipeline, a gate script or the verifier changes
  - setup: Every pipeline file the agent adds or edits: an automatic injection check before its owner reviews it; a file found vulnerable is removed from every branch
  - setup: Once per repository: every required check is reported by a job that always runs and fails unless the check it stands for finished. Due at once when: A required check gets a path, branch, actor or other run condition, or a new check becomes required
  - setup: Every gate where a model gives the verdict, including a model that reviews permission requests: denials are counted per task, and after a denial the next attempt goes to a person, not to another try. Due at once when: A model starts to decide whether the agent's work or request goes through
- Read with:
  - Complements ae-004 Evidence before done, when acceptance depends on a check outside the producer claim. Evidence identity and acceptance authority are distinct questions. Limit: Evidence presence alone does not establish independent control.
  - Tell apart from ae-013 Review the diff, when a change has been reviewed carefully and is about to merge. Review the diff is about what the review reads; Independent gates is about who gives the merge verdict and whether the agent can change, skip or pass it. Limit: A careful review does not make the acceptance independent, and an independent gate does not read the change.

### ae-031 Decide what people read (Hr)

- Column: Verification. Row: Organisation.
- Problem: Nobody has decided which code a person must read, so review is either everything, and gets skimmed, or whatever the reviewer has time for.
- Seen on your own code when: The team has decided which code a person must read and which a check may accept.
- Adds work without helping when: Reopening the decision for every change: it is revisited when a new system, path or task class goes to agents, or when unreviewed merges rise without a decision.
- Activities:
  - decision: Once per team: per path or tier, whether a person must read or a check may accept. Due at once when: A new system, path or task class is handed to agents
  - setup: Once per repository: the tiers encoded in code owners and branch protection
  - review: Each audit cycle: seed known faults and count what each human step catches. Due at once when: Merges without a person's review rise and nobody decided it
  - decision: Each path or change class a check may accept without a person: a named owner holds its risk; gate files, pipeline files, tests and migrations are never in it; its rollback is drilled; a post-deploy alert reaches the owner
- Related: ae-022.

### ae-005 Trace the run (Tx)

- Column: Diagnosis. Row: Task.
- Problem: A run went wrong, and the only account of what happened is the agent's own, which may be the very thing that is wrong.
- Seen on your own code when: When a run goes wrong, you find the step where it went wrong and check that step against a record the agent cannot write: the command log, CI or the repository.
- How to check it, clause by clause:
  - "When a run goes wrong, you find the step where it went wrong" (Person, Run): A diagnosis that names the failing step of a specific run
  - "check that step against a record the agent cannot write: the command log, CI or the repository" (Run, Repository): The command log, CI result or repository state for that step, compared with what the agent said
- Adds work without helping when: Reconstructing the whole run when a focused test reproduces a deterministic failure: check the failing step against the test output or the CI record, fix it and add the regression; the rest of the run adds nothing.
- Activities:
  - practice: Every failed or surprising run, before you change prompt, model or code. Due at once when: The agent reports success and the result disagrees
  - setup: Once per team: a run record the agent cannot write, kept for the whole measurement period. Due at once when: A new agent tool or cloud runner with its own retention default is adopted
  - review: Every week: the corrections you made more than once
- Read with:
  - Complements ae-014 Name the failure, when a failed step can be located but its cause remains uncertain. A specific record supports testing one causal hypothesis. Limit: An obvious deterministic defect may need only a focused fix and regression.
  - Tell apart from ae-004 Evidence before done, when an agent reported done and the result fails. Evidence before done asks whether the done claim carried evidence tied to the acceptance criteria; Trace the run asks where the run went wrong, checked against a record the agent could not write. Limit: Both can be missing at once; evidence for the claim does not locate the failure, and a located failure does not repair the claim.
- Related: ae-014.

### ae-014 Name the failure (Fc)

- Column: Diagnosis. Row: Change.
- Problem: A failed run is fixed by changing several things at once (prompt, rules, model), so nobody learns which change mattered and the failure comes back.
- Seen on your own code when: When the agent fails, you name the likely cause (missing context, unclear task, wrong tool, model limit) and test that guess by changing one thing.
- Adds work without helping when: Varying more once a one-change test has confirmed the named cause: further variations add runs, not knowledge.
- Activities:
  - practice: Every failed agent run, before you touch prompt, model or code. Due at once when: A fix is proposed before the failure has a name
  - practice: Every fix: change one thing, rerun the same tasks several times. Due at once when: A prompt, rule, model or harness change is proposed as the fix
  - review: Per batch of about 50 to 100 collected failures: each carries one written reason; the reasons are grouped and counted, and a rule promoted from them names its category and count. Due at once when: The same failure mode shows up across several sessions
- Read with:
  - Complements ae-005 Trace the run, when a failed step can be located but its cause remains uncertain. A specific record supports testing one causal hypothesis. Limit: An obvious deterministic defect may need only a focused fix and regression.
- Related: ae-002.

### ae-023 Stop and roll back (Sb)

- Column: Diagnosis. Row: System.
- Problem: An unattended run goes on past the point where it should have stopped (looping, spending, touching more than intended), and nobody can stop it or say what it changed.
- Seen on your own code when: Every unattended run has a cap set outside the agent (turns, time or spend) and a stop it cannot talk past; a run that reaches the cap ends as not verified; logs outside its write access show what it changed, its work sits in a branch you can drop, and a dated drill shows the stop ends every process the run started and revokes every credential the run was issued or obtained.
- How to check it, clause by clause:
  - "Every unattended run has a cap set outside the agent (turns, time or spend)" (Environment): Runner or managed configuration the agent cannot reach, with the cap set
  - "a stop it cannot talk past" (Environment): A stop path enforced outside the agent's process and permissions
  - "a run that reaches the cap ends as not verified" (Run): The record of a capped run, kept where the agent cannot write, ending as not verified
  - "logs outside its write access show what it changed" (Run): Runner, pipeline or audit logs the agent cannot write
  - "its work sits in a branch you can drop" (Repository): A branch or worktree per run, separate from the protected branch
  - "a dated drill shows the stop ends every process the run started and revokes every credential the run was issued or obtained" (Person, Environment): A dated drill record: a person stops a run, confirms its processes ended and every credential it was issued or obtained no longer works
- Adds work without helping when: Drilling the stop more often than the schedule the team set while the stop path, the runner and the credential setup are unchanged: an extra drill repeats the last one. A change to any of them makes a new drill due at once.
- Activities:
  - decision: Before each unattended or goal run: who or what stops it, on which signal. Due at once when: A new unattended run, loop or automation is set up
  - setup: Once per team: a hard stop plus a branch or copy the run's work can be dropped from. Due at once when: A new runner, agent product or credential path is adopted
  - review: A dated drill before the first unattended run, then on a schedule the team sets. Due at once when: The stop path, the runner or the credential setup changes
- Read with:
  - Complements ae-024 Sandbox and rights, when an unattended run has effective action and duration boundaries. The run needs appropriate rights before its stop limit is reached. Limit: Neither a time cap nor a sandbox substitutes for the other test.
  - Tell apart from ae-011.01 Context budget, when long work requires context renewal and execution limits. Session handover and enforced run termination solve different problems. Limit: Restarting a session does not establish cancellation or credential revocation.
- Related: ae-025.

### ae-032 Learn from incidents (Li)

- Column: Diagnosis. Row: Organisation.
- Problem: Agent incidents are fixed and forgotten, so the same class comes back and nobody knows whether the last corrective action did anything.
- Seen on your own code when: Every agent incident ends in a recorded corrective action, and you check later whether it worked.
- Adds work without helping when: A full review of a near miss that an existing guard caught as designed: record it, and review in depth when a guard did not hold or the class recurs.
- Activities:
  - practice: Every agent incident or near miss, in its review. Due at once when: An agent incident or near miss is reported
  - decision: Each rule added from an incident: named approver, owner, dated promotion. Due at once when: An incident review proposes a new rule or guard
  - review: At every release and every model change. Due at once when: The same incident class recurs after its corrective action
- Related: ae-029.

### ae-006 Secrets stay out (Sx)

- Column: Security. Row: Task.
- Problem: Credentials sit where the agent can read, print, commit or send them, so one wrong step or one injected instruction leaks them.
- Seen on your own code when: Secret files are denied to the agent, credentials stay outside its environment, and a planted fake credential is blocked at the push and in outgoing requests.
- How to check it, clause by clause:
  - "Secret files are denied to the agent" (Repository, Environment): The deny rules in the project's agent settings, and the effective settings on the machine or runner
  - "credentials stay outside its environment" (Environment): The agent's environment, inspected for credentials
  - "a planted fake credential is blocked at the push and in outgoing requests" (Environment, Run): A planted fake credential and the run records of both blocks; pinned as a gate check
- Adds work without helping when: Adding a second scanner that watches the same paths as one that already blocks the planted fake credential at the push and in outgoing requests: it repeats a check without covering a new path. Checking this never means reading real secrets.
- Activities:
  - setup: Once per machine and repository, before the first agent run. Due at once when: A new agent tool, MCP server or cloud agent environment is added
  - practice: Every agent push: scanned for secrets; a hit blocks the push until a person clears it
  - review: At each gate re-test, a planted fake credential must be blocked. Due at once when: The agent's environment, tools or scanner configuration changes
- Read with:
  - Tell apart from ae-024 Sandbox and rights, when the observed risk involves credentials or excessive capability. Credential boundaries and effective rights address different mechanisms. Limit: One successful refusal cannot establish all secrets or rights clauses.
- Related: ae-024.

### ae-015 Output is untrusted (Ui)

- Column: Security. Row: Change.
- Problem: Model output reaches a shell, a query or a page as raw text, so whatever the model was led to write runs with the application's rights.
- Seen on your own code when: Model output reaches a shell, a query or a web page only through that sink's safe interface (parameters, escaping, an allow-list), never as raw text.
- Applies when: Applies when model output reaches a shell, a query or a web page, at run time or in a build script. Code an agent wrote is not model output in this sense.
- Adds work without helping when: Treating an output filter as the fix: where the sink's safe interface is in use, a filter on top adds little; where it is missing, a filter does not replace it.
- Activities:
  - setup: Once per application, kept current with its architecture. Due at once when: Model output starts to feed a new consumer: shell, query, page or URL fetch
  - practice: Every change that passes model output to a shell, a query or a page. Due at once when: An agent proposes a fix that filters the output instead of securing the sink
- Read with:
  - Tell apart from ae-033 Threat model, when untrusted content can influence a privileged action. Safe handling at a sink and mapping content-to-capability paths have different scopes. Limit: Preserve ae-015 applicability; ordinary generated source code is not automatically sink-bound output.

### ae-015.01 Authorization tests (Az)

- Column: Security. Row: Change.
- Extends: ae-015 Output is untrusted.
- Problem: An endpoint returns another user's object because an ownership check is missing or was removed, and no test notices.
- Seen on your own code when: Every endpoint that takes an object ID has a test in which one user asks for another user's object and is refused; a planted removal of an ownership check, or of a row policy in the database, turns a named test red.
- Adds work without helping when: Writing a second refusal test for the same endpoint, the same role and the same ownership path: a test for another path or role is not a duplicate.
- Activities:
  - setup: Once per application: one refusal test per endpoint that takes an object ID
  - practice: Every agent change that touches authorization, or a migration that changes row policies: reviewed like a deleted test. Due at once when: A permission error is fixed by loosening a check or a policy
  - review: At each release: a planted removal of an ownership check turns a named test red
- Related: ae-010.

### ae-024 Sandbox and rights (Sp)

- Column: Security. Row: System.
- Problem: The agent runs with the user's full rights, so a mistaken or injected action can reach anything the user can.
- Seen on your own code when: The agent runs in a sandbox with only the rights its task needs, set in managed settings a project file cannot loosen: a planted denied action is refused, and every agent tool installed on the machine, used or not, refuses to start in its bypass mode.
- How to check it, clause by clause:
  - "The agent runs in a sandbox with only the rights its task needs" (Environment): The sandbox and permission configuration of the runner or machine the agent used
  - "set in managed settings a project file cannot loosen" (Environment): Managed settings above the project level, and a project file that tries to loosen them without effect
  - "a planted denied action is refused" (Environment, Run): A planted denied action and the run record of its refusal
  - "every agent tool installed on the machine, used or not, refuses to start in its bypass mode" (Environment): An inventory of installed agent tools and a start attempt in bypass mode for each, refused
- Adds work without helping when: Denying rights the task needs in order to look strict: the agent then asks for broad exceptions and people route around the sandbox. Least privilege means the rights the task needs, not fewer.
- Activities:
  - setup: Once per machine and repository, enforced through managed settings. Due at once when: An agent tool, subagent or tool server is installed or updated
  - practice: Every permission or policy change: decided on what it newly allows, compared with the current policy. Due at once when: The agent asks for more access
  - review: Every quarter, and on every model or agent version change. Due at once when: A new model version or a sandbox security advisory ships
  - review: Every gate run: a test identity attempts one planted denied action, and the gate fails if it is allowed. Due at once when: The sandbox, managed settings or an agent tool changes
- Read with:
  - Tell apart from ae-006 Secrets stay out, when the observed risk involves credentials or excessive capability. Credential boundaries and effective rights address different mechanisms. Limit: One successful refusal cannot establish all secrets or rights clauses.
  - Complements ae-023 Stop and roll back, when an unattended run has effective action and duration boundaries. The run needs appropriate rights before its stop limit is reached. Limit: Neither a time cap nor a sandbox substitutes for the other test.
- Related: ae-023.

### ae-033 Threat model (Tm)

- Column: Security. Row: Organisation.
- Problem: Untrusted content (issues, web pages, documents, tool output) reaches the agents, and nobody knows what an instruction hidden in it could make them touch.
- Seen on your own code when: The team keeps a current map of where untrusted content reaches its agents and what it could touch, and a planted instruction in that content reaches nothing the map rules out.
- Adds work without helping when: Mapping sources that never reach an agent: the map covers where untrusted content meets agents, and a general security inventory belongs elsewhere.
- Activities:
  - setup: Once per agent system, drawn with the developers who build it
  - review: Whenever the agent's capabilities change. Due at once when: A new tool, MCP server, skill, model version or data source is added
  - practice: Every listed threat, until a control exists and a test shows it holds
- Read with:
  - Tell apart from ae-015 Output is untrusted, when untrusted content can influence a privileged action. Safe handling at a sink and mapping content-to-capability paths have different scopes. Limit: Preserve ae-015 applicability; ordinary generated source code is not automatically sink-bound output.
- Related: ae-024.

### ae-037 Mark agent work (Mk)

- Column: Adoption. Row: Change.
- Problem: Nobody can tell which changes an agent made, so incidents, reviews and measurements cannot separate agent work from people's work.
- Seen on your own code when: Every change made through the team's agent runner carries its one marker, written by the tooling; the pipeline refuses a commit from an agent's identity without it, and every agent run in the log links to the changes it made.
- How to check it, clause by clause:
  - "Every change made through the team's agent runner carries its one marker, written by the tooling" (Repository): The marker in the history of each agent change, written by the harness configuration
  - "the pipeline refuses a commit from an agent's identity without it" (Repository, Environment): The pipeline or branch rule (usually defined in the repository) and a planted unmarked commit it refused
  - "every agent run in the log links to the changes it made" (Run, Over time): The run log outside the repository, cross-checked against the changes release after release
- Adds work without helping when: Adding markers by hand or after the fact: a marker the tooling did not write is a claim, so it adds work without becoming evidence.
- Activities:
  - decision: Once per team: one marker convention, for example a trailer. Due at once when: A target repository has its own policy: read it at its current revision
  - setup: Once per repository: the harness or the pipeline writes the marker, and the pipeline refuses an agent commit without it
  - review: Every release: each agent run in the log links to the changes it produced, and each of those changes carries the marker. Due at once when: A run without linked changes, or a marked change without its run
  - practice: Every marked change: it takes the review path the team set for agent work (ae-031); the marker routes the read, it does not replace it
- Related: ae-022, ae-031.

### ae-017 Hand it over (Ho)

- Column: Adoption. Row: System.
- Problem: The agent setup works only for the person who built it: when they are away nobody can run it, or a colleague runs it and gets different results without noticing.
- Seen on your own code when: A colleague runs your agent setup without you, from what is written down, and a dated record of that run shows the same checks fired, the run log was kept, and the results stayed within the spread of your own repeated runs.
- How to check it, clause by clause:
  - "A colleague runs your agent setup without you, from what is written down" (Person): The colleague's run, without the owner
  - "a dated record of that run shows the same checks fired" (Run): The dated record of the colleague's run, listing the checks that fired
  - "the run log was kept" (Run): The run log of that run
  - "the results stayed within the spread of your own repeated runs" (Over time): Your own repeated runs of the same tasks, and the colleague's results beside them
- Adds work without helping when: The setup still changes every week and only its owner uses it: a handover run then tests a version that will not last. Run it when a second person is about to rely on it.
- Activities:
  - setup: Once per repository, kept current with every change to the setup
  - review: Once before calling the setup done, then when its owner changes. Due at once when: The owner is away for a sprint or a new developer joins
  - practice: After each handover run: whatever the colleague had to ask becomes written setup or a script that runs the same checks. Due at once when: The colleague needed the owner during the run
- Related: ae-029.

### ae-026 Measure before and after (Mb)

- Column: Adoption. Row: Organisation.
- Problem: The team believes agents made it faster or better, but there is no comparison on comparable work, no quality figure beside the speed figure, and other changes in the same period explain as much.
- Seen on your own code when: The team measured before and after on comparable work over at least a quarter, paired every speed figure with a quality figure, names what else changed in between, and every figure says what it counts, over which window and population.
- How to check it, clause by clause:
  - "The team measured before and after on comparable work over at least a quarter, paired every speed figure with a quality figure, names what else changed in between, and every figure says what it counts, over which window and population" (Over time, Person): Checked live, at team level: before-and-after measurements over a quarter, kept outside any one build
- Adds work without helping when: A person trying a tool for a few weeks: the quarter-long comparison serves a decision to roll agents out to teams, not a first trial.
- Activities:
  - setup: Once per team, before agents or champions start
  - review: At each measurement point, on the same held-back tasks. Due at once when: A model, harness, tool or rollout change
  - decision: Before each rollout wave. Due at once when: Agents are about to reach more teams
  - review: Before a model, effort or harness change is credited: the same tasks run several times under the current setup first, and the change counts only where it moves results beyond that setup's own run-to-run spread
  - setup: Once per team, before the first measurement: records are keyed by task, not by person, and no review form names an engineer's AI usage
  - setup: Every held-back task made from the team's solved work: its answer cannot be reached from the agent's environment, neither in later commits, refs and tags nor in a store that grew after the task. Due at once when: A held-back task is made by reverting or deleting a solution
  - decision: Before a result on replayed past tasks is credited: it counts for the class of tasks the replay covered, not for the work ahead. Due at once when: A model, harness or setting is chosen on replayed past tasks
- Related: ae-037, ae-030.

### ae-009 Kinds of AI (Ka)

- Column: AI products. Row: Task.
- Problem: A language model does work that plain code or a simpler model would do more cheaply and reliably, so the product inherits cost, latency and unpredictability it did not need.
- Seen on your own code when: Each step that uses a language model has a written reason why plain code or another kind of model would not do, and the steps plain code can do are done by plain code.
- Applies when: Applies when the product, or a script that produces its content, calls a language model. A model used only to write the code does not count.
- Adds work without helping when: Writing a long justification for a step whose need for a language model is not in doubt, such as open-ended text a person reads: one sentence of reason is enough.
- Activities:
  - decision: Once per AI feature or workflow, before the build. Due at once when: A step is proposed for a language model
  - practice: Every task, before reaching for a model
  - review: When a step's volume or its model changes. Due at once when: A failure is traced to work done by the wrong kind of tool

### ae-018 Evals for a feature (Ef)

- Column: AI products. Row: Change.
- Problem: An AI feature ships on a few examples tried by hand, so its real failure rate is unknown and a model or prompt change can make it worse unnoticed.
- Seen on your own code when: An AI feature has representative test cases and a pass threshold, agreed before it ships, and met over repeated runs of each case.
- Applies when: Applies when the product ships a feature whose output a model produces at run time, including extraction a person then confirms. Answers recorded once from a model are content, not a feature.
- Adds work without helping when: Growing the case set or tightening the threshold beyond what the decision to ship needs: representative cases and an agreed threshold over repeated runs are the bar, not a benchmark.
- Activities:
  - setup: Once per AI feature, before it ships
  - practice: Every change to prompts, model version, tools or data: each case runs several times, and the result names the number of runs and how many cases passed in all of them
  - review: On a fixed schedule after launch. Due at once when: A production failure or a new model version
  - review: Before the pass threshold is trusted: a person checks a sample of the failing cases themselves; a case that rejects a correct answer is fixed or removed
  - review: Where a model grades the cases: before its scores count, and after any change to its prompt or model, a person labels cases the grader was never tuned on, the grader runs on them once, and both rates are reported (correct answers it passes, wrong answers it fails); scores from two grader versions are not read as a trend. Due at once when: A model grades the cases, or its prompt or model changes
- Related: ae-036.

### ae-027 Retrieval and grounding (Rg)

- Column: AI products. Row: System.
- Problem: An AI feature answers from retrieved documents, but only the final answers are checked, so a retrieval failure looks like a model failure and gets fixed in the wrong place.
- Seen on your own code when: Retrieval has its own test set, and the answers are also tested end to end.
- Adds work without helping when: Tuning retrieval further while the end-to-end answers already meet their agreed threshold: improve retrieval where the end-to-end tests fail.
- Activities:
  - setup: Once per retrieval feature, before launch
  - practice: Every change to the retriever, chunking, index or embedding model
  - review: On a fixed schedule once real traffic exists. Due at once when: Real queries arrive or the document corpus changes
- Related: ae-018.

### ae-036 AI in production (Rp)

- Column: AI products. Row: Organisation.
- Problem: A live AI feature degrades, costs more or drifts after launch, and nobody notices until users do, because nobody watches real traffic for it.
- Seen on your own code when: A live AI feature has a quality check on real traffic, a cost budget and a drift alert, each with a person who acts on it.
- Applies when: Applies when a model is called on live user traffic. Not applicable when no model runs at request time; can't tell when that is unknown.
- Adds work without helping when: Adding dashboards once the quality check, the cost budget and the drift alert each have a person who acts on them: signals nobody acts on add noise.
- Activities:
  - setup: Once per AI feature, before launch
  - review: Weekly in the first month after launch, then monthly; drift and budget as alerts in between. Due at once when: A model snapshot, prompt or provider changes, or cost passes its budget
  - decision: Each time the model choice is revisited. Due at once when: A new model release changes price or quality on the task

## Gaps

- predicted gap, adoption × task: Show a run.

## Retired IDs

- ae-008 Shared conventions: retired, see ae-029.
- ae-035 Govern who builds: retired, see ae-030.01.
