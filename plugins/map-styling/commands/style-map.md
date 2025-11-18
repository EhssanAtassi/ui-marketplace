---
description: Interactive map styling wizard - generates custom map themes, markers, and popups
---

I'll help you create custom map styling for your Leaflet or Mapbox map.

## What This Command Does

This interactive wizard will help you:
1. Choose your mapping library (Leaflet or Mapbox GL JS)
2. Select a base theme (light, dark, satellite, custom)
3. Customize marker styles
4. Design popup layouts
5. Configure controls and overlays
6. Generate production-ready code

## How It Works

I'll ask you a series of questions about your requirements, then generate:
- Complete HTML/CSS/TypeScript code
- Custom marker icons (SVG or images)
- Styled popups and tooltips
- Map controls and UI elements
- Integration with your existing design system
- Performance optimization patterns

## Example Use Cases

**E-Commerce Store Locator:**
"I need a store locator map with custom markers for each store category, popups showing store hours and photos, and a search control."

**Real Estate Property Map:**
"Create a property listing map with price-based marker colors, rich popups with property images and details, and cluster markers by neighborhood."

**Delivery Tracking Map:**
"I need a dark-themed map showing delivery routes with animated markers, real-time location updates, and ETA information in popups."

**Tourism Guide Map:**
"Build a tourist attraction map with category-based markers (restaurants, hotels, museums), image galleries in popups, and custom controls for filtering."

## What I Need From You

To generate the best map styling for your needs, I'll ask about:

### 1. Map Library
- Leaflet (open-source, flexible)
- Mapbox GL JS (powerful, 3D support)
- OpenLayers (advanced GIS)
- Google Maps (familiar, widely used)

### 2. Base Theme
- Light mode (default streets)
- Dark mode (night theme)
- Satellite imagery
- Custom branded theme
- Terrain with elevation
- Minimalist/Clean

### 3. Marker Design
- Icon style (SVG, PNG, emoji, custom)
- Size and shape
- Colors (single or category-based)
- Clustering (enabled/disabled)
- Animation effects (pulse, bounce, none)
- Design token integration

### 4. Popup Layout
- Content type (simple text, rich media, cards)
- Include images/videos?
- Action buttons?
- Custom branding?
- Animations?

### 5. Features & Controls
- Zoom controls
- Layer switcher
- Search/geocoding
- Geolocation
- Drawing tools
- Fullscreen mode
- Custom controls

### 6. Performance Requirements
- Expected number of markers (< 100, 100-1000, 1000+)
- Mobile optimization needed?
- Offline support?
- Real-time updates?

### 7. Design System Integration
- Use existing design tokens?
- Match brand colors?
- Typography system?
- Component library (Angular Material, Ant Design, etc.)?

## What You'll Get

After answering the questions, I'll generate:

### 1. Map Initialization Code
```typescript
// Complete setup with your chosen library
const map = initializeMap({
  theme: 'dark',
  center: [lat, lng],
  zoom: 12,
  // ... custom configuration
});
```

### 2. Custom Marker Styles
```typescript
// SVG markers with your brand colors
const marker = createCustomMarker({
  color: 'var(--color-primary)',
  icon: 'location',
  size: 'medium'
});
```

### 3. Popup Components
```html
<!-- Styled popup templates -->
<div class="map-popup">
  <!-- Your custom layout -->
</div>
```

### 4. CSS Styling
```css
/* Complete styles with design tokens */
.leaflet-popup-content-wrapper {
  background: var(--color-surface);
  /* ... */
}
```

### 5. Integration Code
```typescript
// Angular/React/Vue component integration
@Component({
  selector: 'app-map',
  // ...
})
export class MapComponent implements OnInit {
  // Complete implementation
}
```

### 6. Documentation
- Usage instructions
- Customization guide
- Performance tips
- Accessibility notes
- Troubleshooting

## Quick Start Examples

If you want to skip the wizard and use a preset, choose from:

1. **Store Locator** - Multi-location business map
2. **Property Listings** - Real estate with filters
3. **Delivery Tracker** - Real-time vehicle tracking
4. **Event Map** - Location-based events
5. **Service Areas** - Coverage zones with polygons
6. **Tourist Guide** - Points of interest
7. **Fleet Management** - Vehicle tracking
8. **Restaurant Finder** - Food & dining locations

## Advanced Features

For complex requirements, I can also generate:

- **Data Visualization**: Choropleth maps, heat maps, density maps
- **3D Buildings**: Extruded buildings and terrain
- **Custom Basemaps**: Styled tiles matching your brand
- **Offline Maps**: Tile caching and offline support
- **Clustering Algorithms**: Category-based, grid-based, or custom
- **Route Drawing**: Polylines with animations
- **Geofencing**: Boundary visualization and triggers
- **Time-based Data**: Animated temporal visualizations

## Let's Get Started!

**Option 1: Quick Preset**
Tell me which preset you'd like (e.g., "Store Locator"), and I'll generate it with sensible defaults.

**Option 2: Custom Wizard**
Tell me about your map requirements, and I'll ask clarifying questions to build exactly what you need.

**Option 3: Specific Feature**
Tell me what specific feature you want to add to an existing map (e.g., "I need to add custom cluster markers").

What would you like to create?
