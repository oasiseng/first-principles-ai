# 30-Minute AI Safety Self-Assessment

Answer each question with **Yes / No / Partial**. Any **No** in a high-impact context should block deployment until resolved.

## 1) Human authority is non-negotiable
- Is there a reliable human override/kill switch for this system?
- Are high-impact decisions reviewed by a trained human before irreversible action?
- Is there an appeals process for affected users?

## 2) Safety scales with capability
- Have you defined capability thresholds and linked safeguards?
- Are higher-capability systems subject to stronger testing and access controls?
- Is deployment scope limited by risk tier?

## 3) Transparency is the default
- Can users clearly tell they are interacting with AI?
- Are system limitations and uncertainty communicated in plain language?
- Can you explain key decisions to affected users?

## 4) Harm has owners
- Is there a named accountable owner for this system in production?
- Is there an incident commander and escalation contact list?
- Do contracts/vendor integrations preserve accountability?

## 5) Test before you trust
- Did the system pass pre-deployment safety evaluations with documented thresholds?
- Are adversarial/jailbreak tests part of the release gate?
- Is there continuous post-deployment monitoring with alerting?

## 6) Honesty is structural, not aspirational
- Does the system avoid presenting uncertain outputs as certain facts?
- Are confidence levels and evidence boundaries visible to users?
- Are deceptive UX patterns explicitly prohibited and tested for?

## 7) Principles evolve; rights don't
- Is the framework versioned with a changelog and rationale for updates?
- Are privacy, dignity, autonomy, and non-discrimination treated as fixed constraints?
- Does your governance process include public reasoning for major changes?
