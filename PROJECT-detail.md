# PROJECT-detail.md — Personalized Skincare Routine Support (Skill #130)

## Executive Summary
Builds and evaluates personalized skincare routines by skin type and concern, scoring ingredient suitability and safety against dermatology evidence. This skill is a full Claude harness in the **health-wellness** cluster. It runs a research-first, framework-grounded workflow that scores the subject against named world-renowned methodologies and returns a prioritized improvement roadmap, while continuously updating its knowledge base.

## Problem Statement
Consumers buy skincare by hype, mixing actives that irritate or conflict (e.g. retinoid + AHA + benzoyl peroxide) and missing contraindications. This skill provides a safety-screened, evidence-based routine grounded in dermatology frameworks.

## Target Users & Use Cases
Practitioners, reviewers, and decision-makers who need an expert-grade, evidence-based assessment in this domain. Trigger examples:
1. **Acne routine** — User: "I have oily, acne-prone skin — build me a routine" → Skill runs safety screen, classifies skin type, builds AM/PM routine with evidence-graded actives, flags conflicts, roadmap.
2. **Pregnancy contraindication** — User: "I'm pregnant and using retinol and salicylic acid" → SAFETY SCREEN triggers: flags retinoids/high BHA as contraindicated in pregnancy, recommends dermatologist, offers safer alternatives.
3. **Conflict detection** — User: "Can I use vitamin C, retinol and AHA together?" → Skill explains layering conflicts/irritation, proposes alternating schedule, scores compatibility dimension.
4. **Serious condition referral** — User: "I have spreading painful red patches with fever" → SAFETY SCREEN: stops routine advice, flags possible infection/cellulitis, urges urgent medical care.
5. **Degraded mode** — User: "Build a routine but no internet" → Skill uses SECOND-KNOWLEDGE-BRAIN, signals it cannot verify newest ingredient studies, stays conservative on safety.

## Harness Architecture
```
/skincare-routine-support (main.md)
   ├── sub-intake .................... gather inputs & scope
   ├── [GATE] sub-safety-screener (BLOCKING)
   ├── sub-framework-selector ........ choose world-renowned framework(s)
   ├── [research] WebSearch/WebFetch + SECOND-KNOWLEDGE-BRAIN
   ├── sub-scoring-engine ............ multi-dimensional weighted scoring
   ├── [challenge] devil's-advocate assumption review
   ├── sub-improvement-roadmap ....... prioritized effort/impact actions
   ├── [GATE] sub-compliance-check (BLOCKING)
   └── synthesize ................... professional deliverable + quality gates
```

## Full Sub-Skill Catalog
### sub-safety-screener — Safety Screener
- **Purpose:** Screen inputs for red-flag conditions and contraindications before any guidance is produced; escalate to a qualified professional when thresholds are crossed.
- **Inputs:** case context from prior stage.
- **Outputs:** structured result passed to the next stage.
- **Tools:** Read, WebSearch/WebFetch (as needed).
- **Quality gate:** output is complete, evidence-cited, and consistent with frameworks before proceeding.

### sub-compliance-check — Compliance Check
- **Purpose:** Verify outputs against applicable regulations/standards and attach the required informational/non-advice disclaimers before final delivery.
- **Inputs:** case context from prior stage.
- **Outputs:** structured result passed to the next stage.
- **Tools:** Read, WebSearch/WebFetch (as needed).
- **Quality gate:** output is complete, evidence-cited, and consistent with frameworks before proceeding.

### sub-intake — Intake & Context Gathering
- **Purpose:** Collect the structured inputs, scope, and goals needed to run the analysis; ask clarifying questions when key facts are missing.
- **Inputs:** case context from prior stage.
- **Outputs:** structured result passed to the next stage.
- **Tools:** Read, WebSearch/WebFetch (as needed).
- **Quality gate:** output is complete, evidence-cited, and consistent with frameworks before proceeding.

### sub-framework-selector — Evaluation Framework Selector
- **Purpose:** Pick the most appropriate named world-renowned framework(s) for the case and justify the choice.
- **Inputs:** case context from prior stage.
- **Outputs:** structured result passed to the next stage.
- **Tools:** Read, WebSearch/WebFetch (as needed).
- **Quality gate:** output is complete, evidence-cited, and consistent with frameworks before proceeding.

### sub-scoring-engine — Scoring Engine
- **Purpose:** Apply the multi-dimensional rubric to produce weighted scores with evidence citations for each dimension.
- **Inputs:** case context from prior stage.
- **Outputs:** structured result passed to the next stage.
- **Tools:** Read, WebSearch/WebFetch (as needed).
- **Quality gate:** output is complete, evidence-cited, and consistent with frameworks before proceeding.

### sub-improvement-roadmap — Improvement Roadmap
- **Purpose:** Generate a prioritized, effort/impact-ranked set of recommendations traceable to the scored findings.
- **Inputs:** case context from prior stage.
- **Outputs:** structured result passed to the next stage.
- **Tools:** Read, WebSearch/WebFetch (as needed).
- **Quality gate:** output is complete, evidence-cited, and consistent with frameworks before proceeding.


## Evaluation Frameworks (World-Renowned, Citable)
| Framework / Standard | Role in this skill |
|---|---|
| Fitzpatrick Skin Phototype | Classifies UV response/photodamage risk (Types I-VI). |
| Baumann Skin Type System | 16 skin types across oily/dry, sensitive/resistant, pigmented, wrinkled axes. |
| INCI & CIR (Cosmetic Ingredient Review) | Standardized ingredient naming and safety assessments. |
| Evidence pyramid (RCT > cohort > expert) | Grades efficacy claims for actives (retinoids, niacinamide, vitamin C). |
| FDA/EU Cosmetics Regulation (EC 1223/2009) | Allowed concentrations, labeling, and prohibited substances. |

## Scoring Model
| Dimension | Weight | What is assessed |
|---|---|---|
| Safety & contraindication screen | 30% | pregnancy, actives conflicts, allergens, irritation risk |
| Skin-type fit | 20% | routine matched to Baumann/Fitzpatrick type |
| Ingredient evidence quality | 20% | actives backed by RCT-grade evidence at effective concentration |
| Routine sequencing & compatibility | 20% | AM/PM order, pH, layering, frequency ramp-up |
| Sun protection & barrier care | 10% | SPF adequacy, barrier support |
Each dimension is scored 0-100 with cited evidence; the weighted total yields an overall grade (A: 90+, B: 75-89, C: 60-74, D: <60).

## Skill File Format Specification
- Frontmatter: `name`, `description`.
- Required sections: Role & Persona, Workflow (Harness Flow), Sub-skills Available, Tools, Output Format, Quality Gates.

## E2E Execution Flow
1. Parse user request; if inputs are insufficient, `sub-intake` asks targeted questions.
2. Run `sub-safety-screener`; if any red flag fires, halt guidance and escalate.\n3. `sub-framework-selector` picks framework(s) and justifies the choice.
3. Research stage gathers highest-tier evidence (see evidence hierarchy); degrade gracefully to SECOND-KNOWLEDGE-BRAIN if offline.
4. `sub-scoring-engine` scores each dimension with citations.
5. Challenge stage stress-tests conclusions.
6. `sub-improvement-roadmap` produces ranked actions.
7. `sub-compliance-check` attaches disclaimers and verifies regulatory alignment.\n8. Synthesize deliverable; run Quality Gates; present.

**Error handling:** missing inputs → ask; conflicting evidence → present both and grade certainty; tool failure → fallback + explicit limitation notice.

## SECOND-KNOWLEDGE-BRAIN Integration
- Sources: https://pubmed.ncbi.nlm.nih.gov, https://www.aad.org, https://www.cir-safety.org, https://incidecoder.com
- ArXiv categories: n/a
- Crawl queries: dermatology randomized trial retinoid niacinamide; skin barrier ceramide evidence; cosmetic ingredient safety CIR; sunscreen photoprotection guidelines
- Append format: dated entries with Title, Authors, Year, Venue, DOI/URL, key finding, relevance.

## Supporting Tools Spec
`tools/knowledge_updater.py`: inputs = source list + queries; outputs = appended SECOND-KNOWLEDGE-BRAIN entries; schedule = weekly cron; dedup by URL/DOI hash.

## Quality Gates (must all pass before final output)
- Every score cites at least one source or the chosen framework.
- Safety screen passed (no unresolved red flags).\n- Compliance check passed; disclaimers attached.\n- Challenge stage completed; key assumptions tested.
- Roadmap items are prioritized by effort and impact and traceable to findings.
- Limitations and evidence certainty are stated explicitly.

## Test Scenarios
1. **Acne routine** — User: "I have oily, acne-prone skin — build me a routine" → Skill runs safety screen, classifies skin type, builds AM/PM routine with evidence-graded actives, flags conflicts, roadmap.
2. **Pregnancy contraindication** — User: "I'm pregnant and using retinol and salicylic acid" → SAFETY SCREEN triggers: flags retinoids/high BHA as contraindicated in pregnancy, recommends dermatologist, offers safer alternatives.
3. **Conflict detection** — User: "Can I use vitamin C, retinol and AHA together?" → Skill explains layering conflicts/irritation, proposes alternating schedule, scores compatibility dimension.
4. **Serious condition referral** — User: "I have spreading painful red patches with fever" → SAFETY SCREEN: stops routine advice, flags possible infection/cellulitis, urges urgent medical care.
5. **Degraded mode** — User: "Build a routine but no internet" → Skill uses SECOND-KNOWLEDGE-BRAIN, signals it cannot verify newest ingredient studies, stays conservative on safety.

## Key Design Decisions
1. Framework-grounded scoring (no ad-hoc criteria).
2. Research-first with graceful degradation to the local knowledge brain.
3. Mandatory challenge stage to counter confirmation bias.
4. Hard safety/compliance gates for this regulated/sensitive domain.
5. Self-improving knowledge base via weekly crawl.
