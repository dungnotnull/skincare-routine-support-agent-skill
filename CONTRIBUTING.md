# Contributing to Skincare Routine Support

Thank you for your interest in contributing to Skincare Routine Support (Skill #130)!

## How to Contribute

### Areas for Contribution

We welcome contributions in the following areas:

1. **Knowledge Base Expansion**
   - Add new research papers to SECOND-KNOWLEDGE-BRAIN.md
   - Expand framework documentation
   - Add ingredient safety data

2. **Framework Integration**
   - Add new evaluation frameworks (e.g., COSMOS, JSAE)
   - Enhance existing framework implementations
   - Add region-specific regulatory frameworks

3. **Test Scenarios**
   - Add new test scenarios based on real user runs
   - Expand regression test cases
   - Add edge case testing

4. **Internationalization**
   - Add region-specific compliance requirements
   - Translate documentation (maintain English as primary)
   - Add localized regulatory references

5. **Tooling**
   - Enhance knowledge_updater.py
   - Add automated testing
   - Improve documentation generation

### Contribution Workflow

1. **Fork the Repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/skincare-routine-support.git
   cd skincare-routine-support
   ```

2. **Create a Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make Your Changes**
   - Write clear, concise code
   - Add comments for complex logic
   - Update tests if applicable
   - Update documentation

4. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Brief description of changes"
   ```

5. **Push and Create Pull Request**
   ```bash
   git push origin feature/your-feature-name
   ```
   Then create a pull request on GitHub.

### Code Style Guidelines

#### Python (tools/knowledge_updater.py)
- Follow PEP 8
- Use type hints where appropriate
- Add docstrings for functions
- Maximum line length: 100 characters

#### Markdown (skills/, docs/)
- Use consistent header levels
- Use bullet lists for itemized information
- Maintain formatting consistency
- Include metadata frontmatter for skill files

#### Comments
- Explain "why" not "what"
- Avoid obvious comments
- Use inline comments for complex logic only

### Testing

Before submitting a pull request:

1. **Run Test Scenarios**
   - Manually verify test scenarios in tests/test-scenarios.md
   - Ensure all pass criteria are met

2. **Verify Harness Flow**
   - Test safety gate with red-flag conditions
   - Test compliance gate with various inputs
   - Verify degraded mode (offline operation)

3. **Test Knowledge Updater**
   ```bash
   python tools/knowledge_updater.py --dry-run --verbose
   ```

### Documentation

When adding features:
- Update README.md if user-facing
- Update PROJECT-detail.md for technical changes
- Add inline documentation for complex logic
- Update CLAUDE.md if behavior changes

### Pull Request Guidelines

In your pull request, describe:
1. **What** you changed
2. **Why** you changed it
3. **How** you tested it
4. **Any** documentation updates needed

### Review Process

Maintainers will review your pull request for:
- Code quality and style
- Test coverage
- Documentation completeness
- Alignment with project goals
- Safety and compliance considerations

Response time: Typically within 1-2 weeks.

## Community Guidelines

### Be Respectful
- Use inclusive language
- Assume good intentions
- Give constructive feedback

### Focus on Safety
- This skill deals with health information
- Prioritize safety over features
- Flag potential safety issues
- When uncertain, be conservative

### Evidence-Based
- Cite sources for claims
- Use peer-reviewed research when available
- Distinguish evidence grades
- Acknowledge limitations

## Getting Help

- **Documentation**: See README.md, PROJECT-detail.md
- **Issues**: Check existing issues or create a new one
- **Discussions**: Use GitHub Discussions for questions

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to Skincare Routine Support!
