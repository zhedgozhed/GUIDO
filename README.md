# DitherPro - Advanced Image Dithering Tool

A professional-grade web application for applying various dithering algorithms to images, with support for custom color palettes and multiple processing modes.

## Features

### Core Dithering Algorithms
- Threshold (no dither)
- Random noise dithering
- Bayer matrix dithering (2x2, 4x4, 8x8, 16x16)
- Blue noise dithering
- Floyd-Steinberg error diffusion
- Jarvis-Judice-Ninke error diffusion
- Atkinson dithering
- Simple 2D error diffusion
- Riemersma dithering (Hilbert curve)

### Processing Modes
- **Monochrome Mode** - Black and white dithering only
- **Color Mode** - Preserves original colors while applying dithering patterns
- **Palette Mode** - Quantizes images to selected color palettes with optional dithering

### Color Palettes
Includes 23 curated color palettes across two categories:

**Abstract**
- Crystalline 2-7 (various color counts)

**Contrasts**
- Burned, Citrus, Citrus 2, Electric, Flare, Fruity
- Lime, Lime 2, Poison, Pop, Pop 2, Sweets, Sweets 2
- Tangerine, Tangerine 2, Ultravio, Ultravio 2

### Image Adjustments
- Threshold control
- Brightness
- Contrast
- Midtones
- Highlights
- Shadows
- Gamma correction

### User Interface
- Split-panel layout with workspace and control sidebar
- Zoom controls (in, out, fit to view)
- Original/Dithered view toggle
- Real-time preview with throttled rendering
- Image information display
- Processing time metrics
- Theme support (Dark, Light, System) with localStorage persistence

### File Operations
- Import images (drag and drop via file picker)
- Export dithered results as PNG
- Reset to default test pattern

## Technical Implementation

### Architecture
- Pure HTML/CSS/JavaScript implementation
- No external dependencies
- Canvas-based image processing
- Throttled rendering for performance
- Modular algorithm organization

### Color Processing
- RGB to HSL conversions for tone adjustments
- Gamma-corrected color space handling
- Euclidean distance for color quantization
- Two-color interpolation for palette dithering

### Dithering Methods

**Ordered Dithering**
- Uses threshold matrices (Bayer, blue noise)
- Pixel-independent processing
- Fast and parallelizable

**Error Diffusion**
- Sequential pixel processing
- Error propagation to neighbors
- Multiple matrix patterns (Floyd-Steinberg, Jarvis, Atkinson)

**Riemersma Dithering**
- Hilbert curve traversal
- Error diffusion along space-filling curve
- Organic, noise-like results

## Usage Guide

1. **Load an Image**
   - Click "IMPORT" or use the file picker
   - Supports common image formats

2. **Select Mode**
   - Monochrome: Black and white output
   - Color: Preserve original colors with dithering
   - Palette: Use predefined color palettes

3. **Choose Algorithm**
   - Select from 10 dithering algorithms
   - Algorithm-specific controls appear automatically

4. **Adjust Settings**
   - Fine-tune with adjustment sliders
   - Enable/disable gamma correction
   - Toggle dithering on/off

5. **Apply Palette (Palette Mode)**
   - Choose from Abstract or Contrasts categories
   - Toggle "APPLY DITHERING TO PALETTE" for dithered quantization

6. **Export Result**
   - Click "EXPORT" to save as PNG
   - Original image dimensions preserved

## Keyboard Shortcuts
- Import: Click IMPORT button
- Export: Click EXPORT button
- Reset: Click RESET button
- Zoom: Use +/- buttons or FIT

## Browser Compatibility
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Requires JavaScript enabled
- WebGL not required

## Performance Notes
- Large images (>4K) may cause temporary UI slowdown
- Processing time displayed in status bar
- Blue noise generation cached for performance
- Throttled rendering prevents excessive recalculations

## Development

### Project Structure
- Single HTML file with embedded CSS and JavaScript
- Modular algorithm organization
- State management with central parameters object

### Key Components
- `ColorImage` / `GrayImage` classes for image data
- `PALETTES` database with all color schemes
- Algorithm objects for monochrome, color, and palette modes
- UI state management with localStorage

### Adding New Palettes
Add to the `PALETTES` object with format:
```javascript
paletteKey: {
    category: "CategoryName",
    name: "Palette Name",
    color_count: 8,
    colors: [
        { r: 0, g: 0, b: 0 },
        // ... more colors
    ]
}
```

## License
Free for personal and commercial use.

## Credits
- Dithering algorithms based on "Ditherpunk" article by Surma
- Color palettes from various sources like Dither-Boy
- Interface design inspired by professional image editing tools

## Version History
- v6.0 - Complete algorithm fixes, palette improvements, UI enhancements
- v5.0 - Color mode fixes, gamma correction, HSL adjustments
- v4.0 - Palette integration, mode decoupling
- v3.0 - Initial color palette support
- v2.0 - Performance improvements, bug fixes
- v1.0 - Basic dithering algorithms
