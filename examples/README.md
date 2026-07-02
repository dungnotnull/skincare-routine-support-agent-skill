# Examples — Skincare Routine Support (Skill #130)

This directory contains example inputs and outputs to demonstrate the skill's capabilities.

## Example Structure

Each example includes:
1. **Input**: User query or request
2. **Context**: Additional information provided during intake
3. **Output**: Skill's analysis and recommendations (key sections)
4. **Notes**: What this example demonstrates

## Examples

### Example 1: Acne Routine for Oily, Sensitive Skin

**File**: `example-1-acne-routine.md`

**Demonstrates**: Full harness flow with framework selection, scoring, and roadmap for acne-prone skin.

### Example 2: Pregnancy Safety Check

**File**: `example-2-pregnancy-safety.md`

**Demonstrates**: Safety gate triggering for pregnancy contraindications, appropriate escalation.

### Example 3: Ingredient Compatibility

**File**: `example-3-ingredient-compatibility.md`

**Demonstrates**: Compatibility analysis for multiple active ingredients, pH considerations, scheduling.

### Example 4: Anti-Aging for Dry Skin

**File**: `example-4-anti-aging-dry.md`

**Demonstrates**: Framework selection for anti-aging concerns, SPF recommendations, barrier support.

### Example 5: Degraded Mode (Offline)

**File**: `example-5-degraded-mode.md`

**Demonstrates**: Graceful degradation using local knowledge base, conservative recommendations.

## Using These Examples

1. **For Understanding**: Review examples to understand how the skill processes different requests
2. **For Testing**: Use example inputs to test skill installation and configuration
3. **For Development**: Reference examples when extending or modifying the skill
4. **For Documentation**: See expected output formats and quality standards

## Example Outputs

Each example output includes:

### Intake Summary
- Request type
- Skin profile (type, sensitivity, concerns)
- Current routine (if evaluating)
- Goals and constraints
- Safety screen indicators

### Safety Screen Result
- PASSED or BLOCKING status
- Yellow flags (if any)
- Escalation guidance (if red flag triggered)

### Framework Selection
- Primary framework with justification
- Secondary frameworks (if applicable)
- How frameworks apply to the case

### Scoring Results
- Dimension-by-dimension scores
- Evidence citations
- Overall letter grade
- Strengths and improvement areas

### Improvement Roadmap
- Prioritized recommendations (quick wins first)
- Effort/impact matrix
- Implementation steps
- Timeline and expectations

### Compliance Information
- Disclaimer
- Regulatory acknowledgment
- Uncertainty and limitations

## Note on Privacy

These examples use simulated or anonymized data. No real personal health information is included.

## Contributing Examples

To add new examples:
1. Create a new markdown file: `example-N-name.md`
2. Follow the example structure above
3. Include realistic but anonymized data
4. Demonstrate a specific skill capability
5. Update this README with the new example

For contribution guidelines, see `CONTRIBUTING.md` in the root directory.
