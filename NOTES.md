# Claude Notes - swatch

## Project Overview

Single-file color picker and gradient generator web application. Users can select colors via RGB sliders, save them to palettes, and generate/export gradients from those palettes.

## Technical Stack

- **Frontend**: Pure HTML/CSS/JavaScript with jQuery
- **Fonts**: Google Fonts (Dongle, Koulen)
- **Storage**: localStorage with JSON serialization
- **Export**: Canvas API for PNG generation (1920x1080)
- **Architecture**: Single-file application (index.html)

## Key Implementation Details

### File Structure
- `index.html` - All HTML, CSS, and JavaScript in one file
- Inline SVG favicon using data URI
- No build process or external dependencies beyond CDN resources

### Data Model
```javascript
palettes = [
    {
        id: number,
        name: string,
        colors: string[] // hex colors with # prefix, max 6
    }
]
```

### Important Functions
- `addToPalette(paletteId)` - Normalizes hex values (ensures # prefix)
- `loadPalettes()` - Auto-repairs malformed colors on load
- `updateGradientDisplay()` - Supports 1-color palettes by duplicating
- `downloadGradientPNG()` - Renders to canvas and exports

### CSS Architecture
- Mode switching via body classes: `.picker-mode`, `.gradient-mode`
- Sticky header with `position: sticky`
- Contrast adjustment via `.dark-bg` class
- Selection indicator uses `outline` (not `border`) to avoid layout shift

### Known Issues/Fixes Applied
- ✅ Hex normalization (ensures # prefix on all colors)
- ✅ Single-color palette support (duplicates color for gradient)
- ✅ Removed transform effects that caused "bopping"
- ✅ Fixed header background masking on scroll
- ✅ Event delegation for dynamically rendered palette rows

## Todos

### Features
- [ ] Add color copying to clipboard on click
- [ ] Keyboard shortcuts for common actions
- [ ] Undo/redo for palette edits
- [ ] Import/export palettes as JSON
- [ ] Color harmony suggestions (complementary, triadic, etc.)
- [ ] Eye dropper tool for sampling colors from images
- [ ] Gradient animation preview

### UX Improvements
- [ ] Drag to reorder colors within palettes
- [ ] Drag to reorder palettes
- [ ] Delete confirmation dialog
- [ ] Toast notifications for actions (saved, deleted, etc.)
- [ ] Color name display (closest named color)

### Technical
- [ ] Add accessibility features (ARIA labels, keyboard navigation)
- [ ] Consider removing jQuery dependency (use vanilla JS)
- [ ] Add service worker for offline support
- [ ] Optimize for mobile touch interactions
- [ ] Add color space conversions (HSL, HSV)

### Polish
- [ ] Add loading states for export
- [ ] Better empty states (no palettes, no colors)
- [ ] Smooth transitions between modes
- [ ] Tutorial/onboarding for first-time users
- [ ] Get rid of cheesy alert for deleting palette - just delete. Maybe allow undo shortcut key 

## Session History Notes

- Original file was `colors.html`, renamed to `index.html`
- Named "swatch" after exploring many alternatives
- Significant debugging around palette selection click handlers
- Root cause: invalid hex values (missing #) caused silent CSS failures
