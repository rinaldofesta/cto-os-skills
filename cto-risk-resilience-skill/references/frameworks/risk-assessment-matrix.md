# Risk Assessment Matrix Framework

A systematic approach to identifying, assessing, and prioritizing technical and operational risks.

---

## Risk Assessment Process

### Step 1: Identify Risks

Brainstorm potential risks across all categories. Use the checklist below as a starting point.

---

### Risk Categories Checklist

#### 1. Security Risks

**Access & Authentication**:

- [ ] Weak password policies
- [ ] No multi-factor authentication (MFA)
- [ ] Over-privileged accounts
- [ ] Shared credentials
- [ ] Inadequate access reviews
- [ ] No session timeout enforcement

**Data Protection**:

- [ ] Unencrypted data at rest
- [ ] Unencrypted data in transit
- [ ] Sensitive data in logs
- [ ] No data classification scheme
- [ ] Inadequate data backup
- [ ] No data loss prevention (DLP)

**Application Security**:

- [ ] SQL injection vulnerabilities
- [ ] Cross-site scripting (XSS)
- [ ] Cross-site request forgery (CSRF)
- [ ] Insecure dependencies
- [ ] No security testing in CI/CD
- [ ] Hardcoded secrets in code

**Network Security**:

- [ ] No firewall rules
- [ ] Open ports exposed to internet
- [ ] No network segmentation
- [ ] Unmonitored network traffic
- [ ] No DDoS protection
- [ ] Insecure APIs

**Third-Party Risks**:

- [ ] Unvetted vendors
- [ ] No vendor security assessments
- [ ] Excessive vendor access
- [ ] No vendor SLA monitoring
- [ ] Supply chain vulnerabilities

---

#### 2. Availability & Reliability Risks

**Infrastructure**:

- [ ] Single points of failure
- [ ] No redundancy for critical systems
- [ ] Inadequate capacity planning
- [ ] No auto-scaling
- [ ] Aging hardware/infrastructure
- [ ] No geographic distribution

**Operations**:

- [ ] Manual deployment processes
- [ ] No automated testing
- [ ] Inadequate monitoring
- [ ] No alerting thresholds defined
- [ ] Unclear on-call procedures
- [ ] No incident response plan

**Performance**:

- [ ] Slow response times
- [ ] Database performance issues
- [ ] Inefficient queries
- [ ] Resource exhaustion (CPU, memory, disk)
- [ ] No performance testing
- [ ] No capacity monitoring

**Recovery**:

- [ ] No disaster recovery plan
- [ ] Untested backup procedures
- [ ] Undefined RTO/RPO
- [ ] No failover capability
- [ ] Data loss potential
- [ ] Long recovery times

---

#### 3. Compliance & Legal Risks

**Data Privacy**:

- [ ] GDPR non-compliance
- [ ] CCPA non-compliance
- [ ] Inadequate privacy policy
- [ ] No data subject rights processes
- [ ] Insufficient consent management
- [ ] No data retention policy

**Industry Regulations**:

- [ ] HIPAA violations (healthcare)
- [ ] PCI DSS gaps (payment data)
- [ ] SOX issues (public companies)
- [ ] Industry-specific regulations

**Contractual**:

- [ ] SLA violations
- [ ] Breach of customer contracts
- [ ] Non-compliance with terms of service
- [ ] Intellectual property issues

**Certifications**:

- [ ] No SOC 2 certification (B2B SaaS)
- [ ] No ISO 27001 certification
- [ ] No PCI certification (handling payments)
- [ ] Missing required certifications for target market

---

#### 4. Operational Risks

**Process Risks**:

- [ ] No change management process
- [ ] Inadequate code review
- [ ] No deployment checklist
- [ ] Unclear escalation procedures
- [ ] No documentation standards
- [ ] Poor communication channels

**Human Risks**:

- [ ] Key person dependency (bus factor)
- [ ] Inadequate training
- [ ] No backup for critical roles
- [ ] High team turnover
- [ ] Burnout indicators
- [ ] Insufficient staffing

**Technical Debt**:

- [ ] Outdated dependencies
- [ ] Legacy code with no owner
- [ ] Lack of tests
- [ ] Complex, unmaintainable code
- [ ] Architecture doesn't scale
- [ ] No refactoring time allocated

---

#### 5. Business Continuity Risks

**Dependencies**:

- [ ] Critical vendor lock-in
- [ ] Single cloud provider
- [ ] Third-party API dependencies
- [ ] Open source library risks
- [ ] Payment processor dependency
- [ ] Email/communication service dependency

**Financial**:

- [ ] Budget overruns
- [ ] Unexpected cost spikes
- [ ] Insufficient reserves for incidents
- [ ] Contract penalties at risk

**Reputational**:

- [ ] Customer trust erosion
- [ ] Negative press from incidents
- [ ] Competitive disadvantage
- [ ] Loss of market position

---

## Step 2: Assess Each Risk

For each identified risk, complete this assessment:

### Risk Assessment Template

**Risk ID**: R-001
**Risk Name**: [Short descriptive name]
**Category**: [Security / Availability / Compliance / Operational / Business]
**Identified By**: [Name]
**Date Identified**: [Date]

---

#### Description

[Detailed description of the risk]

**Example**: "Production database has no automated backups. If database is corrupted or deleted, we could lose all customer data with no recovery option."

---

#### Probability Assessment

**How likely is this risk to occur?**

Select one:

⬜ **High (5)**: Very likely, could happen anytime

- Occurs frequently (monthly or more)
- Conditions are already present
- Historical pattern of occurrence

⬜ **Medium-High (4)**: Likely to occur

- Occurs occasionally (quarterly)
- Some conditions are present
- Industry precedent exists

⬜ **Medium (3)**: Possible, but not certain

- Could occur (annually)
- Requires specific circumstances
- Happens but infrequently

⬜ **Medium-Low (2)**: Unlikely but possible

- Rare (every few years)
- Would require multiple failures
- Few precedents

⬜ **Low (1)**: Very unlikely

- Extremely rare (once in 5+ years)
- Would require highly unusual circumstances
- No known precedents

**Probability Score**: [1-5]

**Justification**: [Why you chose this score]

---

#### Impact Assessment

**What would happen if this risk occurred?**

Select one:

⬜ **Critical (5)**: Catastrophic business impact

- Complete service outage >4 hours
- Major data breach or loss
- Regulatory violations with large fines
- Existential threat to company
- Revenue loss >$1M or >10% monthly revenue
- Customer trust severely damaged

⬜ **High (4)**: Severe impact

- Partial outage or major degradation
- Significant data exposure
- Compliance violations
- Revenue loss $100K-$1M or 5-10% monthly revenue
- Major customer dissatisfaction
- Significant remediation cost

⬜ **Medium (3)**: Moderate impact

- Minor outage or degradation (<1 hour)
- Limited data exposure
- Contract violations
- Revenue loss $10K-$100K or 1-5% monthly revenue
- Customer complaints
- Moderate remediation effort

⬜ **Medium-Low (2)**: Minor impact

- Brief disruption (<30 min)
- Internal systems affected
- Process inefficiency
- Revenue loss <$10K
- Few customer complaints
- Small remediation effort

⬜ **Low (1)**: Minimal impact

- No service disruption
- No customer impact
- Internal inconvenience only
- No revenue loss
- Easily fixed

**Impact Score**: [1-5]

**Justification**: [Why you chose this score]

---

#### Risk Score Calculation

```
Risk Score = Probability × Impact

Score Range: 1-25

High Risk (15-25): Immediate action required
Medium Risk (6-14): Plan mitigation within 90 days
Low Risk (1-5): Monitor and address opportunistically
```

**Calculated Risk Score**: [1-25]

---

#### Existing Controls

**What controls are currently in place to prevent or detect this risk?**

**Preventive Controls** (stop it from happening):

- [Control 1]
- [Control 2]

**Detective Controls** (detect when it happens):

- [Control 1]
- [Control 2]

**Responsive Controls** (respond when it happens):

- [Control 1]
- [Control 2]

**Control Effectiveness**: [Effective / Partially Effective / Ineffective / None]

---

#### Mitigation Strategy

**If this risk has a score ≥6, define mitigation:**

**Recommended Actions**:

1. [Action 1] - [Owner] - [Timeline]
2. [Action 2] - [Owner] - [Timeline]
3. [Action 3] - [Owner] - [Timeline]

**Estimated Cost**: $[Amount] or [Engineer time]

**Risk After Mitigation**:

- Probability: [New score]
- Impact: [New score]
- Residual Risk Score: [New score]

**Mitigation Status**: [Not Started / In Progress / Completed]

---

## Step 3: Prioritize Risks

### Risk Matrix

Plot all risks on this matrix:

```
IMPACT →
   5  |  10  |  15  |  20  |  25
   4  |   8  |  12  |  16  |  20
   3  |   6  |   9  |  12  |  15
   2  |   4  |   6  |   8  |  10
   1  |   2  |   3  |   4  |   5
   ─────────────────────────────
   1     2     3     4     5
          ← PROBABILITY

Risk Zones:
🔴 Red (15-25): Critical - Address immediately
🟡 Yellow (6-14): Important - Plan mitigation within 90 days
🟢 Green (1-5): Low - Monitor and address opportunistically
```

---

### Priority 1: Critical Risks (Score 15-25)

**Action Required**: Address immediately (within 30 days)

**Example Risk Profile**:

- High probability + High impact
- Medium-high probability + Critical impact
- Could cause existential damage to business

**Typical Examples**:

- No database backups
- Known security vulnerability actively exploited
- Single point of failure in revenue-critical system
- Imminent compliance deadline unmet

---

### Priority 2: High Risks (Score 10-14)

**Action Required**: Plan mitigation (within 90 days)

**Example Risk Profile**:

- Medium probability + High impact
- High probability + Medium impact

**Typical Examples**:

- No disaster recovery plan
- Outdated dependencies with known vulnerabilities
- No monitoring on production systems
- Key person dependency

---

### Priority 3: Medium Risks (Score 6-9)

**Action Required**: Plan mitigation (within 6 months)

**Example Risk Profile**:

- Low probability + High impact
- Medium probability + Medium impact
- High probability + Low impact

**Typical Examples**:

- Manual deployment process
- Limited test coverage
- No automated security scanning
- Technical debt in non-critical systems

---

### Priority 4: Low Risks (Score 1-5)

**Action Required**: Monitor, address opportunistically

**Example Risk Profile**:

- Any low impact scenarios
- Very low probability scenarios

**Typical Examples**:

- Minor technical debt
- Cosmetic security issues
- Process inefficiencies
- Non-critical system failures

---

## Step 4: Create Risk Register

Maintain an ongoing risk register (spreadsheet or tool):

| Risk ID | Risk Name                   | Category     | Probability | Impact | Score | Owner         | Status      | Mitigation Deadline |
| ------- | --------------------------- | ------------ | ----------- | ------ | ----- | ------------- | ----------- | ------------------- |
| R-001   | No database backups         | Availability | 4           | 5      | 20    | DBA           | In Progress | 2024-02-28          |
| R-002   | SQL injection vulnerability | Security     | 3           | 5      | 15    | Security Team | Not Started | 2024-03-15          |
| R-003   | Key engineer departure risk | Operational  | 3           | 4      | 12    | Eng Manager   | In Progress | 2024-04-30          |
| R-004   | No SOC 2 certification      | Compliance   | 2           | 4      | 8     | CTO           | Planned     | 2024-09-30          |

---

## Step 5: Review and Update

### Review Cadence

**Monthly**:

- Review high/critical risks
- Update status of mitigation efforts
- Add newly identified risks

**Quarterly**:

- Full risk register review
- Reassess probability and impact scores
- Reprioritize based on changes
- Present to executive team

**Annually**:

- Comprehensive risk assessment
- Board-level review
- Update risk management strategy

---

## Example Risk Assessments

### Example 1: Production Database Has No Backups

**Risk ID**: R-001
**Category**: Availability / Business Continuity
**Identified By**: DevOps Team
**Date**: 2024-01-15

**Description**: Production PostgreSQL database has no automated backup system. If database is corrupted, deleted, or hardware fails, all customer data would be permanently lost.

**Probability**: 4 (Medium-High)

- Database corruption happens
- Human error is common
- No safeguards in place
- Matter of when, not if

**Impact**: 5 (Critical)

- Complete data loss
- Business cannot operate
- Regulatory violations
- Company reputation destroyed
- Potential lawsuits

**Risk Score**: 4 × 5 = 20 (CRITICAL 🔴)

**Existing Controls**: None

**Mitigation Strategy**:

1. Implement automated daily backups with 30-day retention (CTO, Feb 15)
2. Set up point-in-time recovery (PITR) (DevOps Lead, Feb 20)
3. Test backup restoration monthly (DevOps, ongoing)
4. Implement backup monitoring and alerting (DevOps Lead, Feb 25)

**Estimated Cost**: $500/month storage + 40 hours engineering time

**Risk After Mitigation**:

- Probability: 1 (automated system, low failure rate)
- Impact: 2 (can recover with minutes of data loss)
- Residual Risk Score: 2 (LOW 🟢)

**Status**: In Progress (50% complete)

---

### Example 2: No Multi-Factor Authentication (MFA)

**Risk ID**: R-005
**Category**: Security
**Identified By**: Security Audit
**Date**: 2024-01-20

**Description**: Admin accounts and production systems accessible with password only. No MFA required. Phishing or compromised credentials could give attacker full access.

**Probability**: 3 (Medium)

- Phishing is common
- Password reuse is common
- Credentials leaked in breaches
- Has happened to similar companies

**Impact**: 5 (Critical)

- Complete system compromise possible
- Customer data at risk
- Regulatory violations
- Reputational damage
- Major remediation cost

**Risk Score**: 3 × 5 = 15 (CRITICAL 🔴)

**Existing Controls**:

- Password complexity requirements (partial)
- Rate limiting on login attempts (partial)

**Control Effectiveness**: Partially Effective (passwords alone are insufficient)

**Mitigation Strategy**:

1. Enforce MFA for all admin accounts (Security Team, Feb 28)
2. Enforce MFA for production system access (DevOps, Feb 28)
3. Offer optional MFA for all users (Product Team, Mar 31)
4. Implement MFA for VPN access (IT, Feb 20)

**Estimated Cost**: $5/user/month for MFA service + 60 hours implementation

**Risk After Mitigation**:

- Probability: 1 (MFA significantly reduces successful compromise)
- Impact: 3 (breach still possible but much harder)
- Residual Risk Score: 3 (LOW 🟢)

**Status**: Planned (starting Feb 1)

---

### Example 3: Single Cloud Provider Dependency

**Risk ID**: R-012
**Category**: Business Continuity
**Identified By**: CTO
**Date**: 2024-01-25

**Description**: Entire infrastructure runs on AWS. If AWS has regional outage or account suspension, business cannot operate. No backup cloud provider.

**Probability**: 2 (Medium-Low)

- AWS outages are rare but happen
- Account suspension unlikely but possible
- Regional failures occur occasionally

**Impact**: 5 (Critical)

- Complete service outage
- No immediate recovery option
- Could last hours or days
- Significant revenue loss

**Risk Score**: 2 × 5 = 10 (HIGH 🟡)

**Existing Controls**:

- Multi-AZ deployment within AWS (partial)
- Good relationship with AWS account team (minimal)

**Control Effectiveness**: Partially Effective (doesn't address AWS-level issues)

**Mitigation Strategy**:

1. Implement multi-region failover within AWS (Q2 2024)
2. Evaluate multi-cloud strategy (Q3 2024)
3. Create runbooks for cloud migration (Q3 2024)
4. Quarterly DR tests including AWS failover scenarios (ongoing)

**Estimated Cost**: $30K/month additional infrastructure + 6 months engineering time

**Risk After Mitigation**:

- Probability: 1 (multi-region significantly reduces risk)
- Impact: 3 (can failover with minimal disruption)
- Residual Risk Score: 3 (LOW 🟢)

**Status**: Planned (roadmapped for Q2)

---

## Risk Communication

### Monthly Risk Report to Executive Team

**Format**: 1-page summary

**Sections**:

1. **Risk Summary**:

   - Critical risks: [count]
   - High risks: [count]
   - Medium risks: [count]

2. **Top 3 Risks** (by score):

   - [Risk name]: Score [X], Status [Y]

3. **Completed Mitigations This Month**:

   - [Risk name]: Mitigation completed, score reduced from [X] to [Y]

4. **New Risks Identified**:

   - [Risk name]: Score [X], mitigation planned

5. **Budget/Resources Needed**:
   - $[amount] for [purpose]
   - [FTEs] for [period]

---

### Quarterly Risk Report to Board

**Format**: 3-5 slides in board deck

**Slides**:

1. **Risk Landscape**: Heat map of all risks
2. **Top Risks**: Detail on top 3-5 critical risks
3. **Mitigation Progress**: Completed and in-progress
4. **Trends**: Are we getting more or less risky over time?
5. **Ask**: Resources, approvals, or guidance needed

---

**Framework Version**: 1.0.0
**Last Updated**: [Date]
**Owner**: [CTO / Risk Manager]
