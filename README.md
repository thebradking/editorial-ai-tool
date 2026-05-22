# Editorial AI Tool

A lightweight, browser-based tool for tagging the AI applicability of every task in an editorial workflow. Built as a single self-contained HTML file — no install, no build step, no backend.

**Live site:** [thebradking.github.io/editorial-ai-tool](https://thebradking.github.io/editorial-ai-tool/)

**Paper reference.** Cai, A., YeckehZaare, I., Sun, S., Charisi, V., Wang, X., Imran, A., Laubacher, R., Prakash, A., & Malone, T. W. (2026). *Where can AI be used? Insights from a deep ontology of work activities.* MIT Center for Collective Intelligence. [arXiv:2603.20619](https://arxiv.org/abs/2603.20619).

**See also.** [`editorial-ai-ontology`](https://github.com/thebradking/editorial-ai-ontology) — a successor project that operationalizes the same idea against the paper's full framework: inheritance, scenario planning, multi-typed risk, and per-activity evidence. v1 (this repo) is the lightweight workflow tagger; v2 is the methodology-grounded version. Both are maintained; they answer different questions.

## What this is

Researchers from MIT's Sloan School of Management published a 120-page paper outlining a framework for evaluating workflows — and the tasks that make them up — to help teams determine where (or if) AI might be deployed and how that might (or might not) help the team. It's a deep dive into the nuance of work, the kind project managers who've done Work Breakdown Structures have lived with for a while.

The general idea that resonated for me (and please read the paper to get the actual idea) is that you shouldn't — or can't — think about using AI for your workflow. Instead, you should evaluate each individual task within a workflow to determine whether or when it can be improved with an existing tool or one that will soon exist. This gives teams the ability to be thoughtful about how to improve their workflows.

While I was an academic for almost twelve years, I'm a practitioner at heart. (Go, Journalism and Storytelling.) I've always tried to operationalize research and turn it into a practical tool that helps me solve problems. That's what research is (sometimes) really good at doing.

So, I turned to Claude Projects and vibe-coded an interactive template that uses that framework and turns it into a usable tool for building a workflow and evaluating the potential use of AI for any task within it.

If you're working toward understanding when, why, and whether you can (or shouldn't) use AI in your workflows, this framework is pretty great.

## What v1 does

- **Workflow phases** — Planning, Writing, Editing, Design, Distribution, Analytics (editable)
- **Per-activity tagging** — for each task in a phase, record:
  - **Applicability** — is AI available for this? (`none` / `emerging` / `available` / `commoditized`)
  - **Mode** — how would you use it? (`human` / `augmentation` / `either` / `automation`)
  - **Risk** — what level? (`low` / `medium` / `high`)
  - **Recommendation** — what to do about it? (`human` / `monitor` / `pilot` / `adopt`)
  - **Rationale** — free-text reasoning
  - **Currently using AI** — toggle
- **Multiple workflows** — switch between templates (Newsletter, Magazine, anything else you add)
- **JSON import/export** — share configurations as files

v1 treats each activity as an independent thing to tag. It doesn't model the paper's inheritance hierarchy, scenario planning, or risk typology — that's what v2 is for.

## File structure

```
.
├── editorial-ai-tool (1).json   ← sample seed data (Newsletter workflow)
├── index.html                    ← the whole tool — open it directly
├── README.md
└── LICENSE                       ← GPL-3.0
```

No `package.json`. No build step. No dependencies. One HTML file that runs in any modern browser.

## Use it

**Easiest:** click the live site → [thebradking.github.io/editorial-ai-tool](https://thebradking.github.io/editorial-ai-tool/).

**Run locally:** download or clone the repo, then double-click `index.html`. It opens in your browser and runs.

**Edit the seed data directly:** open `editorial-ai-tool (1).json` in any text editor. The in-app UI can also import and export JSON files for sharing or backup.

**Note on persistence.** This is a local-only tool. Edits live in your browser session — refresh and they're gone unless you export to JSON first. Treat the export as your save button.

## Data schema

The JSON file holds workflows, each containing phases and activities.

| Field | Type | Notes |
|---|---|---|
| `id` | string | Unique identifier |
| `activity` | string | Task name (verb-object pair recommended) |
| `description` | string | One-line description |
| `phase` | string | Which workflow phase it belongs to |
| `applicability` | enum | `none` / `emerging` / `available` / `commoditized` |
| `mode` | enum | `human` / `augmentation` / `either` / `automation` |
| `risk` | enum | `low` / `medium` / `high` |
| `rec` | enum | `human` / `monitor` / `pilot` / `adopt` |
| `rationale` | string | Free-text reasoning for the ratings above |
| `usingAI` | boolean | Is your team currently using AI for this task? |
| `notes` | string | Internal notes, status, blockers |

Workflows themselves carry `id`, `name`, an ordered list of `phases`, and an array of `activities`.

## License

GPL-3.0. The MIT Sloan paper and its ontology are separately licensed by their authors.
