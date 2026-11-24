# Plan

Working plan for the IS 201 final project: a **Technology and Society Ethics Simulator** for
**Scenario 4: Generative AI in Universities** (institutional policy on GenAI in teaching, assessment
and administration). The full brief is in [docs/requirements/final-req.md](docs/requirements/final-req.md).

**Due: Saturday, December 19, 2026.** Submit a working website link and a 10–12 min YouTube video.

## 1. What the requirements boil down to

| Area | Hard requirement | Where it lives in this repo |
|---|---|---|
| Decision variables | 5+, each with 2+ meaningful options | `data/model.json` → `variables` |
| Indicators | 5+, distinct, clear interpretation; must cover **equity**, **governance**, **sustainability** + others | `data/model.json` → `indicators` |
| Interactions | 4+, each on a **different pair** of variables, each justified | `data/model.json` → `interactions` |
| Course concepts | The 3 central areas **shape the model**, plus 2+ of: ethical frameworks/professional responsibility, privacy/data rights, cybersecurity, AI, software development | Tagged per rule in `model.json`; explained on the site |
| Model behaviour | Auto-updates; several variables per indicator; real trade-offs (no "right answer"); understandable rules | `js/engine.js` + the rendered rules table |
| Site sections | Scenario overview + stakeholders · decision interface · dashboard · ethical explanations · model transparency (rules, assumptions, limitations, hypothetical labels) · references | `index.html` sections |
| Evidence | Each key relationship: **why**, **what supports it**, **assumptions/limitations**; how weights were set | `justification` + `sources` fields per rule; `data/references.json` |
| No separate report | Everything is inside the site | Nothing graded lives only in `docs/` |
| Video | 10–12 min; scenario, model + justification, demo, insights, limitations; **every member speaks** | `docs/video/script.md` |

**Grading:** ethical reasoning 30% · model quality and justification 30% · functionality and usability 25% · presentation 15%.
So 60% rides on the *reasoning and evidence*, not the code, and the plan front-loads research and model design.

## 2. Key design decision: one model file drives everything

The model (variables, options, indicators, base values, effects, interactions, justifications and
source IDs) lives in **one data file**, `data/model.json`. The site:

1. builds the decision controls from it,
2. computes the indicators from it (`js/engine.js`, a small pure function), and
3. renders the "How the model works" rules table and the justifications from it.

So the rules users read are *exactly* the rules that run, and the team can change the model without
touching UI code. A small check script (`tools/check-model.js`, run in CI) fails if the model drops
below the minimums: under 5 variables or indicators, a variable with fewer than 2 options, a missing
required dimension, fewer than 4 interactions, two interactions on the same pair, or a rule with no
justification or source.

Scoring follows the brief's sample: every indicator starts at a base (e.g. 50), rule effects add up,
and the result is clamped to 0–100. All values are labelled **hypothetical**.

## 3. Repo structure

```
genai-ethics-simulator/
├── index.html              # the whole site (sections below), served by GitHub Pages
├── css/style.css
├── js/
│   ├── engine.js           # pure: (model, decisions) → indicator scores + which rules fired
│   └── app.js              # renders controls, dashboard, explanations, rules table
├── data/
│   ├── model.json          # single source of truth for the model
│   └── references.json     # citation list; rules cite these by id
├── tools/check-model.js    # requirement checks on model.json (run by CI)
├── docs/                   # team working files, NOT graded (the site must be self-contained)
│   ├── requirements/final-req.md
│   ├── research/           # evidence log: one note per source or topic
│   └── video/script.md     # video outline, speaker split
├── .github/workflows/check.yml
├── PLAN.md
└── README.md
```

Site sections in `index.html`: **Overview** (context, stakeholders) → **Simulator** (decisions, live
dashboard, which rules fired) → **Trade-offs** (ethical explanations) → **How the model works**
(rules table, assumptions, limitations, how weights were set) → **References**.

## 4. Draft model (a starting point for the team, not a decision)

These are *candidates* to argue over in the model-design meeting. Every item kept needs evidence (§5).

### Stakeholders

Students (including those with limited devices or connectivity, and non-native English writers),
faculty, administrators and staff, the university as an institution, AI vendors, parents and the
public, and the environment.

### Candidate decision variables

| Variable | Options |
|---|---|
| Usage policy | Ban · Allowed with disclosure · Fully integrated |
| AI detection | None · Detector as a flag for human review · Detector output as evidence |
| Tool provisioning | Students bring their own (free tiers) · Institution-licensed enterprise tool · Self-hosted open model |
| Assessment design | Unchanged · Partly redesigned (oral, in-class, process-based) · Fully redesigned |
| Data governance | Vendor default terms · Negotiated data agreement (no training on student data) · On-premise only |
| AI literacy training | None · Optional · Mandatory for students and faculty |
| Administrative use | None · Drafting and support only · Automated decisions (e.g. admissions or advising triage) |
| Policy governance | Administration only · Committee with faculty and student representatives |

### Candidate indicators

| Indicator | Dimension |
|---|---|
| Equity of access | Equity and social justice |
| Fairness of integrity enforcement | Equity and social justice |
| Accountability and transparency | Technology governance |
| Environmental footprint | Computing and sustainability |
| Student data privacy | Privacy, data and digital rights |
| Learning and skill development | Other (learning outcomes) |
| Assessment validity | Other (academic integrity) |
| Faculty workload | Other (professional responsibility) |

### Candidate interactions (each on a different pair)

1. **AI detection × Usage policy:** detectors under a ban drive more accusations, and known false
   positives against non-native English writers hurt *fairness of enforcement* more.
2. **Tool provisioning × Usage policy:** full integration with student-supplied tools widens the
   paid-tier gap (*equity*); with institution-licensed tools it narrows it.
3. **Tool provisioning × Data governance:** negotiated terms protect *privacy* only for
   institution-licensed tools; with bring-your-own tools the university controls nothing.
4. **AI literacy × Assessment design:** redesigned assessment raises *learning* more when students
   and faculty are trained to use the tools well.
5. **Administrative use × Policy governance:** automated admin decisions hurt *accountability* far
   more without a representative oversight body.
6. A *sustainability* interaction, e.g. **Tool provisioning × Usage policy** on energy use is taken
   by #2, so look for another pair (e.g. self-hosted hardware × usage level). Keep every pair distinct.

### Course concepts to tag

Central: equity, governance, sustainability. Plus **AI**, **privacy, data and digital rights**, and
**ethical frameworks and professional responsibility** (e.g. ACM Code of Ethics, faculty duty of care).

## 5. Evidence to find and verify

A member checks every source before it is cited. Leads to start from (not yet verified):

- UNESCO, *Guidance for generative AI in education and research* (2023).
- Liang et al. (2023), GPT detectors are biased against non-native English writers (*Patterns*).
- Republic Act 10173, the Data Privacy Act of 2012 (Philippines), and National Privacy Commission issuances.
- University of the Philippines guidance on responsible AI use, and any CHED guidance (check what exists).
- EU AI Act, which lists some education uses as high-risk (a governance comparison).
- Research on the energy and water use of AI training and inference (e.g. Luccioni et al.).
- ACM Code of Ethics and Professional Conduct.
- Documented cases: universities that banned and later reversed GenAI policies; false accusations from AI detectors.

Log each source in `docs/research/` with the claim it supports, the rule(s) it backs, and its limitations.

## 6. Timeline (milestones)

| Milestone | Dates | Outcome |
|---|---|---|
| **M1 Research and model design** | Nov 24 – Dec 1 | Stakeholders, final variables/indicators/interactions, evidence log, weights rationale |
| **M2 Simulator build** | Dec 2 – Dec 8 | `model.json` filled in; engine, UI, dashboard and rules table working on Pages; CI check passing |
| **M3 Site content** | Dec 5 – Dec 12 | Overview, trade-off explanations, assumptions, limitations and references written into the site |
| **M4 Review and polish** | Dec 12 – Dec 15 | Full checklist audit, usability test with someone outside the group, mobile check, fixes |
| **M5 Video and submission** | Dec 15 – Dec 19 | Script, recording (everyone speaks), YouTube upload, both links submitted |

Aim to submit by **Dec 18** to keep a day of buffer.

## 7. How we work

- Work is tracked as issues under the milestones above, using the org's issue forms (Task, Bug, Feature, Docs).
- Branch per issue, open a PR, and get one teammate's review before merging to `main`. `main` is what Pages serves.
- **GenAI use:** allowed for research help, coding and debugging, per the brief. Members verify every
  source, and the model's rules and ethical judgments are the group's own; AI output never stands in
  for a justification.
- Every member contributes and appears in the video, as the brief requires.

## 8. Open questions

- Team members' GitHub handles and roles (research, model, front-end, content, video).
- Final variable/indicator set and the weighting scheme (fixed points as in the sample, or something else).
- One page or several? One page keeps the demo simple, so that is the default.
