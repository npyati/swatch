# Claude Notes - swatch

## Project Overview

Single-file color picker and gradient generator web application. Users can select colors via RGB sliders, save them to palettes, and generate/export gradients from those palettes.

## Technical Stack

- **Frontend**: Pure HTML/CSS/JavaScript (vanilla JS, no dependencies)
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
- [x] Add color copying (hex) to clipboard on click
- [x] Color harmony suggestions (complementary, triadic, analogous, split-complementary)
- [x] Eye dropper tool for sampling colors from screen (Chrome EyeDropper API)
- [x] Be able to save individual colors and palettes as .SVG files that will show a preview in a Mac or Windows filesystem. Then, accept drag and drop of these into the window - colors update the picker, palettes get added as a palette w/ name

### UX Improvements
- [x] On mobile, tab icons are blue and not responsive to background contrast
- [x] On mobile, swatch icons in the palette in gradient view run out of the box and off the screen
- [x] Drag to reorder colors within palettes
- [x] Drag to reorder palettes
- [x] Delete confirmation dialog (removed - now deletes directly)
- [x] Toast notifications for actions (saved, deleted, etc.)
- [x] Remove the palette emoji when there are no palettes. does not keep with clean aesthetic of app.
- [x] No toast for choosing harmony colors - not needed

### Technical
- [x] Add accessibility features (ARIA labels, keyboard navigation with shortcuts)
- [x] Consider removing jQuery dependency (use vanilla JS)
- [x] Optimize for mobile touch interactions (44px touch targets, better feedback)
- [x] Add color space conversions (RGB ↔ HSL for harmonies)

### Polish
- [x] Add loading states for export
- [x] Better empty states (no palettes, no colors)
- [x] Smooth transitions between modes
- [x] Get rid of cheesy alert for deleting palette - just delete. Maybe allow undo shortcut key 

## Session History Notes

- Original file was `colors.html`, renamed to `index.html`
- Named "swatch" after exploring many alternatives
- Significant debugging around palette selection click handlers
- Root cause: invalid hex values (missing #) caused silent CSS failures
- Major polish update: Added toast notifications, loading states, empty states, smooth transitions, and fixed remaining jQuery bug
- Feature-rich update: Added color harmonies, keyboard shortcuts, and mobile accessibility improvements (removed color name display as not useful)
- SVG export/import: Full SVG file support with drag-and-drop, making palettes portable and shareable
- Polish refinements: Fixed SVG export aesthetics, improved drag-and-drop UX, contrast-sensitive export icon, overlay toggle state persistence
- Final features: Eye dropper tool (Chrome EyeDropper API), removed unnecessary toast notifications
- **ALL TODOS COMPLETE** - Project feature-complete and polished!
