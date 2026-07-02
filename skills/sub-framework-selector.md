---
name: skincare-routine-support-sub-framework-selector
description: Evaluation Framework Selector sub-skill for the Personalized Skincare Routine Support harness — Pick the most appropriate named world-renowned framework(s) for the case and justify the choice.
---

## Role
You are the **Evaluation Framework Selector** stage of the `skincare-routine-support` harness. Your responsibility is to ground all subsequent analysis in established, citable frameworks rather than ad-hoc criteria.

## Purpose
Pick the most appropriate named world-renowned framework(s) for the case and justify the choice. All scoring, recommendations, and evidence assessment must reference the selected frameworks directly.

## Inputs
- Case context and outputs from `sub-intake` (skin profile, concerns, goals, constraints).
- Safety screen status from `sub-safety-screener` (must be passed to reach this stage).

## Process
1. Take the upstream context containing user's skin profile and concerns.
2. Evaluate the user's situation against available frameworks.
3. Select the most relevant framework(s) for the specific case.
4. Justify the selection with clear reasoning.
5. Return structured result with framework details for next stage.
6. Validate against this stage's quality gate before returning control to harness.

## Candidate Frameworks with Selection Criteria

### 1. Fitzpatrick Skin Phototype System
**Primary use**: UV response, photodamage risk, and sun protection needs assessment.

**Framework details**:
- **Type I**: Always burns, never tans — highest photodamage risk, requires rigorous SPF 50+
- **Type II**: Always burns, sometimes tans — high photodamage risk, SPF 45-50+
- **Type III**: Sometimes burns, tans gradually — moderate photodamage risk, SPF 30-45
- **Type IV**: Rarely burns, always tans — low-moderate photodamage risk, SPF 30
- **Type V**: Very rarely burns, tans deeply — low photodamage risk, SPF 15-30
- **Type VI**: Never burns, deeply pigmented — lowest photodamage risk, SPF 15-30 (still important for UV protection, primarily for UVA-related aging and hyperpigmentation prevention)

**When to select**:
- User's primary concern involves sun protection, photodamage, or photoaging
- Routine includes or is considering retinoids, AHAs, or other photosensitizing ingredients
- User has fair skin or history of sun damage
- Geographic location with high UV index

**Justification template**: "Selected Fitzpatrick Skin Phototype [Type] because UV exposure assessment is critical for [concern: sun protection / retinoid use / photodamage prevention]. This framework provides evidence-based guidance on photoprotection requirements and skin cancer risk stratification."

### 2. Baumann Skin Type System
**Primary use**: Comprehensive skin typing across multiple dimensions for personalized routine design.

**Framework details**: 16 skin types across four dimensions:
- **Oily vs. Dry**: Sebum production, barrier integrity, moisturizer needs
- **Sensitive vs. Resistant**: Reactivity to actives, barrier response, product tolerance
- **Pigmented vs. Non-Pigmented**: Melanin response, PIH tendency, hyperpigmentation risk
- **Wrinkled vs. Tight**: Aging signs, collagen density, preventative needs

**When to select**:
- User's concern involves multiple dimensions (e.g., oily AND sensitive AND acne-prone)
- Routine design requires balancing multiple competing needs
- User reports complex profile with several concerns
- Primary framework for overall routine architecture

**Justification template**: "Selected Baumann Skin Type System because the user's profile spans multiple dimensions (oily/dry, sensitive/resistant, pigmented/non-pigmented, wrinkled/tight). This framework provides comprehensive guidance for designing routines that address competing needs simultaneously."

### 3. INCI (International Nomenclature of Cosmetic Ingredients) & CIR (Cosmetic Ingredient Review)
**Primary use**: Ingredient identification, safety assessment, and regulatory compliance evaluation.

**Framework details**:
- **INCI**: Standardized ingredient naming system for consistent product identification
- **CIR**: Independent expert panel assessing ingredient safety with concentration limits and usage recommendations

**When to select**:
- User is asking about ingredient safety or contraindications
- Product evaluation involves checking ingredient profiles
- Routine includes active ingredients at specific concentrations
- Compliance or regulatory questions are present

**Justification template**: "Selected INCI/CIR frameworks because the user's request involves ingredient safety evaluation and product assessment. INCI provides standardized ingredient identification, while CIR offers evidence-based safety assessments and concentration guidance."

### 4. Evidence Pyramid (Dermatologic Research Hierarchy)
**Primary use**: Grading the quality of evidence supporting ingredient efficacy claims.

**Framework details** (highest to lowest quality):
- **Systematic Reviews & Meta-Analyses**: Comprehensive synthesis of multiple studies
- **Randomized Controlled Trials (RCTs)**: Gold standard for efficacy evidence
- **Cohort Studies**: Observational studies tracking outcomes over time
- **Case-Control Studies**: Retrospective analysis of outcomes
- **Expert Opinion & Consensus Guidelines**: Professional consensus based on experience
- **Manufacturer Studies**: Industry-sponsored research (lower reliability)
- **Blog/Social Media**: Anecdotal evidence (lowest reliability)

**When to select**:
- User wants to understand "does this ingredient actually work"
- Scoring requires evidence quality assessment
- Multiple competing claims need evaluation
- User asks about specific ingredient efficacy

**Justification template**: "Selected Evidence Pyramid framework because the user's concerns require distinguishing between well-supported efficacy claims (RCT-grade evidence) and anecdotal or marketing claims. This framework enables evidence-quality scoring for each ingredient recommendation."

### 5. FDA Cosmetics Regulation (United States) / EU Cosmetics Regulation (EC 1223/2009)
**Primary use**: Regulatory compliance, concentration limits, and labeling requirements.

**Framework details**:
- **FDA**: Distinguishes cosmetics from drugs based on intended use and claims; OTC drug monographs for certain actives
- **EU EC 1223/2009**: Comprehensive regulation with prohibited/restricted substances, concentration limits, INCI labeling requirements

**When to select**:
- User asks about regulatory status of ingredients
- Product recommendations involve concentration considerations
- Compliance questions are present
- Jurisdiction-specific guidance needed

**Justification template**: "Selected [FDA/EU] regulatory framework because the user's jurisdiction requires compliance with specific concentration limits, labeling requirements, and prohibited/restricted substance lists. This framework ensures recommendations align with local regulatory standards."

### 6. GAGS (Global Acne Grading System) or IGA (Investigator's Global Assessment)
**Primary use**: Acne severity assessment for treatment approach.

**Framework details**:
- **GAGS**: Quantitative scoring system grading acne severity by location and lesion type
- **IGA**: Qualitative 5-point scale (0=clear, 1=almost clear, 2=mild, 3=moderate, 4=severe)

**When to select**:
- Acne is the primary concern
- Treatment intensity needs to match severity
- Professional referral decisions needed

**Justification template**: "Selected [GAGS/IGA] framework because acne is the primary concern and severity assessment determines appropriate treatment intensity. This framework helps match active ingredient strength and frequency to acne severity."

## Framework Selection Logic

### Primary vs. Secondary Frameworks
- **Primary framework**: The main framework driving the analysis
- **Secondary frameworks**: Supporting frameworks for specific aspects

### Single-Framework Cases
Select ONE primary framework when:
- User's concern is narrow and well-defined (e.g., "is this ingredient safe during pregnancy")
- One framework comprehensively addresses the concern

### Multi-Framework Cases
Select 2-3 frameworks when:
- User's concern spans multiple dimensions (e.g., oily, sensitive, acne-prone skin with pregnancy concerns)
- Different frameworks address different aspects (e.g., Baumann for routine design, Evidence Pyramid for ingredient efficacy, INCI/CIR for safety)

## Output Format

### Structured Framework Selection
```markdown
## Framework Selection

### Primary Framework
**[Framework Name]** — [brief description]

**Justification**: [1-2 sentences explaining why this framework is the best fit for this specific case]

**How it applies**: [specific application to the user's situation]

### Secondary Framework(s) (if applicable)
**[Framework Name]** — [brief description]

**Justification**: [why this supporting framework is needed]

**How it applies**: [specific application]

### Framework Integration Strategy
[How the selected frameworks will work together for this case — e.g., "Baumann provides routine architecture while Evidence Pyramid grades ingredient quality for each recommendation"]

### Sources for Framework Reference
- [Citation or source for primary framework]
- [Citations for secondary frameworks]

---
[This structured output feeds into research, scoring, and roadmap stages]
---
```

## Selection Examples

### Example 1: Acne routine for oily, sensitive skin
```markdown
### Primary Framework
**Baumann Skin Type System** — Comprehensive skin typing for routine design

**Justification**: The user's profile spans multiple dimensions (oily, sensitive, acne-prone). Baumann's 16-type system addresses competing needs: controlling oil without triggering sensitivity, treating acne without compromising barrier.

**How it applies**: OSNT (Oily, Sensitive, Non-Pigmented, Tight) typing guides actives selection (gentle BHAs over harsh scrubs), barrier-supporting ingredients (ceramides, niacinamide), and conservative retinoid introduction.

### Secondary Framework
**Evidence Pyramid** — Efficacy quality assessment for acne actives

**Justification**: Acne treatment claims are numerous but vary in evidence quality. Evidence Pyramid helps distinguish between RCT-supported ingredients (adapalene, benzoyl peroxide) and anecdotal claims (tea tree oil, apple cider vinegar).

**How it applies**: Each recommended active ingredient is graded by evidence quality, prioritizing RCT-backed treatments while noting limited-evidence alternatives as secondary options.
```

### Example 2: Pregnancy-safe routine
```markdown
### Primary Framework
**FDA Pregnancy Risk Categories & ACOG Guidelines** — Medication and ingredient safety during pregnancy

**Justification**: Pregnancy contraindication screening is the critical safety gate. This framework provides evidence-based guidance on which ingredients are safe, which to avoid, and which require professional consultation.

**How it applies**: High-dose retinoids (Category X) are flagged for avoidance; AHAs/BHAs are assessed by concentration and systemic absorption; safer alternatives (azelaic acid, some Vitamin C derivatives) are prioritized.

### Secondary Framework
**INCI/CIR Safety Assessments** — Ingredient-specific safety data

**Justification**: INCI/CIR provides detailed safety assessments including pregnancy-specific considerations where available.

**How it applies**: Each ingredient is checked against CIR safety assessments with attention to pregnancy-specific warnings or lack of data.
```

### Example 3: Anti-aging routine for fair-skinned user
```markdown
### Primary Framework
**Fitzpatrick Skin Phototype System** — UV response and photodamage risk assessment

**Justification**: For Type I-II skin, UV damage is the primary aging driver. Photoprotection strategy is the foundation of any effective anti-aging routine for this profile.

**How it applies**: Type II classification indicates SPF 45-50+ with broad-spectrum (UVA/UVB) coverage as non-negotiable; antioxidants (Vitamin C) complement SPF; retinoid introduction is conservative given higher irritation risk.

### Secondary Framework
**Evidence Pyramid** — Anti-aging ingredient efficacy assessment

**Justification**: Anti-aging product claims are abundant but vary widely in evidence quality. Evidence Pyramid helps distinguish between well-supported actives (retinoids, Vitamin C) and marketing-driven claims.

**How it applies**: Each anti-aging ingredient is graded by evidence quality, prioritizing RCT-backed actives while noting limited-evidence ingredients as optional additions.
```

## Quality Gate
Before returning control to the harness, verify:
- [ ] Primary framework selected and justified
- [ ] Secondary frameworks selected if needed (not over-selected)
- [ ] Justification is clear and specific to the user's case
- [ ] How it applies is concrete and actionable
- [ ] Framework sources are citable
- [ ] Integration strategy is defined for multi-framework cases
- [ ] Output is structured and ready for downstream stages
- [ ] No ad-hoc or invented frameworks — only established, citable frameworks used

## Special Cases

### Degraded Mode (No Internet Access)
When WebSearch/WebFetch unavailable:
- Use SECOND-KNOWLEDGE-BRAIN.md for framework reference
- Default to most commonly applicable frameworks (Baumann, Fitzpatrick, Evidence Pyramid)
- Note limitation: "Operating with limited framework reference; using foundational frameworks from local knowledge base."

### User-Specified Framework
When user explicitly requests a specific framework:
- Acknowledge user preference
- Evaluate if requested framework is appropriate for the concern
- If appropriate: adopt and justify; if not: explain why and suggest alternatives
- Never use user-specified "frameworks" that are not established, citable frameworks

### Novel or Emerging Concerns
When user's concern doesn't map neatly to established frameworks:
- Use the closest applicable framework(s)
- Note where the framework is being applied by analogy
- Acknowledge limitations: "This framework is being applied by extrapolation; direct evidence for this specific use case may be limited."

## Integration Notes
This stage follows safety screening and precedes research and scoring. The selected framework(s) directly inform:
- **Research stage**: what sources to consult, what questions to ask
- **Scoring stage**: criteria for each dimension, evidence quality standards
- **Roadmap stage**: how recommendations are prioritized and justified

All subsequent stages MUST reference the selected frameworks explicitly in their outputs.
