# Trade-off Analysis Matrix Template

Use this template to systematically compare multiple options against weighted criteria.

---

## Decision: [NAME OF DECISION]

**Date**: YYYY-MM-DD
**Decision Owner**: [Name]
**Context**: [One sentence summary]

---

## Step 1: Define Evaluation Criteria

List all criteria that matter for this decision. Not all criteria are equal - assign weights.

| Criterion         | Description                    | Weight (1-10) | Why This Weight?              |
| ----------------- | ------------------------------ | ------------- | ----------------------------- |
| Performance       | Response time, throughput      | 8             | Critical for user experience  |
| Cost              | Initial + ongoing costs        | 7             | Budget constraint of $X/month |
| Team Expertise    | How well team knows technology | 9             | Only 2 months to ship         |
| Scalability       | Ability to handle growth       | 8             | Expecting 10x traffic         |
| Maintainability   | Ease of updates and fixes      | 6             | Standard priority             |
| Security          | Vulnerability risk             | 9             | Handling sensitive data       |
| Time to Implement | Speed to production            | 7             | Market timing important       |
| Vendor Lock-in    | Switching cost                 | 5             | Acceptable for now            |

**Total Weight**: [Sum of weights - use for normalization]

---

## Step 2: Score Each Option

Score each option on each criterion (1-10 scale, where 10 = best).

### Option 1: [NAME]

| Criterion         | Weight | Raw Score (1-10) | Weighted Score | Notes/Justification                  |
| ----------------- | ------ | ---------------- | -------------- | ------------------------------------ |
| Performance       | 8      | 9                | 72             | Benchmarks show <50ms latency        |
| Cost              | 7      | 6                | 42             | $3K/month, within budget             |
| Team Expertise    | 9      | 4                | 36             | Would need 2-3 months learning       |
| Scalability       | 8      | 10               | 80             | Proven to handle our target scale    |
| Maintainability   | 6      | 7                | 42             | Good documentation, active community |
| Security          | 9      | 8                | 72             | SOC 2 certified, penetration tested  |
| Time to Implement | 7      | 5                | 35             | 3 months estimated                   |
| Vendor Lock-in    | 5      | 3                | 15             | Proprietary APIs, hard to migrate    |

**Total Weighted Score**: 394

**Key Strengths**:

- Excellent performance and scalability
- Strong security posture

**Key Weaknesses**:

- Team learning curve is steep
- Significant vendor lock-in risk

---

### Option 2: [NAME]

| Criterion         | Weight | Raw Score (1-10) | Weighted Score | Notes/Justification             |
| ----------------- | ------ | ---------------- | -------------- | ------------------------------- |
| Performance       | 8      | 7                | 56             | Good but not exceptional        |
| Cost              | 7      | 9                | 63             | Open source, $500/month hosting |
| Team Expertise    | 9      | 9                | 81             | Team has 3 years experience     |
| Scalability       | 8      | 7                | 56             | Scales well with proper config  |
| Maintainability   | 6      | 8                | 48             | Team knows it well              |
| Security          | 9      | 7                | 63             | Solid, but needs hardening      |
| Time to Implement | 7      | 9                | 63             | 4 weeks estimated               |
| Vendor Lock-in    | 5      | 9                | 45             | Open source, can self-host      |

**Total Weighted Score**: 475

**Key Strengths**:

- Team expertise means fast implementation
- Low cost and no vendor lock-in
- Quick time to market

**Key Weaknesses**:

- Performance is acceptable but not optimal
- Will require some security hardening

---

### Option 3: [NAME]

| Criterion         | Weight | Raw Score (1-10) | Weighted Score | Notes/Justification               |
| ----------------- | ------ | ---------------- | -------------- | --------------------------------- |
| Performance       | 8      | 8                | 64             | Very good, near Option 1          |
| Cost              | 7      | 8                | 56             | $1.5K/month, good value           |
| Team Expertise    | 9      | 6                | 54             | Similar to tools we know          |
| Scalability       | 8      | 9                | 72             | Proven at scale                   |
| Maintainability   | 6      | 7                | 42             | Standard maintenance burden       |
| Security          | 9      | 9                | 81             | Enterprise-grade security         |
| Time to Implement | 7      | 7                | 49             | 6-8 weeks estimated               |
| Vendor Lock-in    | 5      | 6                | 30             | Some lock-in, but has export APIs |

**Total Weighted Score**: 448

**Key Strengths**:

- Balanced across most criteria
- Excellent security
- Good performance and scalability

**Key Weaknesses**:

- Moderate learning curve
- Middle cost option

---

## Step 3: Visual Comparison

### Score Summary

| Option           | Total Weighted Score | Rank | Cost        | Time to Implement |
| ---------------- | -------------------- | ---- | ----------- | ----------------- |
| Option 1: [Name] | 394                  | 3rd  | $3K/month   | 3 months          |
| Option 2: [Name] | 475                  | 1st  | $500/month  | 4 weeks           |
| Option 3: [Name] | 448                  | 2nd  | $1.5K/month | 6-8 weeks         |

### Radar Chart Visualization (Conceptual)

For each option, plot the raw scores (1-10) on these key dimensions:

```
Option 2 (Winner):
         Performance (7)
                |
Vendor Lock(9) |  Team Expertise (9)
        \      |      /
         \     |     /
          \    |    /
           \   |   /
            \ | /
    Security (7) — Scalability (7)
```

---

## Step 4: Risk Analysis

### Option 1 Risks

| Risk                               | Probability (H/M/L) | Impact (H/M/L) | Mitigation                           |
| ---------------------------------- | ------------------- | -------------- | ------------------------------------ |
| Team struggles with learning curve | H                   | M              | Budget for training, hire consultant |
| Vendor increases pricing           | M                   | M              | Negotiate multi-year contract        |
| Implementation takes longer        | M                   | H              | Run pilot first, adjust timeline     |

### Option 2 Risks

| Risk                            | Probability (H/M/L) | Impact (H/M/L) | Mitigation                                |
| ------------------------------- | ------------------- | -------------- | ----------------------------------------- |
| Performance doesn't meet needs  | L                   | H              | Load test early, have fallback plan       |
| Security incident due to config | M                   | H              | Security audit, hardening checklist       |
| Outgrows capabilities at scale  | M                   | M              | Monitor metrics, plan migration if needed |

### Option 3 Risks

| Risk     | Probability (H/M/L) | Impact (H/M/L) | Mitigation   |
| -------- | ------------------- | -------------- | ------------ |
| [Risk 1] | -                   | -              | [Mitigation] |
| [Risk 2] | -                   | -              | [Mitigation] |

---

## Step 5: Recommendation

### Recommended Option: [NAME]

**Justification**:

Based on the weighted scoring, Option 2 scores highest at 475 points. While it doesn't have the absolute best performance, it excels in the areas most critical for our context:

1. **Team Expertise** (weighted 9): Team can implement in 4 weeks vs 3 months
2. **Cost** (weighted 7): $500/month is 6x cheaper than Option 1
3. **Time to Implement** (weighted 7): Can launch in 4 weeks, hitting our market window

The performance trade-off (score of 7 vs 9) is acceptable because:

- 7/10 still meets our SLA requirements (<100ms response time)
- We can optimize further after launch
- Faster time to market is worth the trade-off

**Key Success Factors**:

- Must complete security hardening (checklist attached)
- Load testing required before launch
- Plan to revisit if we exceed current scale estimates

**Decision Point**: We should commit to Option 2 unless load testing reveals performance issues that can't be resolved.

---

## Step 6: Sensitivity Analysis

What if we change the weights? Does the recommendation change?

**Scenario A**: If Performance weight increases to 10 (and Time to Implement drops to 5)

- Option 1 score increases to 410
- Option 2 score decreases to 461
- **Recommendation remains Option 2**

**Scenario B**: If Team Expertise weight drops to 5 (and Scalability increases to 10)

- Option 1 score increases to 402
- Option 2 score decreases to 457
- **Recommendation remains Option 2**

**Conclusion**: Recommendation is robust across reasonable weight variations.

---

## Step 7: Stakeholder Alignment

| Stakeholder   | Position                   | Concerns                       | Resolution                   |
| ------------- | -------------------------- | ------------------------------ | ---------------------------- |
| CEO           | Supports Option 2          | Worried about performance      | Will monitor metrics weekly  |
| Head of Eng   | Prefers Option 2           | None - aligns with team skills | Supportive                   |
| Security Team | Neutral, leans Option 3    | Option 2 needs hardening       | Will complete security audit |
| Finance       | Strongly supports Option 2 | Cost savings significant       | Aligned                      |

**Consensus Level**: Strong (3 of 4 supportive, 1 neutral with conditions)

---

## Template Notes

### Scoring Guidance

**Raw Scores (1-10)**:

- 10: Exceptional, best in class
- 8-9: Very good, exceeds requirements
- 6-7: Good, meets requirements
- 4-5: Acceptable, meets some requirements with gaps
- 2-3: Poor, significant gaps
- 1: Fails to meet basic requirements

### Weight Guidance

**Weights (1-10)**:

- 9-10: Critical, deal-breaker if not met
- 7-8: Very important, major factor
- 5-6: Important, significant factor
- 3-4: Moderate importance
- 1-2: Nice to have

### Common Pitfalls

1. **All weights are 10**: Forces you to prioritize
2. **Biased scoring**: Have multiple people score independently
3. **Too many criteria**: Keep to 6-10 most important
4. **Ignoring intangibles**: Consider team morale, strategic fit
5. **Analysis paralysis**: Set a decision deadline

---

**Template Version**: 1.0.0
