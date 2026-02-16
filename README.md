# First Principles for AI Safety

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-active%20draft-orange)

A vendor-neutral, community-maintained framework that turns AI safety first principles into practical actions.

## Principles (summary)

1. **Human authority is non-negotiable** — keep meaningful human oversight in all high-impact decisions.
2. **Safety scales with capability** — increase safeguards as model capability and autonomy increase.
3. **Transparency is the default** — clearly disclose AI use, limits, and decision boundaries.
4. **Harm has owners** — assign accountable humans for every deployed system.
5. **Test before you trust** — require measurable pre-deployment and post-deployment safety evaluation.
6. **Honesty is structural, not aspirational** — prevent deception and communicate uncertainty explicitly.
7. **Principles evolve; rights don't** — version controls and policies while preserving human rights constraints.

## Why this exists

Major AI labs publish strong internal frameworks, but no shared open standard unifies philosophical foundations with practical implementation across regulators, startups, researchers, and open-source teams.

This repository fills that gap with:

- A one-page principles set for broad adoption.
- Auditable controls and checklist-driven implementation.
- Crosswalk mappings to major standards and company frameworks.
- A transparent RFC governance process.

## How to use this

- Start with [`PRINCIPLES.md`](PRINCIPLES.md).
- Run the quick self-audit in [`CHECKLIST.md`](CHECKLIST.md).
- Implement controls using [`IMPLEMENTATION_GUIDE.md`](IMPLEMENTATION_GUIDE.md) and `/templates`.
- Use framework mappings in [`mappings/crosswalk.md`](mappings/crosswalk.md) for policy and compliance alignment.

## Repository guide

- Core principles: [`PRINCIPLES.md`](PRINCIPLES.md)
- Machine-readable source: [`principles.yaml`](principles.yaml)
- Validation schema: [`schema.json`](schema.json)
- Implementation playbook: [`IMPLEMENTATION_GUIDE.md`](IMPLEMENTATION_GUIDE.md)
- Self-assessment: [`CHECKLIST.md`](CHECKLIST.md)
- Incident examples: [`examples/incidents.md`](examples/incidents.md)
- Audience guides: [`guides/`](guides/)
- Framework mappings: [`mappings/`](mappings/)
- Templates: [`templates/`](templates/)
- Governance and updates: [`GOVERNANCE.md`](GOVERNANCE.md), [`CONTRIBUTING.md`](CONTRIBUTING.md), [`CHANGELOG.md`](CHANGELOG.md)

## Citation

### Plain text

First Principles for AI Safety (2026). Community framework for vendor-neutral AI safety principles and implementation guidance. https://github.com/oasis-eng/first-principles-ai

### BibTeX

```bibtex
@misc{firstprinciplesai2026,
  title        = {First Principles for AI Safety},
  author       = {{First Principles for AI Safety Contributors}},
  year         = {2026},
  howpublished = {GitHub repository},
  url          = {https://github.com/oasis-eng/first-principles-ai}
}
```

## Contributing

Contributions are welcome through the RFC process described in [`CONTRIBUTING.md`](CONTRIBUTING.md).
