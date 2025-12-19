# Tasks: Spec-Driven Development Presentation

**Input**: Design documents from `/specs/001-spec-driven-presentation/`
**Prerequisites**: plan.md, storyline.md (draft/), research.md

**Tests**: Not requested - this is a static HTML presentation.

**Organization**: Tasks are grouped by presentation acts to enable incremental development. Each act can be previewed independently.

## Format: `[ID] [P?] [Act?] Description`

- **[P]**: Can run in parallel (different slides, no dependencies)
- **[Act]**: Which presentation act this task belongs to (ACT1, ACT2, etc.)
- Include exact file paths in descriptions

## Path Conventions

```text
src/
└── index.html          # Complete presentation (single file)

draft/
├── storyline.md        # Content reference
└── workflow.png        # Diagram asset
```

---

## Phase 1: Setup (Project Foundation)

**Purpose**: Create base HTML structure with impress.js

- [X] T001 Create src/ directory structure
- [X] T002 Create base HTML skeleton with impress.js CDN in src/index.html
- [X] T003 Add base CSS styles (typography, colors, layout) in src/index.html `<style>` tag
- [X] T004 Add CSS animation classes (fade-in, stagger, draw-in) in src/index.html
- [X] T005 [P] Create reusable stick figure SVG templates as CSS/HTML comments in src/index.html

**Checkpoint**: Base presentation loads with impress.js working, ready for slides

---

## Phase 2: Foundational Slides (Title + Navigation Setup)

**Purpose**: Core slides that set up the presentation and define spatial layout

**⚠️ CRITICAL**: Establishes 3D coordinate system for all acts

- [X] T006 Create title slide (id="title") at center position in src/index.html
- [X] T007 Add speaker info and presentation title to title slide in src/index.html
- [X] T008 Define 3D spatial coordinates for all act positions in src/index.html (as HTML comments)
- [X] T009 Add impress.js initialization script at end of src/index.html

**Checkpoint**: Title slide displays, navigation works, spatial layout documented

---

## Phase 3: ACT 1 - The Skeptic (Priority: P1) 🎯 MVP

**Goal**: Establish the skepticism narrative with 5 slides (left cluster, x=-2000)

**Independent Test**: Open src/index.html, navigate to ACT 1 slides, verify content and animations

### Implementation for ACT 1

- [X] T010 [ACT1] Create "Opening: Promise vs Reality" slide with hype quotes in src/index.html
- [X] T011 [ACT1] Add confused stick figure SVG to opening slide in src/index.html
- [X] T012 [ACT1] Create "My Initial Experience" slide with bullet points in src/index.html
- [X] T013 [ACT1] Create "But what about CLAUDE.md?" slide in src/index.html
- [X] T014 [ACT1] Create "Core Problems" slide with numbered list in src/index.html
- [X] T015 [ACT1] Add frustrated stick figure SVG to problems slide in src/index.html
- [X] T016 [ACT1] Create "My conclusion" slide with quote box in src/index.html
- [X] T017 [ACT1] Add fade-in animations to all ACT 1 bullet points in src/index.html

**Checkpoint**: ACT 1 complete - skepticism narrative flows, stick figures animate

---

## Phase 4: ACT 2 - The Turning Point (Priority: P2)

**Goal**: Show AI strengths/weaknesses with 6 slides (center, rotating)

**Independent Test**: Navigate through ACT 2, verify table renders, lightbulb animation works

### Implementation for ACT 2

- [X] T018 [ACT2] Create "The Question" slide with key question in src/index.html
- [X] T019 [ACT2] Create "What AI Does Well" slide with 3 items (including yapping joke) in src/index.html
- [X] T020 [ACT2] Create "What AI Doesn't Do Well" slide with 3 items in src/index.html
- [X] T021 [ACT2] Create "The Insight" table slide (strengths vs weaknesses) in src/index.html
- [X] T022 [ACT2] Add lightbulb stick figure SVG to insight slide in src/index.html
- [X] T023 [ACT2] Create "Enter: Spec-Driven Development (Maybe?)" disclaimer slide in src/index.html
- [X] T024 [ACT2] Create "Why Specs Might Help" bridge slide in src/index.html
- [X] T025 [ACT2] Add staggered fade-in animations to ACT 2 lists in src/index.html

**Checkpoint**: ACT 2 complete - turning point narrative clear, disclaimer visible

---

## Phase 5: ACT 3 - What is SDD (Priority: P3)

**Goal**: Explain spec-driven development with 6 slides (top, elevated y=-1500)

**Independent Test**: Navigate through ACT 3, verify code blocks render, spec-kit workflow shows

### Implementation for ACT 3

- [X] T026 [ACT3] Create "Definition" slide with Martin Fowler quote in src/index.html
- [X] T027 [ACT3] Create "What is a Spec Anyway?" slide with phase boxes in src/index.html
- [X] T028 [ACT3] Create "Three Levels of Spec-Driven" table slide in src/index.html
- [X] T029 [ACT3] Create "What a Spec Looks Like" slide with code block example in src/index.html
- [X] T030 [ACT3] Style code block with syntax highlighting colors in src/index.html
- [X] T031 [ACT3] Create "GitHub's Spec-Kit" slide with workflow tables in src/index.html
- [X] T032 [ACT3] Add workflow.png image reference to spec-kit slide in src/index.html
- [X] T033 [ACT3] Add writing-spec stick figure SVG to spec example slide in src/index.html
- [X] T034 [ACT3] Create "References" slide with links in src/index.html

**Checkpoint**: ACT 3 complete - SDD explained, spec-kit workflow visible

---

## Phase 6: ACT 4 - My Problem with Specs (Priority: P4)

**Goal**: Present the stale specs problem with 4 slides (right cluster, x=2000)

**Independent Test**: Navigate through ACT 4, verify problem/solution structure clear

### Implementation for ACT 4

- [X] T035 [ACT4] Create "First, the Good Part" slide with benefits list in src/index.html
- [X] T036 [ACT4] Add happy checkmark stick figure SVG in src/index.html
- [X] T037 [ACT4] Create "But Then Reality Hits" slide with problems in src/index.html
- [X] T038 [ACT4] Create "Stale Specs Become Noise" slide with AI hallucination points in src/index.html
- [X] T039 [ACT4] Add worried stick figure SVG with dusty papers in src/index.html
- [X] T040 [ACT4] Create "Spec is Source of Truth" ideal vs reality slide in src/index.html
- [X] T041 [ACT4] Create "So What's the Solution?" slide with Option A/B in src/index.html

**Checkpoint**: ACT 4 complete - problem articulated, BDD teased

---

## Phase 7: ACT 5 - Let's Talk About BDD (Priority: P5)

**Goal**: Introduce BDD as solution with 6 slides (bottom, y=1500, depth z=-500)

**Independent Test**: Navigate through ACT 5, verify Gherkin code block renders, diagram shows

### Implementation for ACT 5

- [X] T042 [ACT5] Create "BDD Blackbox Approach" definition slide in src/index.html
- [X] T043 [ACT5] Create BDD blackbox diagram using CSS boxes (Given/When/Then) in src/index.html
- [X] T044 [ACT5] Create "From Spec to Executable Test" comparison slide in src/index.html
- [X] T045 [ACT5] Create "The Shift" table slide (Traditional vs BDD) in src/index.html
- [X] T046 [ACT5] Create "What BDD Specs Look Like" slide with Gherkin example in src/index.html
- [X] T047 [ACT5] Style Gherkin code block with proper highlighting in src/index.html
- [X] T048 [ACT5] Add test-running stick figure SVG with PASS signs in src/index.html
- [X] T049 [ACT5] Create "Why This Solves Stale Spec Problem" slide with 4 points in src/index.html

**Checkpoint**: ACT 5 complete - BDD explained with practical example

---

## Phase 8: Closing (Priority: P6)

**Goal**: Wrap up with journey recap and takeaways (front, zoomed, z=500, scale=2)

**Independent Test**: Navigate to closing, verify journey flow and Q&A slide

### Implementation for Closing

- [X] T050 [CLOSE] Create "My Journey" slide with flow diagram in src/index.html
- [X] T051 [CLOSE] Create "What I Learned" slide with 4 takeaways in src/index.html
- [X] T052 [CLOSE] Create "The Spectrum" table slide (approaches comparison) in src/index.html
- [X] T053 [CLOSE] Create "Final Thought" slide with quote in src/index.html
- [X] T054 [CLOSE] Create "Q&A" slide with @alileza contact in src/index.html
- [X] T055 [CLOSE] Create "References" final slide with all links in src/index.html
- [X] T056 [CLOSE] Add smooth zoom-in transition for closing sequence in src/index.html

**Checkpoint**: Closing complete - presentation ends with clear call to action

---

## Phase 9: Polish & Cross-Cutting Concerns

**Purpose**: Final improvements across all slides

- [X] T057 [P] Review and adjust all slide positions for smooth 3D navigation in src/index.html
- [X] T058 [P] Verify all stick figure SVG animations trigger correctly in src/index.html
- [ ] T059 [P] Test keyboard navigation (arrows, space) through entire presentation
- [ ] T060 [P] Test presentation in Chrome and Firefox browsers
- [X] T061 Add progress indicator (optional - dots or bar) in src/index.html
- [X] T062 Verify all external links work (Martin Fowler, GitHub, Tomato)
- [ ] T063 Final review: check timing feels right for 15-20 minute talk

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - start immediately
- **Foundational (Phase 2)**: Depends on Setup - establishes coordinate system
- **ACT 1-5 (Phases 3-7)**: All depend on Foundational phase
  - Can proceed in parallel if desired
  - Recommended: sequential for narrative flow testing
- **Closing (Phase 8)**: Depends on ACT 5 (for narrative continuity)
- **Polish (Phase 9)**: Depends on all acts complete

### Within Each Act

1. Create slides with content first
2. Add stick figures where planned
3. Add animations last
4. Test navigation within act

### Parallel Opportunities

- All stick figure SVGs (T011, T015, T022, T033, T036, T039, T048) can be created in parallel
- Code block styling tasks can run in parallel
- Polish tasks (T057-T063) can run in parallel

---

## Parallel Example: Stick Figures

```bash
# Create all stick figures in parallel:
Task: "Add confused stick figure SVG to opening slide"
Task: "Add frustrated stick figure SVG to problems slide"
Task: "Add lightbulb stick figure SVG to insight slide"
Task: "Add writing-spec stick figure SVG"
Task: "Add happy checkmark stick figure SVG"
Task: "Add worried stick figure SVG"
Task: "Add test-running stick figure SVG"
```

---

## Implementation Strategy

### MVP First (ACT 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (title + coordinates)
3. Complete Phase 3: ACT 1 - The Skeptic
4. **STOP and VALIDATE**: Test ACT 1 navigation and animations
5. Demo-ready with skepticism narrative

### Incremental Delivery

1. Setup + Foundational → Base presentation works
2. Add ACT 1 → Test → Demo (can present first 5 minutes)
3. Add ACT 2 → Test → Demo (turning point added)
4. Add ACT 3 → Test → Demo (SDD explained)
5. Add ACT 4 → Test → Demo (problem articulated)
6. Add ACT 5 → Test → Demo (BDD solution)
7. Add Closing → Test → Full presentation ready
8. Polish → Final review

---

## Summary

| Phase | Tasks | Purpose |
|-------|-------|---------|
| Setup | T001-T005 | Base HTML + CSS + impress.js |
| Foundational | T006-T009 | Title + coordinates |
| ACT 1 | T010-T017 | Skepticism (8 tasks) |
| ACT 2 | T018-T025 | Turning point (8 tasks) |
| ACT 3 | T026-T034 | SDD explanation (9 tasks) |
| ACT 4 | T035-T041 | Stale specs problem (7 tasks) |
| ACT 5 | T042-T049 | BDD solution (8 tasks) |
| Closing | T050-T056 | Wrap up (7 tasks) |
| Polish | T057-T063 | Final touches (7 tasks) |

**Total**: 63 tasks
**MVP Scope**: Phases 1-3 (T001-T017) = 17 tasks
**Parallel Opportunities**: 15+ tasks can run in parallel
