# Implementation Plan: Spec-Driven Development Presentation

**Branch**: `001-spec-driven-presentation` | **Date**: 2025-12-19 | **Spec**: [spec.md](./spec.md)
**Input**: Storyline from `draft/storyline.md`

## Summary

Create an interactive impress.js presentation about spec-driven development with AI agents. The presentation follows a 5-act narrative structure with 3D spatial navigation, CSS animations, and stick figure illustrations to make concepts memorable and engaging.

## Technical Context

**Language/Version**: HTML5, CSS3, JavaScript ES6+
**Primary Dependencies**: impress.js v2.0.0 (CDN)
**Storage**: N/A (static files)
**Testing**: Manual browser testing (Chrome, Firefox)
**Target Platform**: Modern browsers with CSS3 3D transform support
**Project Type**: Single static presentation
**Performance Goals**: Smooth 60fps transitions, <3s initial load
**Constraints**: Single HTML file preferred, no build tools, offline-capable after load
**Scale/Scope**: ~25-35 slides across 5 acts + closing

## Constitution Check

✅ **I. Radical Simplicity**:
- Single `index.html` file for entire presentation
- CSS embedded in `<style>` tag (no separate files unless too large)
- impress.js loaded from CDN (no local dependencies)
- Stick figures as inline SVG (no external image files)
- No build tools, no bundlers, no frameworks beyond impress.js

✅ **II. Expand Only When Necessary**:
- Start with everything in one file
- Only extract CSS if it exceeds ~200 lines
- Only extract SVGs if they're reused across many slides

## Project Structure

```text
src/
└── index.html          # Complete presentation (HTML + CSS + inline SVG)

draft/
├── storyline.md        # Content reference (already exists)
└── workflow.png        # Spec-kit workflow diagram

specs/001-spec-driven-presentation/
├── spec.md
├── plan.md             # This file
└── research.md         # impress.js research findings
```

**Structure Decision**: Single file approach per constitution. All CSS, SVG stick figures, and HTML in one `index.html`. The `draft/` folder contains reference content only.

## Research Findings

### impress.js Core Features

**Slide Positioning** (data attributes):
| Attribute | Purpose | Example |
|-----------|---------|---------|
| `data-x` | Horizontal position | `data-x="1000"` |
| `data-y` | Vertical position | `data-y="500"` |
| `data-z` | Depth (3D) | `data-z="-1000"` |
| `data-scale` | Zoom level | `data-scale="2"` |
| `data-rotate` | 2D rotation | `data-rotate="90"` |
| `data-rotate-x/y/z` | 3D rotation | `data-rotate-y="45"` |

**CSS Classes for Animation**:
- `.future` — Slides not yet visited
- `.present` — Current slide (trigger animations here)
- `.past` — Previously visited slides
- `.active` — Visible at camera center

**Animation Pattern**:
```css
/* Hidden by default */
.step .animated-element {
  opacity: 0;
  transform: translateY(20px);
}

/* Animate when slide is active */
.step.present .animated-element {
  opacity: 1;
  transform: translateY(0);
  transition: all 0.5s ease-out;
}
```

### Stick Figure SVG Approach

Simple inline SVG stick figures using:
- `<circle>` for head
- `<line>` elements for body, arms, legs
- `stroke-dasharray` + `stroke-dashoffset` for drawing animations
- CSS transitions on `.present` to animate

**Basic stick figure template**:
```svg
<svg viewBox="0 0 100 150" class="stick-figure">
  <circle cx="50" cy="20" r="15" fill="none" stroke="#333" stroke-width="2"/>
  <line x1="50" y1="35" x2="50" y2="80" stroke="#333" stroke-width="2"/>
  <line x1="50" y1="50" x2="30" y2="70" stroke="#333" stroke-width="2"/>
  <line x1="50" y1="50" x2="70" y2="70" stroke="#333" stroke-width="2"/>
  <line x1="50" y1="80" x2="35" y2="120" stroke="#333" stroke-width="2"/>
  <line x1="50" y1="80" x2="65" y2="120" stroke="#333" stroke-width="2"/>
</svg>
```

## Slide Layout Design

### Spatial Navigation Concept

The presentation uses 3D space to reinforce the narrative journey:

```
                    ACT 3: SDD (top)
                         ↑
ACT 1 (left) ←→ ACT 2 (center) ←→ ACT 4 (right)
                         ↓
                    ACT 5: BDD (bottom)
                         ↓
                    CLOSING (front, zoomed)
```

### Slide Mapping from Storyline

| Act | Slides | Position | Theme |
|-----|--------|----------|-------|
| Title | 1 | Center, scaled up | Introduction |
| ACT 1: Skeptic | 2-6 | Left cluster | Dark/frustrated |
| ACT 2: Turning Point | 7-12 | Center, rotating | Questioning |
| ACT 3: What is SDD | 13-18 | Top, elevated | Learning |
| ACT 4: Problems | 19-22 | Right cluster | Concerned |
| ACT 5: BDD | 23-28 | Bottom, depth | Solution |
| Closing | 29-32 | Front, zoomed in | Resolution |

### Animation Strategy

**Per-slide animations** (trigger on `.present`):
1. **Text fade-in**: Stagger bullet points appearing
2. **Code blocks**: Typewriter effect or highlight lines
3. **Stick figures**: Draw-in animation using stroke-dashoffset
4. **Diagrams**: Fade in sections progressively
5. **Tables**: Row-by-row reveal

**Transition animations** (between slides):
- Default: 1000ms smooth pan/rotate
- Act transitions: 1500ms with scale change
- Dramatic moments: 2000ms with z-axis movement

## Interactive Elements

1. **Keyboard navigation**: Space/arrows (built-in)
2. **Click navigation**: Click anywhere to advance
3. **Overview mode**: Press 'O' to see all slides (plugin)
4. **Progress indicator**: Subtle dots or progress bar

## Stick Figure Scenes

| Scene | Location | Depicts |
|-------|----------|---------|
| Confused developer | ACT 1 | Scratching head, question marks |
| Frustrated at computer | ACT 1 | Arms raised, "!!!" |
| Lightbulb moment | ACT 2 | Light bulb above head |
| Writing spec | ACT 3 | At desk with document |
| Happy with checkmarks | ACT 3 | Thumbs up, checkmarks |
| Worried about stale docs | ACT 4 | Looking at dusty papers |
| Running tests | ACT 5 | Figure with "PASS" signs |

## Complexity Tracking

| Violation | Why Needed | Simpler Alternative Rejected |
|-----------|------------|------------------------------|
| Multiple stick figure SVGs | Visual storytelling | Text-only is less engaging |
| CSS animations | Interactivity requirement | Static slides lose audience |

## Phase 1 Outputs

- **research.md**: ✅ Consolidated above
- **data-model.md**: N/A (no data entities)
- **contracts/**: N/A (no APIs)
- **quickstart.md**: See below

## Quickstart

```bash
# View presentation
open src/index.html

# Or serve locally (for development)
python -m http.server 8000
# Then visit http://localhost:8000/src/index.html
```

**Navigation**:
- `Space` / `→` / `↓` — Next slide
- `←` / `↑` — Previous slide
- `O` — Overview (if plugin enabled)

## Next Steps

Run `/speckit.tasks` to generate implementation task list.
