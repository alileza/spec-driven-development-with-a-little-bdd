<!--
  Sync Impact Report
  ==================
  Version Change: 0.0.0 → 1.0.0 (Initial ratification)

  Modified Principles: N/A (first version)

  Added Sections:
    - Principle I: Radical Simplicity
    - Principle II: Expand Only When Necessary
    - Development Philosophy section
    - Governance section

  Removed Sections: N/A (first version)

  Templates Status:
    ✅ plan-template.md - Constitution Check section compatible
    ✅ spec-template.md - No conflicts with simplicity principles
    ✅ tasks-template.md - Structure aligned with minimal approach

  Follow-up TODOs: None
-->

# Spec-Driven Development Constitution

## Core Principles

### I. Radical Simplicity

Every decision MUST favor the simplest viable solution:

- **Single file over multiple files** - If functionality can live in one file, it stays in one file
- **No directories until necessary** - Flat structure is the default; nesting requires justification
- **No frameworks unless essential** - Vanilla/stdlib solutions first; dependencies earn their place
- **No abstractions without repetition** - DRY only after three concrete instances exist
- **Delete before refactor** - Removing code is better than reorganizing it

**Rationale**: Complexity is a cost. Every file, folder, dependency, and abstraction adds cognitive
load and maintenance burden. Simplicity enables faster iteration and easier understanding.

### II. Expand Only When Necessary

Growth happens incrementally and only when constraints force it:

- **Add structure when current approach breaks** - Not when it "might" break
- **Split files when they become unmanageable** - Defined as: cannot understand the file in one read
- **Add dependencies when building yourself costs more** - Time + maintenance > import cost
- **Create abstractions when patterns emerge** - After implementation, not before

**Rationale**: Premature organization creates orphaned structures and unnecessary indirection.
Real needs reveal themselves through actual pain points, not theoretical concerns.

## Development Philosophy

- **YAGNI (You Aren't Gonna Need It)** - Build for today's requirements, not tomorrow's maybes
- **Working code over perfect architecture** - Ship, then improve based on feedback
- **Inline over extracted** - Keep related code together until separation provides clear benefit
- **Explicit over clever** - Readable beats elegant; obvious beats optimized

## Governance

This constitution guides all development decisions in this project:

- **Compliance**: All changes MUST be evaluated against these principles
- **Violations**: Any complexity MUST be explicitly justified in design docs or PR descriptions
- **Amendments**: Changes to this constitution require explicit rationale and version bump
- **Versioning**: MAJOR for principle changes, MINOR for additions, PATCH for clarifications

**Version**: 1.0.0 | **Ratified**: 2025-12-19 | **Last Amended**: 2025-12-19
