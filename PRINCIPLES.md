# First Principles for AI Safety (v1.0.0)

This one-page set is designed to be memorable, auditable, and implementation-ready.

## 1) Human authority is non-negotiable
**Principle:** AI systems must preserve meaningful human oversight for decisions that affect rights, access, safety, or life outcomes.

**Directive:** Build kill switches, not autopilots.

**What breaks when violated:** Irreversible decisions are made without legitimate human review, appeal, or override.

## 2) Safety scales with capability
**Principle:** Safeguards must increase with capability, autonomy, and potential impact.

**Directive:** Tie controls to capability thresholds.

**What breaks when violated:** Frontier-capability systems receive baseline controls that are inadequate for high-severity risks.

## 3) Transparency is the default
**Principle:** People must know when AI is involved and what limits apply.

**Directive:** Make the AI obvious.

**What breaks when violated:** Users cannot calibrate trust, detect failure modes, or contest decisions.

## 4) Harm has owners
**Principle:** Every production AI system must have named accountable owners.

**Directive:** Name the owner before deployment.

**What breaks when violated:** Responsibility diffuses across teams and vendors, preventing remediation.

## 5) Test before you trust
**Principle:** Safety evaluation is required before release and throughout operation.

**Directive:** No evaluation, no deployment.

**What breaks when violated:** Harms accumulate in production before organizations detect and respond.

## 6) Honesty is structural, not aspirational
**Principle:** AI must not deceive users or misrepresent confidence, identity, evidence, or intent.

**Directive:** Surface uncertainty by design.

**What breaks when violated:** Users make high-stakes decisions based on fabricated or overconfident outputs.

## 7) Principles evolve; rights don't
**Principle:** Framework details should update with technology while preserving fixed human-rights constraints.

**Directive:** Version policies, anchor rights.

**What breaks when violated:** Either protections erode under rapid iteration or controls become obsolete.

---

## Specificity cascade (required for each principle)

- **Value:** Normative intent (e.g., human authority).
- **Criteria:** What must be true in deployment.
- **Indicators:** Quantifiable success/failure thresholds.
- **Observables:** Concrete checks, artifacts, and logs.

Each principle in `principles.yaml` maps to this chain.
