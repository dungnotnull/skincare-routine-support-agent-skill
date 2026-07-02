# Skincare Routine Support (Skill #130)

> Builds and evaluates personalized skincare routines by skin type and concern, scoring ingredient suitability and safety against dermatology evidence.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Skill Cluster: Health & Wellness](https://img.shields.io/badge/Cluster-health--wellness-blue.svg)](https://github.com/skills/health-wellness)
[![Phase: Production Ready](https://img.shields.io/badge/Phase-production--ready-green.svg)](https://github.com/skills/skincare-routine-support)

## Overview

This skill provides evidence-based, framework-grounded skincare routine analysis and recommendations. It evaluates skin types, ingredient compatibility, safety considerations, and creates prioritized improvement roadmaps while deferring serious conditions to qualified professionals.

**Key Features**:
- Multi-dimensional scoring with evidence citations (safety, skin-type fit, evidence quality, sequencing, sun protection)
- Framework-grounded analysis (Fitzpatrick Skin Phototype, Baumann Skin Type System, INCI/CIR, Evidence Pyramid)
- Mandatory safety and compliance gates before any recommendations
- Self-improving knowledge base with automated updates
- Graceful degradation for offline operation

## Problem Statement

Consumers often choose skincare products based on marketing hype rather than evidence, leading to:
- Incompatible ingredient combinations that cause irritation
- Missed contraindications (e.g., retinoids during pregnancy)
- Ineffective routines for their specific skin type
- Wasted spending on products that don't work together

This skill addresses these gaps by providing research-first, professionally-grounded routine analysis.

## Use Cases

1. **Acne Routine**: "I have oily, acne-prone skin — build me a routine"
2. **Pregnancy Safety**: "I'm pregnant and using retinol and salicylic acid — is this safe?"
3. **Ingredient Compatibility**: "Can I use vitamin C, retinol and AHA together?"
4. **Serious Condition Referral**: "I have spreading painful red patches with fever"
5. **Degraded Mode**: "Build a routine but no internet" (offline operation)

## Installation

### Prerequisites
- Python 3.8 or higher
- Claude Code or compatible AI agent harness
- Optional: crawl4ai for automated knowledge updates

### Setup

1. Clone this repository:
```bash
git clone https://github.com/skills/skincare-routine-support.git
cd skincare-routine-support
```

2. Install dependencies (optional, for knowledge updater):
```bash
pip install -r requirements.txt
```

3. Verify the skill structure:
```bash
ls -la skills/
ls -la tools/
```

## Usage

### In Claude Code

The skill integrates with Claude Code's skill system. Invoke it when you need skincare routine analysis:

```bash
# In Claude Code prompt
"I have dry, sensitive skin with fine lines — evaluate my routine"
```

The skill will:
1. Collect intake information (skin type, concerns, current routine)
2. Screen for safety contraindications
3. Select appropriate frameworks
4. Research evidence-based options
5. Score each dimension with citations
6. Generate a prioritized improvement roadmap
7. Attach required disclaimers
8. Present a professional analysis

### Knowledge Updates

Run the automated knowledge updater:

```bash
# Dry run (testing)
python tools/knowledge_updater.py --dry-run --verbose

# Live update
python tools/knowledge_updater.py

# Schedule weekly cron (Linux/Mac)
0 2 * * 0 /usr/bin/python3 /path/to/tools/knowledge_updater.py >> /var/log/skincare_knowledge.log 2>&1
```

## Architecture

### Harness Flow

```
/skincare-routine-support (main.md)
   ├── Intake — gather inputs & scope
   ├── [GATE] Safety Screener (BLOCKING)
   ├── Framework Selector — choose world-renowned framework(s)
   ├── Research — WebSearch/WebFetch + SECOND-KNOWLEDGE-BRAIN
   ├── Scoring Engine — multi-dimensional weighted scoring
   ├── Challenge — devil's-advocate assumption review
   ├── Improvement Roadmap — prioritized effort/impact actions
   ├── [GATE] Compliance Check (BLOCKING)
   └── Synthesize — professional deliverable + quality gates
```

### Sub-Skills

| Sub-Skill | Purpose |
|-----------|---------|
| `sub-intake` | Collect structured inputs, scope, and goals |
| `sub-safety-screener` | Screen for red-flag conditions and contraindications |
| `sub-framework-selector` | Choose appropriate evaluation framework(s) |
| `sub-scoring-engine` | Apply multi-dimensional rubric with evidence citations |
| `sub-improvement-roadmap` | Generate prioritized recommendations |
| `sub-compliance-check` | Attach disclaimers and verify regulatory alignment |

### Scoring Dimensions

| Dimension | Weight | Assessment |
|-----------|--------|------------|
| Safety & contraindication screen | 30% | Pregnancy, actives conflicts, allergens, irritation risk |
| Skin-type fit | 20% | Routine matched to Baumann/Fitzpatrick type |
| Ingredient evidence quality | 20% | Actives backed by RCT-grade evidence at effective concentration |
| Routine sequencing & compatibility | 20% | AM/PM order, pH, layering, frequency ramp-up |
| Sun protection & barrier care | 10% | SPF adequacy, barrier support |

**Overall Grade**: A (90+), B (75-89), C (60-74), D (<60)

## Frameworks

The skill uses established, citable frameworks:

- **Fitzpatrick Skin Phototype**: UV response and photodamage risk (Types I-VI)
- **Baumann Skin Type System**: 16 types across oily/dry, sensitive/resistant, pigmented, wrinkled axes
- **INCI & CIR**: Standardized ingredient naming and safety assessments
- **Evidence Pyramid**: RCT > Cohort > Expert for efficacy claims
- **FDA/EU Cosmetics Regulation**: Concentration limits and prohibited substances

## Safety & Compliance

### Safety Gate (Blocking)
The skill stops routine advice if any red flag is identified:
- Urgent medical symptoms (spreading redness + fever, etc.)
- Pregnancy contraindications (retinoids, high BHA)
- Active dermatologic conditions requiring professional care
- Medication interactions
- Known allergies and sensitivities

### Compliance Gate (Blocking)
All outputs include:
- Informational framing (not medical advice)
- Regulatory acknowledgment (FDA, EU, etc.)
- No guaranteed outcomes
- Uncertainty and limitations stated
- Required disclaimers

## Development

### Project Structure

```
skincare-routine-support/
├── CLAUDE.md                 # Project-specific instructions
├── README.md                # This file
├── PROJECT-detail.md        # Technical specification
├── PROJECT-DEVELOPMENT-PHASE-TRACKING.md  # Phase tracking
├── SECOND-KNOWLEDGE-BRAIN.md # Self-improving knowledge base
├── skills/
│   ├── main.md              # Main harness
│   ├── sub-intake.md
│   ├── sub-safety-screener.md
│   ├── sub-framework-selector.md
│   ├── sub-scoring-engine.md
│   ├── sub-improvement-roadmap.md
│   └── sub-compliance-check.md
├── tools/
│   └── knowledge_updater.py # Automated knowledge update pipeline
└── tests/
    └── test-scenarios.md    # End-to-end test scenarios
```

### Testing

Run test scenarios:

```bash
# In Claude Code, run through scenarios in tests/test-scenarios.md
# Each scenario validates harness flow, gates, and output quality
```

### Contributing

Contributions welcome! Please:

1. Read [CONTRIBUTING.md](CONTRIBUTING.md)
2. Fork the repository
3. Create a feature branch
4. Make your changes with tests
5. Submit a pull request

Areas for contribution:
- Additional research papers for knowledge base
- New framework integrations
- Enhanced test scenarios
- Internationalization (region-specific regulations)
- Knowledge updater improvements

### Code Style

- Python: PEP 8
- Markdown: consistent formatting, clear headers
- Comments: explain "why" for complex logic, avoid clutter

## Documentation

- [Technical Specification](PROJECT-detail.md) — Full technical details
- [Phase Tracking](PROJECT-DEVELOPMENT-PHASE-TRACKING.md) — Development progress
- [Test Scenarios](tests/test-scenarios.md) — Validation suite
- [CLAUDE Instructions](CLAUDE.md) — AI agent guidelines

## License

MIT License — see [LICENSE](LICENSE) file for details.

## Disclaimer

**INFORMATIONAL CONTENT ONLY**

The information provided by this skill is for educational and informational purposes only and is not intended as a substitute for professional medical advice, diagnosis, or treatment.

Always seek the advice of your physician, dermatologist, or other qualified health provider with any questions you may have regarding a medical condition or skincare regimen.

No guarantee of results is expressed or implied. Individual responses to skincare ingredients and routines vary. This content does not establish a provider-patient relationship.

For medical concerns, please consult a board-certified dermatologist or qualified healthcare provider.

## Citation

If you use this skill in your work, please cite:

```
Skincare Routine Support (Skill #130). Health & Wellness Cluster.
https://github.com/skills/skincare-routine-support
```

## Acknowledgments

- Frameworks: Fitzpatrick, Baumann, CIR, FDA, EU EC 1223/2009
- Research: PubMed, AAD, CIR, INCIDecoder communities
- Testing: Real user scenarios and regression cases

## Contact

- Issues: https://github.com/skills/skincare-routine-support/issues
- Discussions: https://github.com/skills/skincare-routine-support/discussions

---

**Version**: 1.0.0
**Last Updated**: 2025-01-17
**Status**: Production Ready
