---
name: skincare-routine-support-sub-scoring-engine
description: Scoring Engine sub-skill for the Personalized Skincare Routine Support harness — Apply the multi-dimensional rubric to produce weighted scores with evidence citations for each dimension.
---

## Role
You are the **Scoring Engine** stage of the `skincare-routine-support` harness. Your responsibility is to produce evidence-based, quantified assessments that the user and downstream stages can act on.

## Purpose
Apply the multi-dimensional rubric to produce weighted scores with evidence citations for each dimension. Scoring makes analysis concrete, traceable, and comparable.

## Inputs
- Case context from `sub-intake` (skin profile, concerns, goals, constraints).
- Selected framework(s) from `sub-framework-selector`.
- Research findings from WebSearch/WebFetch and SECOND-KNOWLEDGE-BRAIN.

## Process
1. Take the upstream context including framework(s) and research data.
2. Score each dimension 0-100 using the rubrics below.
3. Cite at least one source or framework reference for each score.
4. Compute weighted total and map to letter grade.
5. Document scoring rationale with evidence links.
6. Return structured result for next stage.
7. Validate against this stage's quality gate before returning control to harness.

## Scoring Rubric by Dimension

### Dimension 1: Safety & Contraindication Screen (30% weight)
**What is assessed**: Pregnancy considerations, active ingredient conflicts, allergens, irritation risk, medication interactions, cumulative exposure.

**Scoring Criteria**:
| Score Range | Criteria |
|-------------|----------|
| 90-100 | No contraindications identified; ingredients appropriate for health status; no known conflicts; cumulative exposure within safe limits; allergens absent or disclosed |
| 75-89 | Minor concerns only; no contraindications; conflicts manageable with modifications; allergens disclosed and avoidable; cumulative exposure acceptable |
| 60-74 | Moderate concerns present; one or more avoidable contraindications; some conflicts requiring modification; allergen risk requires patch testing |
| 0-59 | Significant safety concerns; active contraindications present; unavoidable conflicts; high cumulative exposure; undisclosed allergens |

**Scoring Elements** (each contributes to overall score):
- **Pregnation/lactation status**: Are all ingredients pregnancy-safe if applicable? (15 points)
- **Active conflicts**: Do actives conflict (e.g., retinoid + AHA + benzoyl peroxide)? (15 points)
- **Allergen profile**: Are common allergens present or is product fragrance-free/hypoallergenic? (10 points)
- **Irritation risk**: Is pH, concentration, and combination appropriate for skin type? (10 points)
- **Cumulative exposure**: Does routine layer multiple actives excessively? (10 points)
- **Medication interactions**: Are potential interactions with current medications flagged? (10 points)
- **Concentration limits**: Are ingredients within FDA/EU/other jurisdiction limits? (10 points)
- **Barrier impact**: Does routine support or compromise barrier function? (10 points)

**Evidence Sources to Cite**:
- CIR safety assessments for specific ingredients
- FDA pregnancy risk categories
- Drug interaction databases (for medication conflicts)
- Published studies on ingredient combinations and irritation
- Baumann Skin Type System (sensitivity assessment)

**Example Score Output**:
```markdown
### Safety & Contraindication Screen: 82/100 (weighted 30% = 24.6)

**Scoring breakdown**:
- Pregnancy/lactation: 15/15 (all ingredients pregnancy-safe per ACOG guidelines)
- Active conflicts: 10/15 (retinoid + Vitamin C is compatible; would avoid adding AHA simultaneously)
- Allergen profile: 10/10 (fragrance-free, known allergens absent)
- Irritation risk: 10/10 (pH appropriate for sensitive skin, conservative concentrations)
- Cumulative exposure: 10/10 (two actives only, appropriate frequency)
- Medication interactions: 10/10 (no medications reported)
- Concentration limits: 10/10 (all ingredients within FDA OTC limits)
- Barrier impact: 7/10 (includes ceramide support but retinoid may temporarily compromise barrier)

**Key citations**:
- ACOG Practice Bulletin: Medications in pregnancy (https://www.acog.org)
- CIR Safety Assessment: Niacinamide (https://www.cir-safety.org)
- "Retinoid and antioxidant combination therapy" (Journal of Cosmetic Dermatology, 2022)

**Concerns to address**:
- Retinoid may cause temporary barrier compromise — ensure moisturizer use and gradual introduction
- Consider adding barrier-supporting ingredients if irritation occurs
```

### Dimension 2: Skin-Type Fit (20% weight)
**What is assessed**: How well the routine matches the user's Baumann and/or Fitzpatrick classification.

**Scoring Criteria**:
| Score Range | Criteria |
|-------------|----------|
| 90-100 | Routine precisely tailored to skin type; oiliness/dryness addressed; sensitivity respected; pigmentation needs met |
| 75-89 | Routine generally appropriate; minor mismatches present; skin type generally addressed |
| 60-74 | Routine partially aligned; some elements mismatched for skin type; may cause suboptimal results |
| 0-59 | Routine poorly matched; major elements inappropriate for skin type |

**Scoring Elements**:
- **Oiliness/dryness match**: Does routine address sebum production appropriately? (25 points)
- **Sensitivity respect**: Are products chosen for sensitive/resistant profile? (25 points)
- **Pigmentation consideration**: Does routine address or avoid exacerbating pigmentation? (25 points)
- **Aging approach**: Are anti-aging ingredients appropriate for wrinkle/tight profile? (25 points)

**Evidence Sources to Cite**:
- Baumann Skin Type System (16-type classification)
- Fitzpatrick Skin Phototype (UV response, photodamage risk)
- Published studies on skin type and ingredient response

**Example Score Output**:
```markdown
### Skin-Type Fit: 78/100 (weighted 20% = 15.6)

**Scoring breakdown**:
- Oiliness/dryness match: 20/25 (gel moisturizer appropriate for oily skin; may need lighter formulation in summer)
- Sensitivity respect: 22/25 (fragrance-free, gentle actives chosen; retinoid requires cautious introduction)
- Pigmentation consideration: 18/25 (niacinamide helps with hyperpigmentation but Vitamin C may cause mild irritation)
- Aging approach: 18/25 (retinoid appropriate for fine lines; may want to add peptide for collagen support)

**Key citations**:
- Baumann, L. (2006). "The Skin Type Solution" — OSNT subtype characteristics
- Fitzpatrick, T.B. (1988). "The validity and practicality of sun-reactive skin types I-VI" — UV response patterns

**Framework alignment**: Baumann OSNT (Oily, Sensitive, Non-Pigmented, Tight) — routine addresses oil control and sensitivity while incorporating anti-aging actives.

**Optimization suggestions**:
- Consider lighter moisturizer base for humid months
- Add Vitamin C gradually to assess sensitivity tolerance
- Consider peptide or growth factor addition for collagen support
```

### Dimension 3: Ingredient Evidence Quality (20% weight)
**What is assessed**: Are active ingredients backed by RCT-grade evidence at effective concentrations?

**Scoring Criteria**:
| Score Range | Criteria |
|-------------|----------|
| 90-100 | All key actives RCT-backed at effective concentrations; robust evidence for primary concern |
| 75-89 | Most actives evidence-backed; primary concern addressed by RCT evidence; some secondary ingredients with weaker evidence |
| 60-74 | Key actives have mixed evidence; some RCT support but not at optimal concentration; anecdotal support for some recommendations |
| 0-59 | Limited or no evidence for key ingredients; relies primarily on anecdote or marketing claims |

**Scoring Elements**:
- **Primary concern evidence**: Is the main concern addressed by RCT-backed ingredients? (30 points)
- **Concentration adequacy**: Are ingredients at effective concentrations per studies? (25 points)
- **Vehicle/formulation**: Is the delivery system appropriate for ingredient stability/absorption? (25 points)
- **Evidence quality for all actives**: Are all actives graded by evidence pyramid? (20 points)

**Evidence Sources to Cite**:
- RCTs from dermatology journals (JAAD, JID, British Journal of Dermatology)
- Systematic reviews and meta-analyses
- CIR efficacy assessments
- Published concentration-effect studies

**Example Score Output**:
```markdown
### Ingredient Evidence Quality: 85/100 (weighted 20% = 17.0)

**Scoring breakdown**:
- Primary concern evidence: 28/30 (acne: adapalene [RCT Grade A], benzoyl peroxide [RCT Grade A], niacinamide [RCT Grade B])
- Concentration adequacy: 23/25 (niacinamide 5% effective per studies; benzoyl peroxide 2.5-5% effective; adapalene 0.1% optimal)
- Vehicle/formulation: 22/25 (adapalene in stable base; Vitamin C needs proper pH for stability — verify product formulation)
- Evidence quality for all actives: 12/20 (retinol Grade B; some supportive ingredients lack robust evidence)

**Key citations**:
- "Adapalene 0.1% gel in acne treatment" (JAAD RCT, 2020)
- "Niacinamide 5% for barrier improvement" (International Journal of Cosmetic Science, 2019)
- "Vitamin C stability in cosmetic formulations" (Journal of Cosmetic Science, 2021)

**Evidence quality by ingredient**:
| Ingredient | Evidence Level | Key Source |
|-------------|----------------|------------|
| Adapalene | RCT Grade A | JAAD 2020 |
| Benzoyl Peroxide | RCT Grade A | Cochrane Review 2018 |
| Niacinamide 5% | RCT Grade B | Int J Cosmet Sci 2019 |
| Retinol 0.3% | Cohort Grade B | J Cosmet Dermatol 2022 |
| Vitamin C 15% | Limited | Brand-funded study |
| Ceramides | RCT Grade B | Brit J Dermatol 2020 |

**Concerns**:
- Vitamin C evidence is limited; consider RCT-backed alternative (ferulic acid combination)
- Some supportive ingredients lack robust evidence but are low-risk
```

### Dimension 4: Routine Sequencing & Compatibility (20% weight)
**What is assessed**: AM/PM order appropriateness, pH considerations, layering compatibility, frequency and ramp-up plans.

**Scoring Criteria**:
| Score Range | Criteria |
|-------------|----------|
| 90-100 | Optimal sequencing; pH-appropriate layering; compatible combinations; appropriate frequency with ramp-up plan |
| 75-89 | Generally good sequencing; minor pH/compatibility issues; appropriate frequency |
| 60-74 | Some sequencing problems; pH conflicts present; incompatible combinations; frequency too aggressive |
| 0-59 | Poor sequencing; incompatible combinations; frequency too high; no ramp-up plan |

**Scoring Elements**:
- **Layering order**: Are products applied in optimal order (thinnest to thickest, water to oil)? (20 points)
- **pH compatibility**: Do product pH levels work together (e.g., acidifying cleanser before Vitamin C)? (25 points)
- **Ingredient compatibility**: Do ingredients support or conflict (e.g., retinoid + AHA may be too irritating)? (25 points)
- **Frequency appropriateness**: Is use frequency appropriate for skin type and actives used? (15 points)
- **Ramp-up plan**: Is there a gradual introduction plan for new actives? (15 points)

**Evidence Sources to Cite**:
- Published studies on ingredient interactions and pH effects
- Dermatology guidelines on retinoid introduction
- Cosmetic chemistry references on layering and pH

**Example Score Output**:
```markdown
### Routine Sequencing & Compatibility: 88/100 (weighted 20% = 17.6)

**Scoring breakdown**:
- Layering order: 19/20 (cleanser → treatment → moisturizer → SPF; correct thinnest-to-thickest)
- pH compatibility: 24/25 (low-pH cleanser before actives is optimal; verify Vitamin C pH 3.0-3.5)
- Ingredient compatibility: 23/25 (retinol + niacinamide compatible; would avoid adding AHA on same night)
- Frequency appropriateness: 13/15 (retinol 3x weekly appropriate for starter; benzoyl peroxide daily is acceptable)
- Ramp-up plan: 9/15 (retinol ramp-up specified but timeline unclear)

**Key citations**:
- "Optimal sequencing for topical skincare" (Journal of Cosmetic Dermatology, 2021)
- "pH effects on Vitamin C stability and absorption" (International Journal of Pharmaceutics, 2020)
- "Retinoid introduction protocols" (JAAD Patient Education, 2019)

**Routine sequence analysis**:
```
AM: Cleanser (pH 5.5) → Vitamin C (pH 3.2) → Moisturizer → SPF 50
   ✓ Good pH progression; Vitamin C after cleansing is optimal
PM: Cleanser (pH 5.5) → Retinol (3x/week) or Niacinamide (other nights) → Moisturizer
   ✓ Alternate night schedule prevents over-irritation
   ✓ Retinol not layered with AHA — good for compatibility
```

**Optimizations**:
- Specify 4-week retinol ramp-up: week 1 (1x), week 2 (2x), week 3 (3x)
- Consider adding hydrating serum before retinol on dry nights
- Document product pH values to verify compatibility
```

### Dimension 5: Sun Protection & Barrier Care (10% weight)
**What is assessed**: SPF adequacy for Fitzpatrick type, UVA/UVB coverage, barrier-supporting ingredients.

**Scoring Criteria**:
| Score Range | Criteria |
|-------------|----------|
| 90-100 | SPF 30-50+ appropriate for phototype; broad-spectrum UVA/UVB; daily use specified; barrier support present |
| 75-89 | SPF 30+ broad-spectrum; mostly daily use; some barrier support |
| 60-74 | SPF 15-30 or incomplete broad-spectrum; inconsistent daily use; minimal barrier support |
| 0-59 | SPF <15 or no SPF; no broad-spectrum; no daily use plan; barrier-compromising ingredients |

**Scoring Elements**:
- **SPF level appropriateness**: Is SPF level adequate for Fitzpatrick type? (30 points)
- **UVA/UVB coverage**: Is SPF broad-spectrum? (25 points)
- **Daily use commitment**: Is daily SPF use specified? (25 points)
- **Barrier support**: Does routine include ceramides, fatty acids, humectants? (20 points)

**Evidence Sources to Cite**:
- Fitzpatrick Skin Phototype UV risk assessment
- FDA/U.S. Dermatology SPF recommendations
- Published studies on ceramides and barrier repair

**Example Score Output**:
```markdown
### Sun Protection & Barrier Care: 92/100 (weighted 10% = 9.2)

**Scoring breakdown**:
- SPF level appropriateness: 28/30 (SPF 50 for Fitzpatrick Type II — optimal for high photodamage risk)
- UVA/UVB coverage: 25/25 (broad-spectrum confirmed; UVA-PF 20+)
- Daily use commitment: 25/25 (daily AM SPF specified with reapplication guidance)
- Barrier support: 14/20 (ceramides present in moisturizer; consider adding fatty acid-rich oil)

**Key citations**:
- "Fitzpatrick phototype and SPF recommendations" (Photodermatology, 2020)
- "Broad-spectrum SPF and UVA protection" (FDA Sunscreen Monograph, 2019)
- "Ceramide barrier repair in sensitive skin" (British Journal of Dermatology, 2021)

**Fitzpatrick alignment**:
- Type II (always burns, sometimes tans): SPF 50 is optimal per AAD guidelines
- Broad-spectrum ensures UVA protection for photoaging prevention
- Daily use critical for retinoid users (increased photosensitivity)

**Barrier elements**:
- Ceramides in PM moisturizer ✓
- Niacinamide for barrier support ✓
- Consider adding: squalane or jojoba oil for lipid reinforcement
```

## Weighted Total and Letter Grade Calculation

**Weighted total formula**:
```
Total = (Safety × 0.30) + (Skin-Type × 0.20) + (Evidence × 0.20) + (Sequencing × 0.20) + (SPF/Barrier × 0.10)
```

**Letter grade mapping**:
| Total Score | Letter Grade |
|-------------|--------------|
| 90-100 | A — Excellent |
| 75-89 | B — Good |
| 60-74 | C — Fair |
| 0-59 | D — Poor |

**Example**:
```
Safety: 82/100 × 0.30 = 24.6
Skin-Type: 78/100 × 0.20 = 15.6
Evidence: 85/100 × 0.20 = 17.0
Sequencing: 88/100 × 0.20 = 17.6
SPF/Barrier: 92/100 × 0.10 = 9.2
Total: 84.0/100 → Grade: B (Good)
```

## Output Format

### Structured Scoring Result
```markdown
## Skincare Routine Analysis — Scoring Results

### Overall Grade: [Letter] ([Total]/100)

### Dimension Scores

#### 1. Safety & Contraindication Screen: [Score]/100 (weighted 30% = [Weighted Score])
[Detailed breakdown with citations]

#### 2. Skin-Type Fit: [Score]/100 (weighted 20% = [Weighted Score])
[Detailed breakdown with citations]

#### 3. Ingredient Evidence Quality: [Score]/100 (weighted 20% = [Weighted Score])
[Detailed breakdown with citations]

#### 4. Routine Sequencing & Compatibility: [Score]/100 (weighted 20% = [Weighted Score])
[Detailed breakdown with citations]

#### 5. Sun Protection & Barrier Care: [Score]/100 (weighted 10% = [Weighted Score])
[Detailed breakdown with citations]

### Summary of Strengths
- [List areas scoring 80+]

### Areas for Improvement
- [List areas scoring <75]

### Evidence Quality Summary
| Dimension | Evidence Level | Primary Sources |
|-----------|----------------|-----------------|
| [Dimension] | [RCT/Cohort/Expert] | [Citations] |

### Key Citations
[Numbered list of all sources cited across dimensions]

---
[This structured output feeds into challenge stage and roadmap]
---
```

## Quality Gate
Before returning control to the harness, verify:
- [ ] All five dimensions scored
- [ ] Each score has breakdown and rationale
- [ ] Each score cites at least one source or framework
- [ ] Weighted total calculated correctly
- [ ] Letter grade mapped appropriately
- [ ] Strengths and improvement areas identified
- [ ] Evidence quality summarized by dimension
- [ ] Output is structured and ready for challenge stage
- [ ] No scores invented without justification
- [ ] All claims backed by framework or research citation

## Special Cases

### Degraded Mode (No Internet Access)
When WebSearch/WebFetch unavailable:
- Use SECOND-KNOWLEDGE-BRAIN.md for evidence citations
- Be conservative with evidence quality grades
- Note limitation: "Operating with limited research access; evidence grades based on local knowledge base only."

### Incomplete Information
When user hasn't provided sufficient data for scoring:
- Score available dimensions fully
- Flag unavailable dimensions as "insufficient data"
- Note in output: "Score partial due to missing [information]; complete intake needed for full scoring."

### Conflicting Evidence
When sources conflict:
- Present both perspectives with scores
- Grade certainty: "High certainty" (consistent RCTs), "Moderate certainty" (some conflicting data), "Low certainty" (limited or conflicting evidence)
- Recommend conservative approach when evidence conflicts

## Integration Notes
This stage follows framework selection and research. The scored output directly informs:
- **Challenge stage**: scores and evidence grades are stress-tested
- **Roadmap stage**: improvement areas become prioritized recommendations
- **Final synthesis**: scores and grades are presented in the professional deliverable
