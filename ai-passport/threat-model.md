# AI Passport Threat Model (Conceptual)

This threat model identifies plausible risks for a human-owned personal intelligence layer. It is not exhaustive and should be revised alongside implementation details and deployment context. See also [architecture.md](./architecture.md) and [principles.md](./principles.md).

---

## 1) Device theft
**Description:** An attacker obtains physical possession of the personal device.

**Why it matters ethically:** Physical loss can become identity loss if personal context and authority are exposed.

**Possible mitigations:** Hardware-backed key protection, rate-limited unlock attempts, local wipe thresholds, secure backup/recovery workflows.

**Open questions:** How to balance recovery usability with strong anti-theft controls?

---

## 2) Cloud model leakage
**Description:** Sensitive prompts or derived personal context leak through cloud logs, training pipelines, or third-party infrastructure.

**Why it matters ethically:** Private thought and identity signals can be appropriated beyond user intent.

**Possible mitigations:** Data minimization, selective redaction, jurisdiction-aware routing, strict retention controls, model-provider contracts.

**Open questions:** How should users verify model-provider data handling claims in practice?

---

## 3) Prompt injection
**Description:** Untrusted content manipulates model behavior to exfiltrate memory or trigger unauthorized actions.

**Why it matters ethically:** Consent is bypassed through adversarial language, undermining autonomy.

**Possible mitigations:** Input provenance tagging, policy guardrails independent of model output, high-risk action confirmations.

**Open questions:** What measurable thresholds define safe autonomy for tool-enabled agents?

---

## 4) Malicious tools/agents
**Description:** Integrated tools or agents abuse granted permissions or contain hidden harmful behavior.

**Why it matters ethically:** Delegation without accountability can produce invisible harms.

**Possible mitigations:** Capability sandboxing, least-privilege scopes, signed tool manifests, continuous permission review.

**Open questions:** What governance model best certifies third-party agent behavior without centralizing control?

---

## 5) Unauthorized memory access
**Description:** Internal components, plugins, or attackers access local memory outside allowed policies.

**Why it matters ethically:** Memory is identity-bearing; unauthorized access can reshape or exploit personhood.

**Possible mitigations:** Fine-grained access policies, encryption at rest/in use where feasible, auditable access logs, anomaly alerts.

**Open questions:** How can non-technical users meaningfully audit memory access events?

---

## 6) Identity spoofing
**Description:** Attackers impersonate the user or trusted entities to gain control.

**Why it matters ethically:** False identity claims can trigger irreversible actions and erode trust.

**Possible mitigations:** Multi-factor authentication, cryptographic attestations, trusted-contact verification workflows.

**Open questions:** How to design anti-spoofing controls resilient to deepfake voice/video attacks?

---

## 7) Coercive access
**Description:** A user is pressured by employers, partners, states, or attackers to reveal device contents or grant access.

**Why it matters ethically:** Consent under coercion is not meaningful consent.

**Possible mitigations:** Duress modes, compartmentalization, selective disclosure, legal/policy protections.

**Open questions:** Which coercion scenarios should technical design handle vs. legal institutions?

---

## 8) Vendor lock-in
**Description:** Personal context becomes dependent on proprietary formats, APIs, or identity rails.

**Why it matters ethically:** Loss of portability weakens ownership and autonomy.

**Possible mitigations:** Export standards, interoperable schemas, multi-provider routing, documented migration paths.

**Open questions:** What minimum interoperability baseline should the ecosystem require?

---

## 9) Government/corporate overreach
**Description:** Institutions demand broad access, create hidden surveillance channels, or impose opaque policy controls.

**Why it matters ethically:** Centralized control over identity context can chill speech and thought.

**Possible mitigations:** Transparency reports, clear legal challenge workflows, independent audits, user-notification defaults where lawful.

**Open questions:** How should cross-border legal conflicts be handled when constitutional rights differ?

---

## 10) Recovery abuse
**Description:** Account or device recovery mechanisms are exploited by attackers or insiders.

**Why it matters ethically:** Recovery paths often bypass frontline defenses and become systemic weak points.

**Possible mitigations:** Recovery cooldowns, multi-party recovery approvals, immutable recovery audit trails, staged privilege restoration.

**Open questions:** What recovery UX preserves dignity under stress without sacrificing security posture?
