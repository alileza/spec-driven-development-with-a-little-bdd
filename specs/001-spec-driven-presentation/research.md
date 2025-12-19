# Research: impress.js & Interactive Presentations

**Feature**: 001-spec-driven-presentation
**Date**: 2025-12-19

## impress.js Framework

### Decision: Use impress.js v2.0.0 from CDN

**Rationale**:
- No build tools required (aligns with constitution)
- Single script include
- Well-documented with active community
- Supports all required 3D transforms and transitions

**Alternatives considered**:
- reveal.js — More features but heavier, requires npm
- Prezi — Not self-hostable, requires account
- Plain HTML/CSS — Too much custom code for 3D navigation

### Core Data Attributes

```html
<!-- Root container -->
<div id="impress"
     data-transition-duration="1000"
     data-width="1920"
     data-height="1080"
     data-perspective="1000">

<!-- Individual slide -->
<div class="step"
     data-x="0" data-y="0" data-z="0"
     data-rotate="0" data-rotate-x="0" data-rotate-y="0"
     data-scale="1">
```

### CSS Class States

| Class | When Applied | Use For |
|-------|--------------|---------|
| `.future` | Unvisited slides | Hide/dim content |
| `.present` | Current slide | Trigger animations |
| `.past` | Visited slides | Show as completed |
| `.active` | Visible at center | Same as present |

### Animation Pattern

```css
/* Element hidden by default */
.step .fade-in {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s, transform 0.6s;
}

/* Animate when slide becomes active */
.step.present .fade-in {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger multiple elements */
.step.present .fade-in:nth-child(1) { transition-delay: 0.1s; }
.step.present .fade-in:nth-child(2) { transition-delay: 0.2s; }
.step.present .fade-in:nth-child(3) { transition-delay: 0.3s; }
```

## SVG Stick Figures

### Decision: Inline SVG with CSS animations

**Rationale**:
- No external files (single HTML file)
- CSS-animatable via stroke properties
- Scalable without quality loss
- Can be styled per-slide

**Alternatives considered**:
- PNG/GIF images — Not animatable, separate files
- Canvas — Requires JavaScript, overkill
- CSS-only drawings — Limited expressiveness

### Drawing Animation Technique

```css
/* SVG line drawing effect */
.stick-figure path,
.stick-figure line,
.stick-figure circle {
  stroke-dasharray: 200;
  stroke-dashoffset: 200;
  transition: stroke-dashoffset 1s ease-out;
}

.step.present .stick-figure path,
.step.present .stick-figure line,
.step.present .stick-figure circle {
  stroke-dashoffset: 0;
}
```

### Stick Figure Templates

**Basic figure** (standing):
```svg
<svg viewBox="0 0 100 150" class="stick-figure">
  <!-- Head -->
  <circle cx="50" cy="20" r="15" fill="none" stroke="currentColor" stroke-width="3"/>
  <!-- Body -->
  <line x1="50" y1="35" x2="50" y2="85" stroke="currentColor" stroke-width="3"/>
  <!-- Arms -->
  <line x1="50" y1="50" x2="25" y2="70" stroke="currentColor" stroke-width="3"/>
  <line x1="50" y1="50" x2="75" y2="70" stroke="currentColor" stroke-width="3"/>
  <!-- Legs -->
  <line x1="50" y1="85" x2="30" y2="130" stroke="currentColor" stroke-width="3"/>
  <line x1="50" y1="85" x2="70" y2="130" stroke="currentColor" stroke-width="3"/>
</svg>
```

**Confused figure** (arms up, question mark):
```svg
<svg viewBox="0 0 120 170" class="stick-figure confused">
  <!-- Head -->
  <circle cx="60" cy="30" r="15" fill="none" stroke="currentColor" stroke-width="3"/>
  <!-- Body -->
  <line x1="60" y1="45" x2="60" y2="95" stroke="currentColor" stroke-width="3"/>
  <!-- Arms raised -->
  <line x1="60" y1="60" x2="35" y2="40" stroke="currentColor" stroke-width="3"/>
  <line x1="60" y1="60" x2="85" y2="40" stroke="currentColor" stroke-width="3"/>
  <!-- Legs -->
  <line x1="60" y1="95" x2="40" y2="140" stroke="currentColor" stroke-width="3"/>
  <line x1="60" y1="95" x2="80" y2="140" stroke="currentColor" stroke-width="3"/>
  <!-- Question mark -->
  <text x="95" y="25" font-size="30" fill="currentColor">?</text>
</svg>
```

**Lightbulb moment**:
```svg
<svg viewBox="0 0 120 180" class="stick-figure lightbulb">
  <!-- Lightbulb above head -->
  <circle cx="60" cy="15" r="12" fill="#FFD700" stroke="#FFA500" stroke-width="2"/>
  <line x1="60" y1="3" x2="60" y2="-5" stroke="#FFA500" stroke-width="2"/>
  <line x1="50" y1="5" x2="45" y2="-2" stroke="#FFA500" stroke-width="2"/>
  <line x1="70" y1="5" x2="75" y2="-2" stroke="#FFA500" stroke-width="2"/>
  <!-- Head -->
  <circle cx="60" cy="50" r="15" fill="none" stroke="currentColor" stroke-width="3"/>
  <!-- Body -->
  <line x1="60" y1="65" x2="60" y2="115" stroke="currentColor" stroke-width="3"/>
  <!-- Arms (one raised) -->
  <line x1="60" y1="80" x2="35" y2="100" stroke="currentColor" stroke-width="3"/>
  <line x1="60" y1="80" x2="90" y2="60" stroke="currentColor" stroke-width="3"/>
  <!-- Legs -->
  <line x1="60" y1="115" x2="40" y2="160" stroke="currentColor" stroke-width="3"/>
  <line x1="60" y1="115" x2="80" y2="160" stroke="currentColor" stroke-width="3"/>
</svg>
```

## Code Block Styling

### Decision: Prism-like syntax highlighting with CSS only

```css
.code-block {
  background: #1e1e1e;
  color: #d4d4d4;
  padding: 1em;
  border-radius: 8px;
  font-family: 'Fira Code', monospace;
  font-size: 0.9em;
  overflow-x: auto;
}

.code-block .keyword { color: #569cd6; }
.code-block .string { color: #ce9178; }
.code-block .comment { color: #6a9955; }
.code-block .function { color: #dcdcaa; }
```

## References

- [impress.js GitHub](https://github.com/impress/impress.js)
- [impress.js Documentation](https://github.com/impress/impress.js/blob/master/DOCUMENTATION.md)
- [SVG Animation with CSS](https://css-tricks.com/svg-line-animation-works/)
- [SVG Artista](https://svgartista.net/) — For generating animation values
