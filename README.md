# swatch

A lightweight, single-file color picker and gradient generator web application.

## Features

### Picker Mode
- Interactive RGB sliders for precise color selection
- Real-time hex and RGB value display
- Dynamic contrast adjustment for optimal readability
- Save colors to custom palettes (up to 6 colors per palette)

### Gradient Mode
- Create gradients from saved palettes
- Four gradient types: linear-right, linear-bottom, linear-diagonal, radial
- Live preview of generated gradients
- Export gradients as 1920x1080 PNG images
- Supports single-color palettes (solid color gradients)

### Data Persistence
- All palettes saved to browser localStorage
- Automatic persistence across sessions
- Auto-repair for malformed color data

## Usage

Simply open `index.html` in a web browser. No server or build process required.

### Picker Mode
1. Use the RGB sliders to select a color
2. Copy the hex value or click "add to palette" to save
3. Create and manage multiple palettes

### Gradient Mode
1. Click on any saved palette to load it
2. Choose a gradient type (linear-right, linear-bottom, linear-diagonal, radial)
3. Preview the gradient in real-time
4. Click "download" to export as PNG

## Technical Details

- Single HTML file with embedded CSS and JavaScript
- Dependencies: jQuery 3.7.1 (CDN), Google Fonts (Dongle, Koulen)
- Canvas API for gradient rendering and PNG export
- Inline SVG favicon (no external assets)
- Responsive design with sticky header
- localStorage for client-side persistence

## Browser Support

Modern browsers with localStorage and Canvas API support (Chrome, Firefox, Safari, Edge).
