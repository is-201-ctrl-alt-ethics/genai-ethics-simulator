<!-- Extracted from the course-site page is201/final-project.html (reinald-dp-course-pages fork), accessed 2026-11-24. Interactive widgets are described as text; their values are the same as in the page script. -->

# Final Group Project: Technology and Society Ethics Simulator

*IS 201: Computer Ethics · Final Requirement*

Build an interactive website where users change technological decisions and a rule-based model calculates the effects on equity, governance, and sustainability. It is not a branching story or a quiz: outcomes come from combinations of decisions.

*Faculty-in-Charge: **Dr. Reinald Adrian Pugoy** — First Semester, AY 2026–2027*

> [!IMPORTANT]
> **Submit by:** December 19, 2026
> Group size: 4–5 students · Output: one interactive website · Video: 10–12 min, on YouTube

## Step 1: Pick one scenario

> **Max 3 groups per scenario.** A sign-up sheet will be on the course site by **Monday, November 23**. Slots are first come, first served.

1. **Campus Surveillance**: Facial recognition for university attendance and security
2. **Employee Recruitment**: AI screening and shortlisting of job applicants
3. **Social Assistance Distribution**: Digital eligibility checks and benefit distribution
4. **Generative AI in Universities**: Institutional policy on GenAI in teaching, assessment, and admin
5. **Smart City Surveillance**: AI cameras across public spaces for public safety
6. **Healthcare Prioritization**: AI-assisted patient prioritization in a public hospital
7. **Digital Learning for Public Schools**: A unified platform, including isolated communities
8. **Device Lifecycle Management**: Software support, repair, and replacement cycles for devices
9. **Credit Scoring**: AI loan evaluation, including people with thin credit histories
10. **Content Moderation**: AI detection of misinformation, hate speech, and harmful content

## Step 2: What to build

Your group decides the variables and indicators on its own. The emphasis is on ethical reasoning, not programming sophistication.

| Requirement | Minimum | What it means |
|---|---|---|
| Decision variables | 5+ | Choices users can change, each with at least two meaningful options. |
| Consequence indicators | 5+ | Scores, ratings, or other measures, each with a clear interpretation. Each must measure a distinct consequence. |
| Variable interactions | 4+ | Where one variable's effect depends on another's value. Each must involve a different pair of variables and come with a stated justification. |

A well-justified interaction counts for more than an extra one.

### Indicators must cover

- **Equity and Social Justice**
- **Technology Governance and Responsible Innovation**
- **Computing and Sustainability**
- + other dimensions of your choice

These three areas must shape the model itself. Also apply at least two of: ethical frameworks and professional responsibility; privacy, data, and digital rights; cybersecurity; AI; software development. Just mentioning them doesn't count.

### The model must

- Update indicators automatically when decisions change
- Let several variables affect the same indicator
- Show real trade-offs, not decisions that are simply right or wrong
- Make its rules and calculations understandable to users

### The simulator must include

- **Scenario overview** with context and stakeholders
- **Decision interface** and **consequence dashboard**
- **Ethical explanations** of the trade-offs
- **Model transparency**: rules, assumptions, limitations
- **References**

## A sample simulator: the Moon Cheese Allocator

> [!NOTE]
> **Made-up example.** Everything here is invented, including the numbers. It shows only the mechanics: your decisions trigger rules, and the rules move the indicators. Use it to see how a simulator works, not as a template. Your own variables, rules, and weights must come from evidence.

The Lunar Council wants an AI to divide the weekly cheese supply among its crater villages. Stakeholders: villagers, the Council, the Cheese Workers' Guild, and the very fragile moon environment.

### Decisions (5 variables)

| Variable | Options |
|---|---|
| Allocation basis | Equal shares · By need · Crater seniority |
| Data collected | Minimal · Full nibble tracking |
| Human review | None · Spot checks · Every appeal |
| Explanations | Black box · Published |
| Server power | Diesel · Solar |

### Consequences (5 indicators, 0–100)

Each indicator starts at 50 and is shown as a bar from 0 to 100.

| Indicator | Dimension |
|---|---|
| Fairness | Equity |
| Accountability | Governance |
| Sustainability | Sustainability |
| Privacy | Other dimension |
| Worker wellbeing | Other dimension |

### Show the rules behind the numbers

| Decision | Fairness | Accountability | Sustainability | Privacy | Worker wellbeing |
|---|---|---|---|---|---|
| Allocation: equal / by need / crater seniority | +10 / +5 / −20 | | | | |
| Data: minimal / full nibble tracking | interaction 1 | | 0 / −10 | +25 / −25 + interaction 4 | |
| Human review: none / spot checks / every appeal | 0 / +5 / +10 | −15 / +5 / +15 + interaction 2 | 0 / 0 / −5 | | +10 / −5 / interaction 3 |
| Explanations: black box / published | | −10 / +15 | | | |
| Server power: diesel / solar | | | −20 / +20 | | |
| **Interaction 1** | Full tracking adds +20 fairness *only* when allocation is by need (better need estimates). Under other bases it adds nothing. | | | | |
| **Interaction 2** | Reviewing every appeal adds a further +10 accountability *only* when explanations are published, because reviewers can't check what they can't see. | | | | |
| **Interaction 3** | Reviewing every appeal costs workers −10 wellbeing, or −20 under crater seniority, which villagers dispute far more often. | | | | |
| **Interaction 4** | Full tracking costs a further −15 privacy when the system is a black box, because villagers can't see how their nibble data is used. | | | | |

Every indicator starts at 50, the rule effects are added, and the result is capped between 0 and 100. In a real project, each row would need a source and a stated assumption.

## Step 3: Justify your rules

- Ground the model in credible evidence: literature, documented cases, laws and policies, codes of ethics, or institutional guidelines.
- For each key relationship, explain **why** it exists, **what** supports it, and its **assumptions and limitations**.
- If you use scores or weights, explain how you set them.

> [!WARNING]
> The simulator illustrates ethical trade-offs. It does not predict real outcomes, so label hypothetical values clearly.

Generative AI can help with research, coding, and debugging, but your group verifies sources, justifies the model, and validates results. AI-generated ethical judgments can't replace the rule-based model.

## Step 4: Submit and get graded

### Submit by December 19, 2026

- A working **website link**
- All explanations, rules, and references **inside the simulator**. No separate report.
- A **10–12 minute recorded video** on YouTube, presenting and demonstrating the website: scenario, variables and indicators, model and its justification, how different decisions change outcomes, insights and limitations
- **Every member** contributes to the work and appears in the video
- The **best project** will have the opportunity to publish its work with Doc Rein in conferences and journals

### Grading

| Criterion | Weight |
|---|---|
| Ethical reasoning and course concepts | 30% |
| Quality and justification of the model | 30% |
| Functionality and usability | 25% |
| Presentation and demo | 15% |

## Submission checklist

Tick off each item as your group finishes it. (On the course site, ticks are saved only in that browser.)

**Submit to the course site: what you hand in**

- [ ] **Working website link**: Opens and runs for anyone with the link
- [ ] **YouTube video link**: Recorded presentation and demo, viewable by anyone with the link

**Inside your website: what the site itself must contain**

- [ ] **Scenario overview**: Context and affected stakeholders
- [ ] **Decision interface**: 5+ decision variables, each with at least two meaningful options
- [ ] **Consequence dashboard**: 5+ distinct indicators covering equity, governance, and sustainability, plus others
- [ ] **Rule-based model**: Indicators update automatically, with 4+ interactions, each on a different pair of variables and justified
- [ ] **Course concepts applied**: The three central areas plus at least two others shape the model
- [ ] **Ethical explanations**: Consequences, competing interests, and trade-offs
- [ ] **Model transparency**: Rules, assumptions, limitations; hypothetical values labeled
- [ ] **References**: Credible sources supporting the analysis and model

**In your video: what the recording must cover**

- [ ] 10–12 minutes long
- [ ] Scenario and its societal significance
- [ ] Variables, indicators, and the model with its justification
- [ ] Demo: how different decisions produce different outcomes
- [ ] Ethical insights and limitations
- [ ] Every member appears and speaks

---

*Guiding question:* How can technological decisions be modeled to demonstrate their consequences for equity, governance, and sustainability?
