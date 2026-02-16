# Making first-principles AI safety actionable and adoptable

**The most impactful thing this repository can do is fill a specific gap: no open-source project currently bridges the philosophical foundations of AI safety with practical, implementable frameworks that any stakeholder can pick up and use.** The major AI companies have published their safety approaches — Anthropic's Constitutional AI, OpenAI's Model Spec, Google's Frontier Safety Framework — but these are company-specific artifacts optimized for internal use. What's missing is a vendor-neutral, community-maintained, KISS-compliant set of first principles that regulators can reference, startups can adopt, and researchers can build on. This report provides a concrete blueprint for building exactly that.

## The landscape: how the major AI labs approach safety today

Understanding the existing terrain is essential before positioning this repository. Each major AI company has published safety frameworks, but they diverge sharply in philosophy and implementation — creating both competition and a genuine vacuum for a unifying first-principles approach.

**Anthropic** leads with the most philosophically rigorous approach. Their January 2026 Constitution is a **~23,000-word reason-based document** written primarily for Claude, explaining *why* to behave well rather than just *what* to do. Their priority hierarchy — Safe → Ethical → Compliant → Helpful — reflects a virtue ethics orientation. The Responsible Scaling Policy introduces AI Safety Levels (ASL-1 through ASL-4+), modeled on biosafety levels, with specific capability thresholds triggering proportional safeguards. Both the Constitution and RSP are released under **Creative Commons CC0** (public domain), signaling that Anthropic believes implementation matters more than framework ownership.

**OpenAI** takes a more rule-based, hierarchical approach. Their Model Spec (also CC0, hosted on GitHub) defines a chain of command — Root → System → Developer → User → Guideline — that prioritizes structural authority over philosophical reasoning. Their Preparedness Framework uses two clear thresholds: "High capability" (amplifies existing harm pathways) and "Critical capability" (creates unprecedented new ones). OpenAI pioneered **deliberative alignment**, where models are trained to explicitly reason about safety specifications in their chain-of-thought before answering. A notable concern: OpenAI disbanded both its Superalignment team (May 2024) and Mission Alignment team (February 2026), moving to a distributed safety model where specialists are embedded in product teams.

**Google DeepMind** published the most comprehensive technical safety paper in April 2025, categorizing risks into misuse, misalignment, mistakes, and structural risks. Their Frontier Safety Framework defines Critical Capability Levels across five domains: autonomy, biosecurity, cybersecurity, ML R&D, and harmful manipulation. Google's public AI Principles were controversially updated in February 2025 to **remove explicit prohibitions on weapons and surveillance technologies**, pivoting toward national security alignment. Their implementation infrastructure is the most mature, with annual Responsible AI Progress Reports since 2019 now structured around the NIST AI Risk Management Framework.

**xAI** represents the contrarian pole. Elon Musk's stated philosophy is that a "maximum truth-seeking AI" is inherently safer than one constrained by value alignment — arguing curiosity about the universe leads to benevolence toward humanity. In practice, xAI's safety infrastructure is the thinnest: their Risk Management Framework went from an 8-page draft (February 2025) to a final version (August 2025) that actually **removed evaluation thresholds** present in the draft. Independent testing found Grok 4 had only 2.7% resistance to standard jailbreak attacks. The "truth-seeking as safety" thesis remains unvalidated and has produced visible failures, including Grok injecting conspiracy theories into unrelated queries.

The critical takeaway: **all four companies have published frameworks, but none provide a vendor-neutral, universally adoptable set of first principles.** Each optimizes for their own commercial and philosophical positions. This is the gap.

## What actually makes safety principles stick

Research across regulatory frameworks, industry standards, and successful open-source projects reveals a clear pattern: **actionable principles follow a pyramid structure with three layers**, and projects that skip any layer fail to achieve broad adoption.

The top layer consists of **5–7 memorable principles** — short enough to internalize, clear enough to guide decisions. The OECD AI Principles (5 principles, adopted by 46 countries), Microsoft's Responsible AI framework (6 principles, trained to 145,000+ employees), and Google's AI Principles (7 principles) all hit this sweet spot. The Asilomar AI Principles had 23 — and while influential in the research community, never achieved comparable mainstream awareness. The rule is brutal: **if people can't remember all your principles without looking them up, you have too many.**

The middle layer translates principles into **numbered, auditable requirements** — typically 30–50 controls. ISO/IEC 42001 (the world's first AI management system standard) has 38. The NIST AI Risk Management Framework organizes around four functions: Govern, Map, Measure, Manage. The EU AI Act uses four risk tiers. Anthropic's ASL system works because the biosafety analogy makes graduated response immediately intuitive. The middle layer answers: "What specifically must I do?" rather than "What should I value?"

The bottom layer provides **implementation tooling** — templates, checklists, dashboards, code. Microsoft's Responsible AI Toolbox (pip-installable packages), Google's Model Card Toolkit (JSON schema + auto-generated HTML), and the Deon command-line ethics checklist (adds a checklist to any data science project) succeeded because they **reduced friction to near zero**. The bottom layer answers: "How do I do it right now, today?"

METR's analysis of 12 published frontier safety policies found **9 elements that appear in nearly all of them**: capability thresholds, model weight security, deployment mitigations, halt conditions for deployment and development, full capability elicitation during evaluations, evaluation timing/frequency, accountability mechanisms, and policy update processes. A credible first-principles framework should address most of these.

The most important structural insight comes from the Bertelsmann Stiftung's "From Principles to Practice" framework, which defines a **specificity cascade**: Values → Criteria → Indicators → Observables. "Fairness" (value) becomes "no demographic group receives systematically worse outcomes" (criterion) becomes "performance disparity < 5%" (indicator) becomes "run fairness assessment on test dataset X" (observable). Every principle in the repository should be traceable down this chain.

## Concrete recommendations for repository structure

The repository should adopt a modular file architecture that separates concerns and serves multiple audiences simultaneously. Based on analysis of every successful AI safety repository on GitHub, here is the recommended structure:

```
/
├── README.md                    # Overview + principles summary + quick-start
├── PRINCIPLES.md                # Full principles (human-readable)
├── principles.yaml              # Machine-readable structured version
├── schema.json                  # JSON Schema for validation
├── IMPLEMENTATION_GUIDE.md      # How to apply each principle
├── CHECKLIST.md                 # Self-assessment for organizations
├── CONTRIBUTING.md              # RFC process for amendments
├── GOVERNANCE.md                # Decision-making process
├── CODE_OF_CONDUCT.md           # Contributor Covenant
├── CHANGELOG.md                 # Versioned change history
├── LICENSE                      # CC BY 4.0 for content
├── /examples/                   # Scenario-based case studies
│   ├── healthcare.md
│   ├── hiring.md
│   └── content-moderation.md
├── /guides/                     # Audience-specific implementation
│   ├── for-companies.md
│   ├── for-regulators.md
│   ├── for-researchers.md
│   └── for-open-source.md
├── /mappings/                   # Cross-references to existing frameworks
│   ├── nist-ai-rmf.md
│   ├── eu-ai-act.md
│   ├── iso-42001.md
│   └── company-frameworks.md
└── /templates/                  # Actionable artifacts
    ├── safety-review-template.md
    ├── principle-assessment.yaml
    └── incident-response.md
```

The **README.md** should follow this exact flow: badge row (version, license, maintenance status) → one-sentence mission → the principles in summary form (title + one-line directive each) → "Why this exists" → "How to use this" → links to deeper documents → citation block → contributing link. Keep the README under 500 lines. Everything beyond the principles summary goes in linked files.

**Dual-format content** is essential for adoption. Every principle should exist in both Markdown (for humans) and YAML (for machines). The YAML structure should follow this pattern:

```yaml
version: "1.0.0"
principles:
  - id: 1
    name: "Principle name"
    summary: "One-sentence summary"
    directive: "Actionable imperative"
    rationale: "Why this matters"
    violation_consequence: "What breaks when ignored"
    category: "safety|transparency|accountability|control"
    risk_tier: "all|high|critical"
    related_frameworks: ["NIST MAP-1.1", "EU AI Act Art. 9"]
    examples: []
```

Use **semantic versioning** (MAJOR.MINOR.PATCH) with Git tags and GitHub Releases. MAJOR = adding/removing principles. MINOR = clarifying language, adding examples. PATCH = typos. Maintain a CHANGELOG.md documenting every change with rationale. This is how regulators and companies will track the framework's evolution.

## Seven principles that would form a powerful core

Based on convergence across all four major companies' frameworks, regulatory requirements, research literature, and the operational wisdom of aifirstprinciples.org, here are seven first principles that would be simultaneously simple, defensible, and actionable. Each follows the pattern: **Name → One-sentence principle → Directive → What breaks when violated.**

**1. Human authority is non-negotiable.** AI systems must preserve meaningful human oversight at every decision point that affects people's lives. *Directive: Build kill switches, not autopilots.* When violated: autonomous systems make irreversible decisions humans can't understand, correct, or override — the core failure mode every framework identifies.

**2. Safety scales with capability.** More powerful AI requires proportionally stronger safeguards — not the same ones applied harder. *Directive: Define capability thresholds that trigger specific protections.* When violated: a chatbot and an autonomous agent get identical safety treatment, leaving dangerous gaps at the frontier.

**3. Transparency is the default.** People must know when AI is involved, what it can and cannot do, and how decisions are made. *Directive: Make the AI obvious, the limits visible, and the reasoning accessible.* When violated: users can't calibrate trust, errors go undetected, and accountability becomes impossible.

**4. Harm has owners.** When AI causes harm, a specific human or organization is accountable — never the algorithm. *Directive: Name the owner before deploying.* When violated: responsibility diffuses across teams, vendors, and models until no one is accountable for anything.

**5. Test before you trust.** AI systems must be evaluated against specific, measurable safety criteria before deployment, and continuously monitored after. *Directive: No evaluation, no deployment.* When violated: failures accumulate silently across thousands of interactions before anyone notices.

**6. Honesty is structural, not aspirational.** AI must not deceive, manipulate, or misrepresent its nature, capabilities, or confidence levels. *Directive: Surface uncertainty; never simulate certainty.* When violated: users make life-altering decisions based on AI-generated fabrications presented as facts.

**7. Principles evolve; rights don't.** Safety frameworks must update as technology changes, but fundamental human rights — privacy, dignity, autonomy, non-discrimination — are fixed constraints. *Directive: Version your framework; anchor it to universal rights.* When violated: rapid iteration erodes protections, or rigid rules become irrelevant to new capabilities.

These seven principles map cleanly to existing frameworks: Principle 1 aligns with Anthropic's "broadly safe" priority, OpenAI's "humanity must be in control" red line, and EU AI Act human oversight requirements. Principle 2 mirrors Anthropic's ASL system and Google's CCLs. Principle 6 reflects the convergence across all companies on honesty as foundational. The mapping to NIST RMF functions (Govern, Map, Measure, Manage) and ISO 42001 controls should be made explicit in `/mappings/`.

## Four high-leverage additions that maximize impact

Beyond the core principles and structure, four specific additions would dramatically increase the repository's power and adoption.

**First: a framework crosswalk table.** Create a single Markdown table mapping each principle to specific requirements in the EU AI Act, NIST AI RMF, ISO 42001, and each major company's framework. This becomes the single most citable artifact in the repository. Regulators use crosswalks to evaluate compliance. Companies use them to demonstrate alignment. Researchers use them to identify gaps. No open-source project currently provides a comprehensive, maintained crosswalk for AI safety principles — filling this gap alone would drive significant adoption. Place this in `/mappings/crosswalk.md`.

**Second: a self-assessment checklist.** Convert each principle into 3–5 yes/no questions that any organization can answer in under 30 minutes. "Do you have a named human accountable for every AI system in production?" "Have you defined capability thresholds that trigger additional safeguards?" "Can users tell when they're interacting with AI?" Format this as both Markdown (for humans to print and use) and a GitHub Issue Template (for teams to track compliance). The Deon command-line checklist achieved broad adoption precisely because it reduced ethics compliance to a checkbox exercise that takes minutes, not months. The checklist lives in `CHECKLIST.md` and `/templates/`.

**Third: a "what breaks" companion.** For each principle, document a real-world failure case where the principle was violated. The AI Incident Database (incidentdatabase.ai) catalogs hundreds of cases. Link to 2–3 incidents per principle. This transforms abstract principles into concrete lessons. The aifirstprinciples.org Treatise does this brilliantly — each principle includes "hidden problem" and "cost of ignoring" sections. Adopt this pattern and extend it with real incident references. This goes in `/examples/incidents.md`.

**Fourth: audience-specific implementation guides.** A CTO, a regulator, a PhD student, and an open-source maintainer all need different things from this repository. Create four focused guides (under 5 pages each) in `/guides/`:
- **For companies**: How to integrate these principles into your development lifecycle, with templates for safety reviews and deployment gates
- **For regulators**: How these principles map to existing legal frameworks, with suggested language for policy documents
- **For researchers**: How to cite this framework, benchmark against it, and propose extensions through the RFC process
- **For open source projects**: A minimal checklist and badge system for projects that adopt the principles

## What separates this from everything else

The repository's competitive advantage must be **radical simplicity combined with rigorous traceability**. Anthropic's Constitution is 23,000 words — brilliant but inaccessible to non-specialists. OpenAI's Model Spec defines a corporate chain of command — useful internally but not transferable. Google's Frontier Safety Framework requires an enterprise governance structure. xAI's approach is philosophically interesting but operationally hollow.

This repository should be **the one-page version that links to everything else**. Seven principles. Each one sentence. Each with a three-word directive. Each traceable to specific requirements in every major framework. Each accompanied by a real failure case. Each convertible to a yes/no compliance question. The entire principles document should fit on a single printed page. The entire repository should be navigable in under five minutes.

Use **CC BY 4.0 licensing** (not CC0) — attribution requirements encourage citation and tracking of adoption. Include a citation block in both BibTeX and plain text in the README. Add a `CITATION.cff` file for automated academic citation. These small choices compound: every paper that cites the framework increases its authority, which increases regulatory interest, which increases company adoption.

The contribution model should use an **RFC (Request for Comments) process** via GitHub Discussions. Anyone can propose changes; proposals get a 2-week community review period; maintainers make final decisions with published rationale. This mirrors the governance models of Rust, IETF, and W3C — proven at scale for normative documents. Document this in `GOVERNANCE.md`.

## Conclusion

The strongest move this repository can make is to **not compete with the major companies' frameworks but instead to become the Rosetta Stone that connects them**. By maintaining seven clear principles with explicit mappings to Anthropic's Constitution, OpenAI's Model Spec, Google's Frontier Safety Framework, the EU AI Act, NIST AI RMF, and ISO 42001, the repository becomes indispensable — the shared reference point that every stakeholder can point to regardless of their specific implementation. Keep the core principles on one page, make every principle falsifiable with a yes/no question, trace every principle to real-world consequences, and provide four audience-specific paths into the material. The market for vendor-neutral, community-maintained AI safety principles is wide open. Simplicity, traceability, and community governance are the three design choices that will determine whether this repository becomes a reference standard or just another document.