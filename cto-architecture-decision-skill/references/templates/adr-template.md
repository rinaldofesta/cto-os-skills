# Architecture Decision Record Template

## ADR Format

Use this template to document any significant architectural or technology decision.

---

## ADR-[NUMBER]: [SHORT TITLE OF SOLVED PROBLEM]

**Status**: [Proposed | Accepted | Deprecated | Superseded by ADR-XXX]

**Date**: YYYY-MM-DD

**Decision Makers**: [Names/roles of people involved in decision]

**Consulted**: [Stakeholders who provided input]

---

### Context

What is the issue we're facing? What factors are driving this decision?

- Describe the problem or opportunity
- Current situation and constraints
- Business/technical drivers
- Timeline pressures
- Budget constraints
- Team capabilities
- Existing system context

**Example**:

> Our monolithic application is becoming difficult to scale. Deployment frequency has dropped from weekly to monthly due to risk and complexity. Different teams are blocked waiting for others to finish their parts. We need to serve 10x traffic in the next 12 months.

---

### Decision

What decision did we make? Be specific.

**We will [ACTION]**

**Example**:

> We will migrate from our Rails monolith to a microservices architecture using the strangler fig pattern over 18 months. We will extract 5 key domains into separate services: Authentication, Billing, Notifications, Reporting, and Core Product.

---

### Alternatives Considered

What other options did we evaluate? Why did we reject them?

#### Option 1: [Name]

**Description**: [What is this option]

**Pros**:

- Advantage 1
- Advantage 2

**Cons**:

- Disadvantage 1
- Disadvantage 2

**Why rejected**: [Reasoning]

#### Option 2: [Name]

[Same format as above]

#### Option 3: Do Nothing

Always consider the "do nothing" option.

**Pros**:

- No migration cost
- No new risks

**Cons**:

- Problem remains and may worsen
- Opportunity cost

**Why rejected**: [Reasoning]

---

### Consequences

What are the implications of this decision? Be honest about trade-offs.

#### Positive Consequences

- Benefit 1: [Describe impact]
- Benefit 2: [Describe impact]
- Benefit 3: [Describe impact]

#### Negative Consequences

- Trade-off 1: [Describe impact and mitigation]
- Trade-off 2: [Describe impact and mitigation]
- Risk 1: [Describe risk and mitigation plan]

#### Neutral Consequences

- Change 1: [Things that are different but neither good nor bad]

---

### Implementation Plan

High-level plan for implementing this decision.

**Phase 1** (Months 1-3):

- Step 1
- Step 2

**Phase 2** (Months 4-9):

- Step 1
- Step 2

**Phase 3** (Months 10-18):

- Step 1
- Step 2

**Success Criteria**:

- Metric 1: [How we measure success]
- Metric 2: [How we measure success]

**Rollback Plan**:

- If X happens, we will Y
- Point of no return: [When decision becomes irreversible]

---

### Technical Details

Optional section for technical specifics.

**Architecture Diagram**: [Link or embed]

**Key Technologies**:

- Technology 1: [Purpose]
- Technology 2: [Purpose]

**Integration Points**: [How this fits with existing systems]

**Data Migration**: [If applicable]

**Security Considerations**: [Any security implications]

---

### References

- [Document or link 1]
- [Document or link 2]
- [Similar decision in industry]
- [Research or benchmarking data]

---

### Notes

Any additional context, updates, or lessons learned can be added here over time.

**Update YYYY-MM-DD**: [Add updates as implementation proceeds]

---

## ADR Numbering

- Start at ADR-001 and increment sequentially
- Never reuse numbers
- Keep ADRs even if deprecated (mark status as "Deprecated" or "Superseded")

## ADR Storage

Store ADRs in your code repository:

```
docs/architecture/decisions/
  ADR-001-database-selection.md
  ADR-002-microservices-adoption.md
  ADR-003-api-design-standard.md
```

## When to Write an ADR

Write an ADR when:

- Decision impacts system architecture
- Decision is costly to reverse
- Multiple options exist with trade-offs
- Decision affects multiple teams
- Future teams will need context

Don't write ADRs for:

- Trivial decisions
- Decisions easily reversible
- Purely local/implementation details
- Temporary/experimental choices

---

**Template Version**: 1.0.0
