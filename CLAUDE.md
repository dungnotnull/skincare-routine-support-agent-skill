# CLAUDE.md — Personalized Skincare Routine Support (Skill #130)

**Slug:** `skincare-routine-support`  •  **Cluster:** `health-wellness`  •  **Source idea:** 130  •  **Phase:** Production Ready (v1.0.0)

## Tagline
Builds and evaluates personalized skincare routines by skin type and concern, scoring ingredient suitability and safety against dermatology evidence.

## Problem This Skill Solves
Consumers buy skincare by hype, mixing actives that irritate or conflict (e.g. retinoid + AHA + benzoyl peroxide) and missing contraindications. This skill provides a safety-screened, evidence-based routine grounded in dermatology frameworks.

## Harness Flow Summary
1. **Intake** (`sub-intake`) — gather structured inputs, scope, goals.
2. **Safety screen** (`sub-safety-screener`) — MANDATORY before guidance.\n3. **Framework selection** (`sub-framework-selector`) — choose named world-renowned framework(s).
4. **Research** (WebSearch/WebFetch + SECOND-KNOWLEDGE-BRAIN) — gather highest-tier evidence.
5. **Scoring** (`sub-scoring-engine`) — multi-dimensional weighted scores with citations.
6. **Challenge** — devil's-advocate review of assumptions and weak evidence.
7. **Roadmap** (`sub-improvement-roadmap`) — prioritized effort/impact recommendations.
8. **Compliance check** (`sub-compliance-check`) — MANDATORY before final output.\n9. **Synthesize** — assemble the professional deliverable; pass Quality Gates.

## Gates
- **Safety gate:** `sub-safety-screener` MUST run and pass before any guidance is produced.
- **Compliance gate:** `sub-compliance-check` MUST run before the final deliverable, attaching required disclaimers.

## Sub-skills
- `skills/sub-safety-screener.md` — Safety Screener: Screen inputs for red-flag conditions and contraindications before any guidance is produced; escalate to a qualified professional when thresholds are crossed.
- `skills/sub-compliance-check.md` — Compliance Check: Verify outputs against applicable regulations/standards and attach the required informational/non-advice disclaimers before final delivery.
- `skills/sub-intake.md` — Intake & Context Gathering: Collect the structured inputs, scope, and goals needed to run the analysis; ask clarifying questions when key facts are missing.
- `skills/sub-framework-selector.md` — Evaluation Framework Selector: Pick the most appropriate named world-renowned framework(s) for the case and justify the choice.
- `skills/sub-scoring-engine.md` — Scoring Engine: Apply the multi-dimensional rubric to produce weighted scores with evidence citations for each dimension.
- `skills/sub-improvement-roadmap.md` — Improvement Roadmap: Generate a prioritized, effort/impact-ranked set of recommendations traceable to the scored findings.

## Tools Required
- `WebSearch`, `WebFetch` — live evidence and standards updates
- `Read`, `Write` — load knowledge base, emit deliverables
- `Bash` — run `tools/knowledge_updater.py`
- Skill tool — invoke sub-skills in sequence

## Knowledge Sources
- ArXiv: (no ArXiv categories; domain is non-academic-preprint)
- Authoritative domain sources:
  - https://pubmed.ncbi.nlm.nih.gov
  - https://www.aad.org
  - https://www.cir-safety.org
  - https://incidecoder.com
- Crawl queries: dermatology randomized trial retinoid niacinamide; skin barrier ceramide evidence; cosmetic ingredient safety CIR; sunscreen photoprotection guidelines

## Supporting Tools
- `tools/knowledge_updater.py` — crawl4ai pipeline that grows `SECOND-KNOWLEDGE-BRAIN.md` (weekly cron recommended).

## Health & Wellness Cluster Integration

This skill is part of the `health-wellness` cluster. Sub-skills are designed for reuse by sibling skills in the cluster.

### Reusable Sub-Skills

The following sub-skills can be invoked by other health-wellness cluster skills:

#### Safety Screener (`sub-safety-screener`)
**Reusable by**: Any health/wellness skill providing guidance that could impact user wellbeing.

**Interface**:
- Input: Case context with user health information
- Output: Safety screen result (PASS/BLOCKING) with escalation guidance if needed
- Use case: Any skill needing safety screening before providing guidance

**Usage example**:
```markdown
To invoke from another skill:
Use Skill tool with `sub-safety-screener` from `skincare-routine-support`.
Adapt red-flag categories for your domain (medical conditions, medications, etc.).
```

#### Compliance Check (`sub-compliance-check`)
**Reusable by**: Any skill providing regulated domain guidance (health, financial, legal).

**Interface**:
- Input: Draft deliverable ready for final review
- Output: Compliance-verified result with disclaimers attached
- Use case: Any skill needing regulatory compliance and disclaimers

**Usage example**:
```markdown
To invoke from another skill:
Use Skill tool with `sub-compliance-check` from `skincare-routine-support`.
Update jurisdiction lists as needed for your domain.
```

#### Intake (`sub-intake`)
**Reusable by**: Any skill requiring structured data collection.

**Interface**:
- Input: Initial user query
- Output: Structured intake summary with all required categories
- Use case: Any skill needing systematic information gathering

**Usage example**:
```markdown
To invoke from another skill:
Use Skill tool with `sub-intake` from `skincare-routine-support`.
Customize data categories for your domain.
```

### Cluster-Level Patterns

This skill implements patterns useful for cluster-wide adoption:

1. **Gate Pattern**: BLOCKING gates before and after core analysis
2. **Framework Grounding**: Named, citable frameworks vs. ad-hoc criteria
3. **Evidence Hierarchy**: Explicit evidence quality grading (RCT > cohort > expert)
4. **Graceful Degradation**: Offline operation using local knowledge base
5. **Challenge Stage**: Devil's-advocate review to counter confirmation bias

### Cluster Collaboration

For sibling skills wanting to collaborate:

1. **Shared Safety Gate**: Use `sub-safety-screener` for consistent safety screening
2. **Shared Compliance**: Use `sub-compliance-check` for regulatory alignment
3. **Shared Intake Patterns**: Adapt `sub-intake` structure for your domain
4. **Framework Library**: Add your frameworks to the shared framework registry
5. **Knowledge Base Sharing**: Contribute to shared SECOND-KNOWLEDGE-BRAIN entries

### Contact for Cluster Collaboration

To discuss cluster-level integration or share reusable components:
- GitHub Discussions: https://github.com/skills/health-wellness-cluster/discussions
- Label issues with `cluster: health-wellness`

## Development Status

### Completed Phases
- [x] Phase 0 — Research & Skill Architecture
- [x] Phase 1 — Core Sub-Skills
- [x] Phase 2 — Main Harness + Quality Gates
- [x] Phase 3 — SECOND-KNOWLEDGE-BRAIN Pipeline
- [x] Phase 4 — Testing & Validation
- [x] Phase 5 — Integration & Cross-Skill Wiring

### Active Tasks
- [ ] Expand SECOND-KNOWLEDGE-BRAIN with first live crawl (pending production deployment)
- [ ] Add regression cases from real user runs (ongoing)
- [ ] Cluster collaboration with sibling skills (ongoing)

## Related Root Docs
- `PROJECT-detail.md` — full technical spec
- `PROJECT-DEVELOPMENT-PHASE-TRACKING.md` — phase roadmap
- `SECOND-KNOWLEDGE-BRAIN.md` — self-improving knowledge base
- `README.md` — user-facing documentation
- `CONTRIBUTING.md` — contribution guidelines
- `LICENSE` — MIT License
- `SECURITY.md` — security policy

## Production Readiness Checklist
- [x] All sub-skills implemented with detailed workflows
- [x] Safety and compliance gates functional
- [x] Knowledge base populated with foundational content
- [x] Test scenarios covering happy path, edge cases, and gates
- [x] Documentation complete (README, CONTRIBUTING, SECURITY, LICENSE)
- [x] Open-source licensing and contribution guidelines
- [x] Cross-skill wiring for cluster reusability
- [x] Graceful degradation for offline operation
- [x] Production-grade code quality throughout

**Status**: Ready for open-source release and production deployment.
