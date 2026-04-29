# AI Passport Design Principles

These principles define the ethical baseline for the AI Passport concept. They are meant to guide design tradeoffs across [architecture](./architecture.md), [threat modeling](./threat-model.md), and the broader constitutional framing in the [essay](./essay.md).

## 1) Human agency first
The system should expand a person’s ability to decide, act, and refuse. AI should support judgment, not silently replace it.

## 2) Private by default
Sensitive data should not leave the personal layer unless the person deliberately chooses to share it.

## 3) Local before cloud
The architecture should prefer local processing and local memory for identity-critical operations, escalating to cloud services when necessary.

## 4) Consent must be explicit
Permission should be clear, revocable, and contextual. Silent consent and hidden inheritance across contexts should be treated as design failures.

## 5) Memory must be inspectable
People should be able to view, correct, export, and delete personal memory entries with understandable controls.

## 6) Revocation must be possible
Access tokens, delegated permissions, and trusted relationships should be revocable with bounded latency and clear effects.

## 7) No hidden behavioral manipulation
The system should not nudge, addict, or steer users through undisclosed optimization objectives.

## 8) Interoperability over lock-in
Cloud models and tooling should be swappable. Personal identity context should not be trapped in a single vendor ecosystem.

## 9) Security claims must be humble
Security language should be precise and constrained. Designers should communicate residual risk, not promises of invulnerability.

## 10) Frontier AI should serve humans directly
As model capability increases, the primary beneficiary should be the person carrying the personal layer—not intermediaries that capture value by controlling identity and context.
