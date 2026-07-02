# Security Policy

## Supported Versions

Currently supported version: 1.0.0

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly.

### How to Report

**Do NOT** create a public issue.

Instead, send an email to: security@skills.example.com

Include:
- Description of the vulnerability
- Steps to reproduce (if applicable)
- Potential impact
- Suggested fix (if known)

### Response Timeline

- **Acknowledgment**: Within 48 hours
- **Initial Assessment**: Within 1 week
- **Remediation**: As appropriate based on severity
- **Public Disclosure**: After fix is released

### Security Areas

This skill handles health-related information. Key security considerations:

1. **User Privacy**
   - No personal data is stored or transmitted
   - No user identifying information collected
   - All processing is local to the user's environment

2. **Medical Information Safety**
   - Skill provides informational content only
   - No diagnostic capabilities
   - Safety gates prevent inappropriate advice
   - Serious conditions always escalated to professionals

3. **Data Integrity**
   - Knowledge base updates are verified
   - Source URLs are validated
   - Deduplication prevents corruption

4. **Code Execution**
   - Knowledge updater runs in isolated environment
   - No arbitrary code execution
   - Network access limited to specific domains

## Security Best Practices

### For Users

1. **Verify Source**
   - Only use from official repositories
   - Verify checksums if provided
   - Check for unauthorized modifications

2. **Understand Limitations**
   - This is informational content, not medical advice
   - Always consult qualified professionals for medical concerns
   - Do not ignore safety gate recommendations

3. **Offline Operation**
   - Degraded mode uses local knowledge only
   - May not have latest safety information
   - Be conservative when offline

### For Contributors

1. **Code Review**
   - All changes go through pull request review
   - Security-sensitive changes require additional review
   - Test coverage for security-related code

2. **Dependency Management**
   - Regular dependency updates
   - Vulnerability scanning
   - Minimal external dependencies

3. **Knowledge Sources**
   - Only fetch from authoritative sources
   - Validate source authenticity
   - Reject suspicious content

## Vulnerability Types

### Critical
- Safety gate bypass
- Escalation failure for serious conditions
- Knowledge base corruption
- Arbitrary code execution

### High
- Compliance gate bypass
- Missing disclaimers
- Information leakage
- Dependency vulnerabilities

### Medium
- Inadequate error handling
- Logging sensitive information
- Race conditions
- Denial of service

### Low
- Minor information disclosure
- UI inconsistencies
- Documentation issues

## Security Audits

Formal security audits:
- **Last Audit**: Pending
- **Next Audit**: Before 2.0 release
- **Scope**: All code, dependencies, knowledge sources

## Contact

For security questions not related to vulnerability reporting:
- Open an issue with the "security" label
- Use the "security" category in Discussions

---

Thank you for helping keep Skincare Routine Support safe!
