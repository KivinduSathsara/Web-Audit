# Security Risk Assessment and Control Assurance Playbook

Version 1.0 | 31 October 2026 | Portfolio learning resource

A practical workflow for assessing a web application and its supporting infrastructure, recording control evidence, and turning findings into accountable remediation.

**Context:** This is an illustrative portfolio resource developed with AI assistance. The scenario and evidence identifiers are fictional. It does not represent a client engagement, certification, independent audit opinion, or a complete implementation of any external standard.

## 1. Purpose and assessment boundary

Use this playbook to answer: What can go wrong, which business outcomes are affected, what controls work today, and who will address the remaining risk?

Before testing, record:

- Business service, system owner, assessment sponsor and decision-maker.
- In-scope application, cloud account, network boundary, interfaces and external dependencies.
- Data classification and applicable contractual or regulatory obligations, confirmed with the responsible owner.
- Business impact assumptions, service recovery objectives and known exclusions.
- Assessment period, environment, approved test methods and constraints.
- Evidence handling rules and the review or expiry date.

Testing requires the system owner's authorization and an agreed scope. Prefer non-destructive checks and sanitized evidence. Do not include credentials, live tokens, personal records or client documents in public assessment records.

**Example scope:** A fictional customer portal, its identity provider, CI/CD pipeline, database and backup service. A payment processor is a dependency; its internal systems are excluded.

## 2. Responsibilities and decisions

| Role | Responsibility |
| --- | --- |
| Business risk owner | Confirms business impact, funds treatment, and accepts residual risk within delegated authority |
| System / engineering owner | Explains architecture, implements actions and maintains controls |
| Assessor | Records scenarios, tests evidence and explains limitations |
| Security lead | Challenges ratings and recommends treatment priorities |
| Independent reviewer | Checks assessment quality and validates closure evidence |
| Governance forum | Resolves escalations and decisions exceeding the risk owner's authority |

Do not let an implementer alone approve closure of their own high-risk finding. Record the approver, rationale, date and expiry for every risk acceptance.

## 3. Assessment workflow

1. **Prepare:** Confirm scope, architecture, assets, dependencies and business context.
2. **Identify:** Describe threat events, exposure or vulnerabilities, affected assets and consequences.
3. **Assess:** Evaluate inherent risk, then test existing controls before estimating current residual risk.
4. **Treat:** Select avoidance, reduction, sharing/transfer, or acceptance. Record actions, owners, deadlines and dependencies.
5. **Validate:** Retest completed actions and obtain an authorized residual-risk decision.
6. **Monitor:** Reassess when incidents, major releases, new dependencies or material control changes occur.

A useful risk statement is: **Because [condition], [threat event] may affect [asset/service], resulting in [business consequence].**

Avoid vague entries such as "missing MFA." Explain who could exploit the gap, what access they could gain, and why it matters.

## 4. Illustrative rating method

Use a common 12-month assessment horizon. The following ordinal scales and thresholds are local design choices for this example, not NIST-prescribed scoring or a statistical loss model.

### Likelihood

| Score | Anchor |
| --- | --- |
| 1 - Rare | Credible scenario but exceptional preconditions and little observed exposure |
| 2 - Unlikely | Plausible, with several difficult preconditions |
| 3 - Possible | Feasible with meaningful exposure or relevant prior events |
| 4 - Likely | Readily feasible, repeated exposure or closely relevant incidents |
| 5 - Almost certain | Active exploitation or persistent conditions making occurrence highly expected |

Record the evidence and uncertainty behind the chosen level. Do not infer likelihood from vulnerability severity alone.

### Business impact

| Score | Anchor |
| --- | --- |
| 1 - Negligible | Minor internal inconvenience within normal operations |
| 2 - Minor | Limited disruption handled by the service team |
| 3 - Moderate | Material service degradation or recoverable business loss requiring management attention |
| 4 - Major | Extended critical-service disruption or substantial confidentiality, integrity or contractual harm |
| 5 - Severe | Threat to critical business objectives, widespread sensitive-data exposure or prolonged critical outage |

Before operational use, business owners must define measurable local thresholds for downtime, loss, affected records and customer harm. Use the highest justified impact dimension and explain it; do not average away severe consequences.

**Priority score = likelihood x impact:** 1-4 Low; 5-9 Moderate; 10-16 High; 17-25 Critical. This is prioritization on ordinal scales, not a probability, currency amount or percentage.

- **Inherent risk:** Scenario before the selected mitigating controls; state which controls are excluded from this baseline.
- **Current residual risk:** Scenario with controls supported by current evidence.
- **Target residual risk:** Expected state after planned actions, clearly marked as a forecast until retested.

Do not reduce a score simply because a policy exists. Describe how an implemented control changes likelihood or impact. Never convert control test pass rates directly into percentage risk reduction.

## 5. Control assurance checklist

| Area | Assessment question | Example evidence and procedure |
| --- | --- | --- |
| Identity and access | Are privileged accounts restricted and reviewed? | Inspect role assignments and MFA enforcement; sample joiner/mover/leaver cases |
| Change management | Are production changes reviewed and traceable? | Trace sampled changes from ticket to approval, automated checks and deployment record |
| Application security | Are relevant security requirements tested? | Review test scope and results; validate selected findings against authorized test evidence |
| Vulnerability management | Are findings owned and retested? | Inspect inventory coverage, triage rationale, remediation records and retest results |
| Logging and detection | Can high-impact events be detected and investigated? | Inspect log coverage, access restrictions, alert routing and an approved test event |
| Resilience | Can the service recover to its agreed objectives? | Inspect backup protection, restore-test evidence and measured recovery results |
| Third-party risk | Are critical supplier dependencies assessed? | Review service scope, assurance reports, exceptions, contractual responsibilities and exit plans |

For each control, distinguish **design adequacy** (would it address the scenario?) from **operating effectiveness** (did it work during the assessment period?).

Record the population, sample selection, period, evidence identifier, procedure, exceptions and conclusion. Explain coverage limits. A screenshot from today cannot establish that a control operated throughout the previous quarter.

Use conclusions such as effective, partially effective, ineffective, or not tested. Missing evidence means effectiveness is unverified; it does not prove a specific security incident occurred.

## 6. Risk register template

Copy this entry for each distinct scenario:

- **Risk ID / title:**
- **Service, asset and business owner:**
- **Assessment date / period / horizon:**
- **Threat event and exposure:**
- **Business consequence:**
- **Evidence and assumptions:**
- **Existing controls and test conclusions:**
- **Inherent likelihood / impact / score:**
- **Current residual likelihood / impact / score:**
- **Confidence and limitations:**
- **Treatment decision and rationale:**
- **Action owner / milestone / due date:**
- **Target residual risk (forecast):**
- **Approval authority / decision date / acceptance expiry:**
- **Retest result / closure evidence / reviewer:**
- **Next review date / reassessment triggers:**

Keep evidence references in a restricted store when they contain sensitive operational details. Public portfolio examples should contain fictional identifiers only.

## 7. Worked example: privileged access to a fictional portal

**R-001:** Because an administrative account can authenticate without MFA, an attacker with a stolen password could change portal configuration or access customer data.

- **Scope:** Fictional portal administration interface; example assessment date 31 October 2026.
- **Assumptions:** Internet-reachable login, one privileged account, no observed compromise. Business owner judges impact Major.
- **Evidence:** Fictional E-001 identity configuration export; E-002 privileged role inventory; E-003 authorized test record. These are example labels, not attached evidence.
- **Inherent:** Likelihood 4 x impact 4 = 16, High.
- **Existing controls:** Named accounts and login alerts are configured. Privileged MFA is absent. Alert-response effectiveness has not been tested.
- **Current residual:** 4 x 4 = 16, High. Available evidence does not justify a reduction.
- **Treatment:** Engineering owner to enforce phishing-resistant MFA for privileged access, review role assignments and test alert routing.
- **Due date:** Illustrative target 14 November 2026; high-risk acceptance requires the designated business approver.
- **Target residual:** 2 x 4 = 8, Moderate, subject to testing and remaining session-recovery risks.
- **Closure criteria:** Demonstrate MFA enforcement, validate recovery and emergency-access paths, review exceptions and independently retest.
- **Decision rule:** Keep the finding open until evidence supports the target state. A completed ticket alone is insufficient.
- **Reassessment triggers:** Identity-provider migration, privilege-model change, account compromise or control bypass.

The target rating is an assumption for discussion, not a claim that MFA eliminates account compromise.

## 8. Finding and engineering handoff template

**Condition:** What was observed, with period and evidence reference.  
**Criteria:** The applicable approved requirement or agreed control objective.  
**Cause:** Confirmed cause, or explicitly "not yet established."  
**Consequence:** The relevant risk scenario and business impact.  
**Recommendation:** The required outcome, with implementation options agreed with engineering.  
**Management response:** Owner, actions, dependencies, due dates and any disagreement.  
**Validation:** Test procedure, acceptance criteria, reviewer and closure evidence.

A useful handoff gives the engineer a reproducible observation, affected scope, expected security outcome and a way to demonstrate success. Validate fixes in an authorized environment and avoid embedding secrets in tickets.

## 9. Monitoring and quality checks

Example measures, to be agreed with owners:

- Number of overdue High/Critical treatment actions, with age and blocked dependencies.
- Number of accepted High/Critical risks approaching expiry.
- Percentage of privileged accounts covered by enforced MFA; disclose excluded account types.
- Percentage of critical services with a successful restore test within the approved interval.
- Percentage of closed findings independently retested.

Every percentage needs a numerator, denominator, measurement date and exclusions. These measures indicate control coverage or workflow health; they are not direct estimates of total risk reduction.

Before publishing an assessment, check that scores match the stated method, current and target states are separated, evidence supports conclusions, acceptance authority is recorded, and no real client or personal data is exposed.

## 10. Source references and boundaries

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework): a reference for organizing cybersecurity risk management outcomes.
- [NIST SP 800-30 Rev. 1](https://csrc.nist.gov/pubs/sp/800/30/r1/final): guidance for conducting risk assessments.
- [OWASP Web Security Testing Guide](https://owasp.org/projects/web-security-testing-guide): a reference for planning authorized web security testing.

This original playbook uses these as background references. It does not reproduce an official control catalog, claim formal conformance, or provide a verified crosswalk to ISO 27001, COBIT or NIST subcategories. Validate any formal mapping against the applicable edition and organizational context.
