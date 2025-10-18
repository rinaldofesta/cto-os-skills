# Incident Response Playbook

A comprehensive guide for responding to production incidents effectively and consistently.

---

## Incident Severity Levels

### P0 - Critical Incident

**Definition**:

- Complete service outage affecting all customers
- Data breach or security incident
- Data loss or corruption
- Revenue-impacting system failure
- Regulatory violation in progress

**Response Time**: Immediate (within 5 minutes)

**Response Team**:

- Incident Commander (IC)
- On-call engineer(s)
- Engineering manager
- CTO notified
- CEO/COO notified (depending on severity)
- Customer success team (for communication)

**Communication**:

- Update status page immediately
- All-hands Slack channel
- Customer email within 30 minutes
- Hourly updates until resolved

**Example**: Database down, login system compromised, payment processing broken

---

### P1 - High Severity

**Definition**:

- Major feature completely broken
- Significant performance degradation (>50% slower)
- Subset of customers affected (e.g., one region)
- Security vulnerability discovered (actively exploited)

**Response Time**: Within 15 minutes

**Response Team**:

- Incident Commander
- On-call engineer(s)
- Engineering manager notified
- Subject matter experts as needed

**Communication**:

- Update status page
- Incident Slack channel
- Customer communication within 2 hours
- Updates every 2-4 hours

**Example**: Search completely broken, API rate limiting too aggressive, authentication slow

---

### P2 - Medium Severity

**Definition**:

- Non-critical feature impaired
- Performance degradation (10-50% slower)
- Workaround exists
- Small subset of customers affected

**Response Time**: Within 2 hours

**Response Team**:

- On-call engineer
- Domain expert as needed

**Communication**:

- Incident Slack channel
- Status page if customer-visible
- No direct customer communication unless requested

**Example**: Analytics dashboard showing incorrect data, email notifications delayed

---

### P3 - Low Severity

**Definition**:

- Minor issue with minimal customer impact
- Cosmetic bugs
- Internal tooling issues
- Non-urgent security findings

**Response Time**: Next business day

**Response Team**:

- Regular team member
- Assigned during business hours

**Communication**:

- Regular ticket/issue tracking
- No special notifications

**Example**: Typo in UI, minor CSS issue, internal dashboard bug

---

## Incident Response Process

### Phase 1: Detection & Alert (0-5 minutes)

**How Incidents Are Detected**:

1. Automated monitoring alerts (PagerDuty, Datadog, etc.)
2. Customer reports (support tickets, social media)
3. Internal team discovery
4. Security scanning alerts

**First Actions**:

1. ✅ Acknowledge the alert/report
2. ✅ Assess severity (P0/P1/P2/P3)
3. ✅ Page appropriate responders
4. ✅ Join incident war room (Slack, Zoom)

**Tools**:

- PagerDuty/Opsgenie for paging
- Slack incident channel (auto-created)
- Zoom bridge for collaboration
- Shared doc for notes

---

### Phase 2: Triage & Assessment (5-15 minutes)

**Incident Commander Actions**:

1. ✅ Establish war room and communication channels
2. ✅ Assign clear roles:
   - Incident Commander (overall coordination)
   - Technical Lead (investigation and fixes)
   - Communications Lead (internal and external updates)
   - Scribe (documentation)
3. ✅ Gather initial information:
   - What is broken?
   - Since when?
   - How many customers affected?
   - What is the business impact?
4. ✅ Update status page (if customer-facing)
5. ✅ Notify stakeholders based on severity

**Key Questions**:

- Is this an ongoing incident or past event?
- Is customer data at risk?
- Do we need to escalate further?
- Should we enable additional logging/monitoring?

**Tools**:

- Monitoring dashboards (Grafana, Datadog)
- Log aggregation (ELK, Splunk)
- APM tools (New Relic, AppDynamics)

---

### Phase 3: Investigation (15-60 minutes)

**Technical Lead Actions**:

1. ✅ Review recent changes (deployments, config changes)
2. ✅ Check monitoring dashboards for anomalies
3. ✅ Analyze logs and error messages
4. ✅ Identify correlated events
5. ✅ Form hypothesis about root cause
6. ✅ Test hypothesis

**Investigation Checklist**:

- [ ] Recent deployments or changes?
- [ ] External dependencies healthy?
- [ ] Database performance issues?
- [ ] Networking or infrastructure problems?
- [ ] Traffic spike or DDoS?
- [ ] Resource exhaustion (CPU, memory, disk)?
- [ ] Security indicators (unusual access patterns)?

**Common Tools**:

```bash
# Check recent deployments
git log --since="2 hours ago" --oneline

# Check system resources
kubectl top pods
top / htop

# Review logs
tail -f /var/log/application.log
grep "ERROR" logs/* | tail -100

# Check database
SHOW PROCESSLIST;
EXPLAIN ANALYZE query;

# Network checks
ping api.example.com
traceroute api.example.com
curl -v https://api.example.com/health
```

---

### Phase 4: Containment (Parallel with Investigation)

**Goal**: Stop the bleeding, prevent further damage

**Containment Actions** (choose appropriate ones):

1. ✅ Roll back recent deployment
2. ✅ Disable problematic feature (feature flag)
3. ✅ Scale up resources (auto-scaling, manual scaling)
4. ✅ Isolate affected systems
5. ✅ Rate limit or block problematic traffic
6. ✅ Failover to backup systems
7. ✅ Enable maintenance mode (if necessary)

**Decision Tree**:

```
Is there a recent deployment?
├─ Yes → Consider rollback
│         Is rollback safe?
│         ├─ Yes → Rollback
│         └─ No → Forward fix or feature flag disable
└─ No → Continue investigation

Is this a capacity issue?
├─ Yes → Scale up resources
└─ No → Continue investigation

Is this a security incident?
├─ Yes → Follow security incident playbook
│         (separate document)
└─ No → Continue standard process
```

---

### Phase 5: Resolution (Variable time)

**Goal**: Permanently fix the issue

**Resolution Actions**:

1. ✅ Develop and test fix
2. ✅ Deploy fix to production
3. ✅ Verify fix resolves issue
4. ✅ Monitor for recurrence
5. ✅ Confirm with customers if applicable

**Testing Before Deploy**:

- [ ] Fix tested in staging environment
- [ ] Peer reviewed by another engineer
- [ ] Monitoring in place to validate fix
- [ ] Rollback plan prepared

**Verification**:

- [ ] Error rates returned to normal
- [ ] Performance metrics recovered
- [ ] Customer reports resolved
- [ ] No new errors introduced

---

### Phase 6: Recovery & Monitoring (1-24 hours)

**Goal**: Ensure stability and catch any recurrence

**Actions**:

1. ✅ Extended monitoring of fixed systems
2. ✅ Customer communication (resolution + apology)
3. ✅ Update status page to "Resolved"
4. ✅ Review any temporary fixes for permanent solutions
5. ✅ Schedule post-mortem meeting (within 48 hours)

**Monitoring Checklist**:

- [ ] Error rates stable for 2+ hours
- [ ] Performance metrics normal
- [ ] No customer escalations
- [ ] Dependent systems healthy

---

### Phase 7: Post-Mortem (Within 48 hours)

**Goal**: Learn and improve, prevent recurrence

**Post-Mortem Meeting** (60-90 minutes):

1. ✅ Review incident timeline
2. ✅ Identify root cause(s)
3. ✅ Discuss what went well
4. ✅ Discuss what could be improved
5. ✅ Create action items with owners and deadlines
6. ✅ Share learnings with broader team

**Post-Mortem Document Sections**:

1. Summary (2-3 sentences)
2. Timeline (chronological events)
3. Root Cause Analysis
4. What Went Well
5. What Went Poorly
6. Action Items (with owners and deadlines)
7. Lessons Learned

**Example Template**: See `post-mortem-template.md`

**Important**: Post-mortems are **blameless**. Focus on systems and processes, not individuals.

---

## Communication Guidelines

### Internal Communication

**Incident Slack Channel**:

- Created automatically for P0/P1 incidents
- Named: `#incident-2024-02-15-database-outage`
- Pinned message with key info and links
- All incident-related discussion happens here
- Archived after resolution for future reference

**Status Updates**:

- IC provides regular updates (frequency based on severity)
- Template: "**UPDATE [TIME]**: [What we know] | [What we're doing] | [ETA for next update]"
- Example: "**UPDATE 2:45 PM**: Database connection pool exhausted. Scaling up connections. Next update in 15 minutes."

**Escalation**:

- P0: Immediate notification to CTO, CEO
- P1: Notification to engineering manager, CTO within 15 min
- P2: Notification to engineering manager within 2 hours
- P3: Regular ticket notification

---

### External Communication

**Status Page Updates**:

- Update within 10 minutes of P0/P1 incident
- Be transparent but concise
- Avoid technical jargon
- Provide ETAs if known (or "Investigating")

**Status Page Language**:

- **Investigating**: "We are aware of an issue affecting [service]. Our team is investigating."
- **Identified**: "We have identified the issue and are implementing a fix."
- **Monitoring**: "A fix has been implemented and we are monitoring the results."
- **Resolved**: "The issue has been resolved. All services are operating normally."

**Customer Email** (for P0 incidents):

- Sent within 30 minutes
- Acknowledge issue and apologize
- Provide current status
- Explain impact
- Give ETA or "working urgently to resolve"
- Provide contact for questions

**Template**:

```
Subject: Service Disruption - [Date]

Dear [Customer],

We are writing to inform you of a service disruption affecting [service/feature].

WHAT HAPPENED:
Starting at [time], customers have experienced [impact description].

CURRENT STATUS:
Our team has [identified/resolved] the issue and [is implementing/has implemented] a fix.
We expect full service restoration by [ETA or "within the next X hours"].

IMPACT:
Approximately [number or %] of [users/requests/features] were affected.
[Specific impact on customer's usage if known]

NEXT STEPS:
- We are monitoring the situation closely
- We will send an update when fully resolved
- We will conduct a full post-mortem and share findings

We sincerely apologize for this disruption and any impact to your business.

If you have any questions, please contact [support email/phone].

[Name]
[Title]
```

---

## Common Incident Types & Runbooks

### Type 1: Application Crash / High Error Rate

**Symptoms**:

- HTTP 500 errors
- Application pods restarting
- Error logs spiking

**Common Causes**:

- Recent deployment with bugs
- Memory leak
- Unhandled exception
- Database connection issues

**Runbook**:

1. Check recent deployments → rollback if appropriate
2. Check application logs for stack traces
3. Check resource usage (memory, CPU)
4. Check database connection pool
5. Scale up if resource exhaustion
6. Deploy fix or rollback

---

### Type 2: Database Performance Issues

**Symptoms**:

- Slow queries
- High database CPU
- Connection pool exhaustion
- Timeouts

**Common Causes**:

- Missing indexes
- Expensive query
- Lock contention
- Too many connections

**Runbook**:

1. Identify slow queries (SHOW PROCESSLIST)
2. Check for missing indexes
3. Check for long-running transactions
4. Scale up database if resource exhaustion
5. Kill problematic queries if safe
6. Optimize queries or add indexes

---

### Type 3: External Dependency Failure

**Symptoms**:

- Errors from third-party API
- Timeouts on external calls
- Features dependent on external service broken

**Common Causes**:

- Third-party service outage
- API rate limits hit
- Network issues
- Authentication expired

**Runbook**:

1. Check third-party status page
2. Verify API credentials still valid
3. Check rate limit headers
4. Enable circuit breaker if available
5. Graceful degradation or queue requests
6. Contact vendor support if necessary

---

### Type 4: Infrastructure / Cloud Issues

**Symptoms**:

- Servers unreachable
- High network latency
- Services not starting
- Unusual cloud provider alerts

**Common Causes**:

- Cloud provider outage
- Network misconfiguration
- Auto-scaling failure
- Resource limits hit

**Runbook**:

1. Check cloud provider status page
2. Verify infrastructure configuration
3. Check billing/quota limits
4. Failover to another region if possible
5. Engage cloud provider support
6. Scale up or provision new resources

---

### Type 5: Security Incident

**Symptoms**:

- Unauthorized access detected
- Unusual traffic patterns
- Security alerts firing
- Customer reports of suspicious activity

**Immediate Actions**:

1. ⚠️ Isolate affected systems
2. ⚠️ Preserve evidence (logs, snapshots)
3. ⚠️ Revoke compromised credentials
4. ⚠️ Engage security team / CISO
5. ⚠️ Follow security incident playbook (separate document)
6. ⚠️ Prepare for possible customer notification (legal review)

**Do NOT**:

- ❌ Delete evidence
- ❌ Communicate publicly without legal/PR review
- ❌ Make major changes without documentation

---

## Roles and Responsibilities

### Incident Commander (IC)

**Responsibilities**:

- Own the incident end-to-end
- Coordinate all responders
- Make decisions on escalation, communication, actions
- Ensure documentation
- Run post-mortem

**Skills Needed**:

- Clear communication
- Calm under pressure
- Decision-making ability
- Technical understanding (not necessarily expert)

**NOT responsible for**:

- Fixing the technical issue (that's Technical Lead)
- Writing all updates (delegate to Communications Lead)

---

### Technical Lead

**Responsibilities**:

- Lead technical investigation
- Coordinate technical team members
- Propose and implement fixes
- Provide technical updates to IC

**Skills Needed**:

- Deep technical expertise
- Debugging and troubleshooting
- System architecture knowledge

---

### Communications Lead

**Responsibilities**:

- Write and publish status page updates
- Draft customer communications
- Coordinate with support team
- Notify stakeholders

**Skills Needed**:

- Clear writing
- Customer empathy
- Judgment on appropriate communication

---

### Scribe

**Responsibilities**:

- Document timeline in real-time
- Record key decisions
- Track action items
- Prepare initial post-mortem draft

**Skills Needed**:

- Attention to detail
- Ability to keep up with fast-moving situation

---

## Tools and Setup

### Required Tools

**Incident Management**:

- PagerDuty, Opsgenie, or similar
- Automated escalation policies
- On-call rotation schedule

**Communication**:

- Slack (with incident bot for auto-channels)
- Zoom (dedicated incident bridge)
- Status page (StatusPage.io, custom, etc.)

**Monitoring & Observability**:

- APM (New Relic, Datadog, etc.)
- Log aggregation (ELK, Splunk, etc.)
- Metrics and dashboards (Grafana, etc.)
- Alerting (PagerDuty, Opsgenie, etc.)

**Documentation**:

- Runbook repository (Notion, Confluence, Git)
- Post-mortem repository
- Incident timeline tool (optional: Jeli, Blameless)

---

### Slack Incident Bot

**Auto-create incident channels**:

```
/incident declare p0 "Database connection pool exhausted"

→ Creates #incident-2024-02-15-database
→ Invites on-call team
→ Posts pinned message with:
   - Severity
   - Declared by
   - Declared at
   - Links to dashboards, runbooks
   - Template for status updates
```

**Helpful commands**:

- `/incident status` - Post status update
- `/incident roles` - Assign roles (IC, TL, Comms)
- `/incident escalate` - Page additional responders
- `/incident resolve` - Mark incident resolved

---

## Preparation and Training

### Quarterly Game Days

**Purpose**: Practice incident response in controlled environment

**Format** (2-3 hours):

1. Facilitator introduces scenario
2. Team responds as if real incident
3. No advance warning of specific scenario
4. Facilitator injects complications
5. Debrief and discuss learnings

**Sample Scenarios**:

- Database primary fails over to replica
- DDoS attack on API endpoint
- Accidentally deleted production data
- Security breach detected
- Major cloud provider outage

---

### Runbook Maintenance

**Frequency**: Review quarterly, update after incidents

**Checklist**:

- [ ] Contact information up to date
- [ ] Tools and access documented
- [ ] Procedures tested within last 6 months
- [ ] Screenshots and examples current
- [ ] Links work and point to correct resources

---

### New Team Member Onboarding

**Incident Response Training** (during first month):

1. Review this playbook
2. Shadow on-call engineer
3. Participate in game day exercise
4. Assigned as secondary on-call before primary

---

## Metrics and Continuous Improvement

### Track These Metrics

| Metric                             | Target   | Current |
| ---------------------------------- | -------- | ------- |
| Time to Acknowledge (P0)           | <5 min   |         |
| Time to Mitigation (P0)            | <30 min  |         |
| Time to Resolution (P0)            | <2 hours |         |
| Incidents per month                | <5       |         |
| Repeat incidents (same root cause) | 0        |         |
| Post-mortem completion rate        | 100%     |         |
| Action item completion rate        | >80%     |         |

---

### Monthly Incident Review

**Attendees**: Engineering leadership, IC rotation

**Agenda**:

1. Review incident trends
2. Discuss recurring themes
3. Review action item completion
4. Identify systemic improvements needed
5. Update runbooks and procedures

---

**Playbook Version**: 1.0.0
**Last Updated**: [Date]
**Owner**: [CTO / Engineering Manager]
**Next Review**: [Date]
