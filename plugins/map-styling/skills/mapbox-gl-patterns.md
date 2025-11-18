---
name: Mapbox GL JS Patterns
description: Master Mapbox GL JS styling with custom themes, 3D visualization, data-driven styling, markers, popups, animations, and performance optimization
tags: [mapbox, mapping, geospatial, visualization, 3D, webgl]
---

# Mapbox GL JS Styling Patterns Library

A comprehensive guide to styling and visualizing maps using Mapbox GL JS, covering custom styles, data-driven visualization, 3D terrain, animations, and performance optimization.

## Table of Contents

1. [Custom Map Styles](#custom-map-styles)
2. [Data-Driven Styling](#data-driven-styling)
3. [Custom Markers and Popups](#custom-markers-and-popups)
4. [3D Buildings and Terrain](#3d-buildings-and-terrain)
5. [Animated Layers](#animated-layers)
6. [Heat Maps](#heat-maps)
7. [Dark Mode Implementation](#dark-mode-implementation)
8. [Performance Optimization](#performance-optimization)

---

## Custom Map Styles

### Basic Map Initialization with Custom Style

```typescript
/**
 * @swagger
 * /api/map/initialize:
 *   post:
 *     summary: Initialize Mapbox GL JS map with custom style
 *     description: Creates a Mapbox map instance with custom styling, pitch, and bearing
 *     tags: [Mapbox, Initialization]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               container:
 *                 type: string
 *                 description: DOM element ID for map container
 *               style:
 *                 type: string
 *                 description: Mapbox style URL
 *               center:
 *                 type: array
 *                 items:
 *                   type: number
 *                 description: Map center coordinates [lng, lat]
 *               zoom:
 *                 type: number
 *                 description: Initial zoom level
 *     responses:
 *       200:
 *         description: Map initialized successfully
 */
import mapboxgl from 'mapbox-gl';

mapboxgl.accessToken = 'YOUR_MAPBOX_ACCESS_TOKEN';

/**
 * Initialize map with custom style
 * @param container - Container element ID
 * @returns Mapbox map instance
 */
function initializeMap(container: string): mapboxgl.Map {
  const map = new mapboxgl.Map({
    container,
    style: 'mapbox://styles/mapbox/dark-v11', // or custom style URL
    center: [-74.5, 40],
    zoom: 9,
    pitch: 45,
    bearing: -17.6,
    antialias: true
  });

  return map;
}
```

### Custom Style JSON Definition

```typescript
/**
 * @swagger
 * /api/map/custom-style:
 *   get:
 *     summary: Get custom Mapbox style JSON
 *     description: Returns a complete custom style definition for dark theme
 *     tags: [Mapbox, Styles]
 *     responses:
 *       200:
 *         description: Custom style JSON object
 *         content:
 *           application/json:
 *             schema:
 *               type: object
 *               properties:
 *                 version:
 *                   type: number
 *                 name:
 *                   type: string
 *                 sources:
 *                   type: object
 *                 layers:
 *                   type: array
 */

// Custom style JSON with dark theme
const customStyle = {
  version: 8,
  name: 'Custom Dark Style',
  metadata: {
    'mapbox:autocomposite': true
  },
  sources: {
    'mapbox-streets': {
      type: 'vector',
      url: 'mapbox://mapbox.mapbox-streets-v8'
    }
  },
  layers: [
    {
      id: 'background',
      type: 'background',
      paint: {
        'background-color': '#1a1a2e'
      }
    },
    {
      id: 'water',
      type: 'fill',
      source: 'mapbox-streets',
      'source-layer': 'water',
      paint: {
        'fill-color': '#16213e',
        'fill-opacity': 0.8
      }
    },
    {
      id: 'parks',
      type: 'fill',
      source: 'mapbox-streets',
      'source-layer': 'landuse',
      filter: ['==', 'class', 'park'],
      paint: {
        'fill-color': '#0f3460',
        'fill-opacity': 0.6
      }
    },
    {
      id: 'roads',
      type: 'line',
      source: 'mapbox-streets',
      'source-layer': 'road',
      paint: {
        'line-color': '#e94560',
        'line-width': 2,
        'line-opacity': 0.7
      }
    },
    {
      id: 'buildings',
      type: 'fill-extrusion',
      source: 'mapbox-streets',
      'source-layer': 'building',
      paint: {
        'fill-extrusion-color': '#533483',
        'fill-extrusion-height': ['get', 'height'],
        'fill-extrusion-base': ['get', 'min_height'],
        'fill-extrusion-opacity': 0.6
      }
    }
  ]
};
```

---

## Data-Driven Styling

### Choropleth Visualization with Expressions

```typescript
/**
 * @swagger
 * /api/map/choropleth:
 *   post:
 *     summary: Add choropleth layer to map
 *     description: Creates a data-driven choropleth layer with interpolated colors based on density values
 *     tags: [Mapbox, Visualization]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               sourceId:
 *                 type: string
 *                 description: GeoJSON source identifier
 *               layerId:
 *                 type: string
 *                 description: Layer identifier
 *               dataUrl:
 *                 type: string
 *                 description: URL to GeoJSON data
 *     responses:
 *       200:
 *         description: Choropleth layer added successfully
 */

interface FeatureData {
  type: 'Feature';
  properties: {
    population: number;
    density: number;
    category: string;
  };
  geometry: any;
}

map.on('load', () => {
  // Add data source
  map.addSource('population', {
    type: 'geojson',
    data: '/data/population.geojson'
  });

  // Choropleth layer with data-driven colors
  map.addLayer({
    id: 'population-layer',
    type: 'fill',
    source: 'population',
    paint: {
      'fill-color': [
        'interpolate',
        ['linear'],
        ['get', 'density'],
        0, '#ffffcc',
        10, '#ffeda0',
        20, '#fed976',
        50, '#feb24c',
        100, '#fd8d3c',
        200, '#fc4e2a',
        500, '#e31a1c',
        1000, '#bd0026',
        2000, '#800026'
      ],
      'fill-opacity': [
        'case',
        ['boolean', ['feature-state', 'hover'], false],
        0.9,
        0.7
      ],
      'fill-outline-color': '#ffffff'
    }
  });
});
```

### Data-Driven Circle Markers

```typescript
/**
 * @swagger
 * /api/map/data-driven-markers:
 *   post:
 *     summary: Add data-driven circle markers
 *     description: Creates circle markers with size and color based on data properties
 *     tags: [Mapbox, Markers]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               sourceId:
 *                 type: string
 *               layerId:
 *                 type: string
 *               populationField:
 *                 type: string
 *               categoryField:
 *                 type: string
 *     responses:
 *       200:
 *         description: Markers added successfully
 */

map.on('load', () => {
  // Data-driven circle markers
  map.addLayer({
    id: 'population-points',
    type: 'circle',
    source: 'population',
    paint: {
      // Size based on population
      'circle-radius': [
        'interpolate',
        ['linear'],
        ['get', 'population'],
        0, 4,
        1000, 8,
        10000, 16,
        100000, 32
      ],
      // Color based on category
      'circle-color': [
        'match',
        ['get', 'category'],
        'urban', '#3b82f6',
        'suburban', '#10b981',
        'rural', '#f59e0b',
        '#6b7280' // default
      ],
      'circle-stroke-width': 2,
      'circle-stroke-color': '#ffffff',
      'circle-opacity': 0.8
    }
  });
});
```

### Interactive Hover Effects

```typescript
/**
 * @swagger
 * /api/map/hover-effects:
 *   post:
 *     summary: Add interactive hover effects to layer
 *     description: Implements hover state changes using feature-state
 *     tags: [Mapbox, Interaction]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               layerId:
 *                 type: string
 *                 description: Layer to add hover effects
 *               sourceId:
 *                 type: string
 *                 description: Source identifier
 *     responses:
 *       200:
 *         description: Hover effects added successfully
 */

// Add hover effect with feature state
let hoveredStateId: string | number | null = null;

map.on('mousemove', 'population-layer', (e) => {
  if (e.features && e.features.length > 0) {
    if (hoveredStateId !== null) {
      map.setFeatureState(
        { source: 'population', id: hoveredStateId },
        { hover: false }
      );
    }
    hoveredStateId = e.features[0].id!;
    map.setFeatureState(
      { source: 'population', id: hoveredStateId },
      { hover: true }
    );
  }
});

map.on('mouseleave', 'population-layer', () => {
  if (hoveredStateId !== null) {
    map.setFeatureState(
      { source: 'population', id: hoveredStateId },
      { hover: false }
    );
  }
  hoveredStateId = null;
});
```

---

## Custom Markers and Popups

### HTML Custom Markers

```typescript
/**
 * @swagger
 * /api/map/custom-markers:
 *   post:
 *     summary: Create custom HTML markers
 *     description: Creates custom markers using HTML elements with labels and pins
 *     tags: [Mapbox, Markers]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               locations:
 *                 type: array
 *                 items:
 *                   type: object
 *                   properties:
 *                     lng:
 *                       type: number
 *                     lat:
 *                       type: number
 *                     color:
 *                       type: string
 *                     label:
 *                       type: string
 *     responses:
 *       200:
 *         description: Custom markers created successfully
 */

/**
 * Create custom marker element
 * @param color - Marker color
 * @param label - Optional label
 * @returns HTML element for marker
 */
function createCustomMarker(color: string, label?: string): HTMLElement {
  const el = document.createElement('div');
  el.className = 'custom-mapbox-marker';
  el.style.backgroundColor = color;

  if (label) {
    el.innerHTML = `
      <div class="marker-label">${label}</div>
      <div class="marker-pin"></div>
    `;
  }

  return el;
}

/**
 * Create styled popup
 * @param title - Popup title
 * @param content - Popup content
 * @returns Mapbox popup instance
 */
function createStyledPopup(title: string, content: string): mapboxgl.Popup {
  return new mapboxgl.Popup({
    className: 'custom-mapbox-popup',
    closeButton: true,
    closeOnClick: false,
    maxWidth: '300px',
    offset: 25
  }).setHTML(`
    <div class="popup-container">
      <div class="popup-header">
        <h3>${title}</h3>
        <span class="popup-badge">New</span>
      </div>
      <div class="popup-content">
        ${content}
      </div>
      <div class="popup-actions">
        <button class="popup-btn primary">View</button>
        <button class="popup-btn secondary">Share</button>
      </div>
    </div>
  `);
}

// Add markers with popups
interface Location {
  lng: number;
  lat: number;
  color: string;
  label: string;
  name: string;
  description: string;
}

const locations: Location[] = [
  {
    lng: -74.5,
    lat: 40,
    color: '#3b82f6',
    label: 'A',
    name: 'Location A',
    description: 'Description for location A'
  }
  // ... more locations
];

locations.forEach(location => {
  const marker = new mapboxgl.Marker({
    element: createCustomMarker(location.color, location.label),
    anchor: 'bottom'
  })
    .setLngLat([location.lng, location.lat])
    .setPopup(createStyledPopup(location.name, location.description))
    .addTo(map);
});
```

### Custom Marker and Popup CSS

```css
/**
 * Mapbox GL JS custom marker and popup styles
 * @description Modern styling for Mapbox markers and popups with animations
 */

/* Custom Marker Styles */
.custom-mapbox-marker {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
  transition: transform 0.2s;
  position: relative;
}

.custom-mapbox-marker:hover {
  transform: scale(1.1);
}

.marker-label {
  color: white;
  font-weight: 600;
  font-size: 14px;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

.marker-pin {
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 8px solid transparent;
  border-right: 8px solid transparent;
  border-top: 12px solid currentColor;
}

/* Pulse animation for active marker */
.custom-mapbox-marker.active::before {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: inherit;
  animation: markerPulse 2s infinite;
}

@keyframes markerPulse {
  0% {
    transform: scale(1);
    opacity: 0.8;
  }
  50% {
    transform: scale(1.5);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 0;
  }
}

/* Custom Popup Styles */
.custom-mapbox-popup .mapboxgl-popup-content {
  padding: 0;
  border-radius: 12px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
  overflow: hidden;
  min-width: 280px;
}

.custom-mapbox-popup .mapboxgl-popup-close-button {
  font-size: 24px;
  padding: 8px 12px;
  color: #6b7280;
  z-index: 10;
}

.custom-mapbox-popup .mapboxgl-popup-close-button:hover {
  background: rgba(0, 0, 0, 0.05);
  color: #374151;
}

.custom-mapbox-popup .mapboxgl-popup-tip {
  border-top-color: #f9fafb;
}

.popup-container {
  background: white;
}

.popup-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.popup-header h3 {
  margin: 0;
  font-size: 18px;
  font-weight: 600;
}

.popup-badge {
  background: rgba(255, 255, 255, 0.3);
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 500;
}

.popup-content {
  padding: 16px;
  color: #374151;
  line-height: 1.6;
}

.popup-actions {
  display: flex;
  gap: 8px;
  padding: 12px 16px;
  background: #f9fafb;
  border-top: 1px solid #e5e7eb;
}

.popup-btn {
  flex: 1;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.popup-btn.primary {
  background: #667eea;
  color: white;
}

.popup-btn.primary:hover {
  background: #5568d3;
  transform: translateY(-1px);
}

.popup-btn.secondary {
  background: white;
  color: #667eea;
  border: 1px solid #667eea;
}

.popup-btn.secondary:hover {
  background: #f3f4f6;
}
```

---

## 3D Buildings and Terrain

### 3D Terrain and Buildings Implementation

```typescript
/**
 * @swagger
 * /api/map/3d-terrain:
 *   post:
 *     summary: Add 3D terrain and buildings to map
 *     description: Adds 3D terrain elevation and extruded buildings with custom styling
 *     tags: [Mapbox, 3D, Visualization]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               exaggeration:
 *                 type: number
 *                 description: Terrain exaggeration multiplier (default 1.5)
 *               minZoom:
 *                 type: number
 *                 description: Minimum zoom for 3D buildings (default 15)
 *     responses:
 *       200:
 *         description: 3D terrain and buildings added successfully
 */

map.on('load', () => {
  // Add 3D terrain
  map.addSource('mapbox-dem', {
    type: 'raster-dem',
    url: 'mapbox://mapbox.mapbox-terrain-dem-v1',
    tileSize: 512,
    maxzoom: 14
  });

  map.setTerrain({
    source: 'mapbox-dem',
    exaggeration: 1.5
  });

  // Add 3D buildings layer
  map.addLayer({
    id: '3d-buildings',
    source: 'composite',
    'source-layer': 'building',
    filter: ['==', 'extrude', 'true'],
    type: 'fill-extrusion',
    minzoom: 15,
    paint: {
      // Height-based color gradient
      'fill-extrusion-color': [
        'interpolate',
        ['linear'],
        ['get', 'height'],
        0, '#e0e0e0',
        50, '#b0b0b0',
        100, '#808080',
        200, '#606060'
      ],
      // Smooth height transition on zoom
      'fill-extrusion-height': [
        'interpolate',
        ['linear'],
        ['zoom'],
        15, 0,
        15.05, ['get', 'height']
      ],
      // Building base height
      'fill-extrusion-base': [
        'interpolate',
        ['linear'],
        ['zoom'],
        15, 0,
        15.05, ['get', 'min_height']
      ],
      'fill-extrusion-opacity': 0.8,
      'fill-extrusion-vertical-gradient': true
    }
  });

  // Add sky layer for atmosphere
  map.addLayer({
    id: 'sky',
    type: 'sky',
    paint: {
      'sky-type': 'atmosphere',
      'sky-atmosphere-sun': [0.0, 90.0],
      'sky-atmosphere-sun-intensity': 15
    }
  });
});
```

### Advanced 3D Building Styling

```typescript
/**
 * @swagger
 * /api/map/advanced-3d-buildings:
 *   post:
 *     summary: Add advanced 3D building visualization
 *     description: Creates sophisticated 3D building visualization with lighting and shadows
 *     tags: [Mapbox, 3D, Buildings]
 */

/**
 * Add advanced 3D buildings with custom colors and lighting
 */
function addAdvanced3DBuildings(): void {
  map.addLayer({
    id: '3d-buildings-advanced',
    source: 'composite',
    'source-layer': 'building',
    filter: ['==', 'extrude', 'true'],
    type: 'fill-extrusion',
    minzoom: 15,
    paint: {
      // Color based on building type
      'fill-extrusion-color': [
        'match',
        ['get', 'type'],
        'residential', '#6366f1',
        'commercial', '#f59e0b',
        'industrial', '#8b5cf6',
        'office', '#3b82f6',
        '#94a3b8' // default
      ],
      'fill-extrusion-height': [
        'interpolate',
        ['linear'],
        ['zoom'],
        15, 0,
        15.05, ['*', ['get', 'height'], 1.2]
      ],
      'fill-extrusion-base': ['get', 'min_height'],
      'fill-extrusion-opacity': 0.85,
      // Enable vertical gradient for realistic lighting
      'fill-extrusion-vertical-gradient': true,
      // Ambient occlusion for shadows
      'fill-extrusion-ambient-occlusion-intensity': 0.3,
      'fill-extrusion-ambient-occlusion-radius': 3
    }
  });
}
```

---

## Animated Layers

### Pulse Animation

```typescript
/**
 * @swagger
 * /api/map/animate-pulse:
 *   post:
 *     summary: Animate layer with pulsing effect
 *     description: Creates a continuous pulsing animation on circle markers
 *     tags: [Mapbox, Animation]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               layerId:
 *                 type: string
 *                 description: Layer ID to animate
 *               minRadius:
 *                 type: number
 *                 description: Minimum radius (default 5)
 *               maxRadius:
 *                 type: number
 *                 description: Maximum radius (default 20)
 *     responses:
 *       200:
 *         description: Animation started successfully
 */

/**
 * Animate circle radius pulsing effect
 * @param layerId - Layer ID to animate
 */
function animatePulse(layerId: string): void {
  let radius = 5;
  let growing = true;

  function pulse() {
    if (growing) {
      radius += 0.5;
      if (radius >= 20) growing = false;
    } else {
      radius -= 0.5;
      if (radius <= 5) growing = true;
    }

    map.setPaintProperty(layerId, 'circle-radius', radius);
    requestAnimationFrame(pulse);
  }

  pulse();
}
```

### Line Flow Animation

```typescript
/**
 * @swagger
 * /api/map/animate-line-flow:
 *   post:
 *     summary: Animate line layer with flow effect
 *     description: Creates animated flowing lines using dash array animation
 *     tags: [Mapbox, Animation, Lines]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               layerId:
 *                 type: string
 *                 description: Line layer ID to animate
 *     responses:
 *       200:
 *         description: Line flow animation started
 */

/**
 * Animate line movement (flow effect)
 * @param layerId - Layer ID to animate
 */
function animateLineFlow(layerId: string): void {
  let offset = 0;

  function animate() {
    offset = (offset + 1) % 20;

    map.setPaintProperty(layerId, 'line-dasharray', [0, offset, 20]);
    requestAnimationFrame(animate);
  }

  animate();
}
```

### Smooth Property Transitions

```typescript
/**
 * @swagger
 * /api/map/property-transitions:
 *   post:
 *     summary: Configure smooth property transitions
 *     description: Sets up smooth transitions for layer property changes
 *     tags: [Mapbox, Animation, Transitions]
 */

// Smooth property transitions
map.on('load', () => {
  map.addLayer({
    id: 'animated-layer',
    type: 'circle',
    source: 'points',
    paint: {
      'circle-radius': {
        base: 1.75,
        stops: [
          [12, 2],
          [22, 180]
        ]
      },
      'circle-color': '#3b82f6',
      // Opacity transition configuration
      'circle-opacity-transition': {
        duration: 1000,
        delay: 0
      },
      // Radius transition configuration
      'circle-radius-transition': {
        duration: 1000,
        delay: 0
      }
    }
  });
});
```

### Path Animation Along Route

```typescript
/**
 * @swagger
 * /api/map/animate-route:
 *   post:
 *     summary: Animate marker along route path
 *     description: Animates a marker following a GeoJSON line path
 *     tags: [Mapbox, Animation, Routes]
 */

/**
 * Animate point along a route
 * @param route - GeoJSON LineString coordinates
 * @param duration - Animation duration in milliseconds
 */
function animateAlongRoute(
  route: number[][],
  duration: number = 10000
): void {
  const start = Date.now();

  // Create point source
  map.addSource('point', {
    type: 'geojson',
    data: {
      type: 'FeatureCollection',
      features: [{
        type: 'Feature',
        properties: {},
        geometry: {
          type: 'Point',
          coordinates: route[0]
        }
      }]
    }
  });

  // Add point layer
  map.addLayer({
    id: 'point',
    source: 'point',
    type: 'circle',
    paint: {
      'circle-radius': 10,
      'circle-color': '#3b82f6',
      'circle-stroke-width': 2,
      'circle-stroke-color': '#ffffff'
    }
  });

  function animate() {
    const elapsed = Date.now() - start;
    const progress = elapsed / duration;

    if (progress < 1) {
      // Calculate current position along route
      const index = Math.floor(progress * (route.length - 1));
      const nextIndex = Math.min(index + 1, route.length - 1);
      const segmentProgress = (progress * (route.length - 1)) - index;

      const lng = route[index][0] +
        (route[nextIndex][0] - route[index][0]) * segmentProgress;
      const lat = route[index][1] +
        (route[nextIndex][1] - route[index][1]) * segmentProgress;

      // Update point position
      const pointSource = map.getSource('point') as mapboxgl.GeoJSONSource;
      pointSource.setData({
        type: 'FeatureCollection',
        features: [{
          type: 'Feature',
          properties: {},
          geometry: {
            type: 'Point',
            coordinates: [lng, lat]
          }
        }]
      });

      requestAnimationFrame(animate);
    }
  }

  animate();
}
```

---

## Heat Maps

### Basic Heat Map Implementation

```typescript
/**
 * @swagger
 * /api/map/heatmap:
 *   post:
 *     summary: Add heat map visualization
 *     description: Creates a heat map layer with custom color gradients and density calculation
 *     tags: [Mapbox, Heatmap, Visualization]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               sourceId:
 *                 type: string
 *                 description: GeoJSON source identifier
 *               dataUrl:
 *                 type: string
 *                 description: URL to point data
 *               weightField:
 *                 type: string
 *                 description: Property field for heatmap weight
 *     responses:
 *       200:
 *         description: Heat map created successfully
 */

map.on('load', () => {
  // Add heat map source
  map.addSource('earthquakes', {
    type: 'geojson',
    data: '/data/earthquakes.geojson'
  });

  // Heat map layer
  map.addLayer({
    id: 'earthquakes-heat',
    type: 'heatmap',
    source: 'earthquakes',
    maxzoom: 15,
    paint: {
      // Increase weight as diameter increases
      'heatmap-weight': [
        'interpolate',
        ['linear'],
        ['get', 'mag'],
        0, 0,
        6, 1
      ],
      // Increase intensity as zoom level increases
      'heatmap-intensity': [
        'interpolate',
        ['linear'],
        ['zoom'],
        0, 1,
        15, 3
      ],
      // Custom color gradient
      'heatmap-color': [
        'interpolate',
        ['linear'],
        ['heatmap-density'],
        0, 'rgba(33, 102, 172, 0)',
        0.2, 'rgb(103, 169, 207)',
        0.4, 'rgb(209, 229, 240)',
        0.6, 'rgb(253, 219, 199)',
        0.8, 'rgb(239, 138, 98)',
        1, 'rgb(178, 24, 43)'
      ],
      // Adjust radius by zoom level
      'heatmap-radius': [
        'interpolate',
        ['linear'],
        ['zoom'],
        0, 2,
        15, 20
      ],
      // Transition from heatmap to circle layer
      'heatmap-opacity': [
        'interpolate',
        ['linear'],
        ['zoom'],
        7, 1,
        15, 0
      ]
    }
  });

  // Add circle layer for high zoom levels
  map.addLayer({
    id: 'earthquakes-point',
    type: 'circle',
    source: 'earthquakes',
    minzoom: 7,
    paint: {
      'circle-radius': [
        'interpolate',
        ['linear'],
        ['get', 'mag'],
        0, 2,
        6, 20
      ],
      'circle-color': [
        'interpolate',
        ['linear'],
        ['get', 'mag'],
        0, '#ffffb2',
        3, '#feb24c',
        5, '#f03b20',
        7, '#bd0026'
      ],
      'circle-stroke-color': 'white',
      'circle-stroke-width': 1,
      'circle-opacity': [
        'interpolate',
        ['linear'],
        ['zoom'],
        7, 0,
        15, 1
      ]
    }
  });
});
```

### Custom Heat Map Color Schemes

```typescript
/**
 * @swagger
 * /api/map/heatmap-colors:
 *   get:
 *     summary: Get predefined heat map color schemes
 *     description: Returns various color gradient configurations for heat maps
 *     tags: [Mapbox, Heatmap, Colors]
 */

/**
 * Predefined heat map color schemes
 */
const heatmapColorSchemes = {
  // Blue to red (temperature)
  temperature: [
    'interpolate',
    ['linear'],
    ['heatmap-density'],
    0, 'rgba(33, 102, 172, 0)',
    0.2, 'rgb(103, 169, 207)',
    0.4, 'rgb(209, 229, 240)',
    0.6, 'rgb(253, 219, 199)',
    0.8, 'rgb(239, 138, 98)',
    1, 'rgb(178, 24, 43)'
  ],

  // Yellow to red (fire)
  fire: [
    'interpolate',
    ['linear'],
    ['heatmap-density'],
    0, 'rgba(255, 255, 255, 0)',
    0.2, '#ffffb2',
    0.4, '#fed976',
    0.6, '#feb24c',
    0.8, '#fd8d3c',
    1, '#e31a1c'
  ],

  // Viridis (scientific)
  viridis: [
    'interpolate',
    ['linear'],
    ['heatmap-density'],
    0, 'rgba(68, 1, 84, 0)',
    0.25, '#3e4989',
    0.5, '#26828e',
    0.75, '#6ece58',
    1, '#fde725'
  ],

  // Purple to orange (sunset)
  sunset: [
    'interpolate',
    ['linear'],
    ['heatmap-density'],
    0, 'rgba(103, 0, 31, 0)',
    0.2, '#bd0026',
    0.4, '#f03b20',
    0.6, '#fd8d3c',
    0.8, '#fecc5c',
    1, '#ffffb2'
  ]
};

/**
 * Apply color scheme to heat map layer
 * @param layerId - Heat map layer ID
 * @param scheme - Color scheme name
 */
function applyHeatmapColorScheme(
  layerId: string,
  scheme: keyof typeof heatmapColorSchemes
): void {
  map.setPaintProperty(
    layerId,
    'heatmap-color',
    heatmapColorSchemes[scheme]
  );
}
```

---

## Dark Mode Implementation

### Mapbox Style Switching

```typescript
/**
 * @swagger
 * /api/map/theme-switch:
 *   post:
 *     summary: Switch map theme/style
 *     description: Switches between light, dark, and satellite Mapbox styles while preserving view
 *     tags: [Mapbox, Theme, Style]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               style:
 *                 type: string
 *                 enum: [light, dark, satellite]
 *                 description: Style to switch to
 *     responses:
 *       200:
 *         description: Style switched successfully
 */

const mapboxStyles = {
  light: 'mapbox://styles/mapbox/streets-v12',
  dark: 'mapbox://styles/mapbox/dark-v11',
  satellite: 'mapbox://styles/mapbox/satellite-streets-v12'
};

let currentStyle: keyof typeof mapboxStyles = 'light';

/**
 * Switch Mapbox style
 * @param style - Style to switch to
 */
function switchMapboxStyle(style: keyof typeof mapboxStyles): void {
  if (currentStyle === style) return;

  // Get current center and zoom
  const center = map.getCenter();
  const zoom = map.getZoom();
  const bearing = map.getBearing();
  const pitch = map.getPitch();

  // Set new style
  map.setStyle(mapboxStyles[style]);

  // Restore view after style loads
  map.once('styledata', () => {
    map.jumpTo({
      center,
      zoom,
      bearing,
      pitch
    });
  });

  currentStyle = style;

  // Update UI
  document.body.setAttribute('data-theme', style);
}
```

### Animated Theme Transition

```typescript
/**
 * @swagger
 * /api/map/animated-theme-switch:
 *   post:
 *     summary: Switch theme with animation
 *     description: Provides smooth animated transition between map themes
 *     tags: [Mapbox, Theme, Animation]
 */

/**
 * Switch theme with fade animation
 * @param newStyle - Style to switch to
 * @param duration - Transition duration in milliseconds
 */
function switchThemeAnimated(
  newStyle: keyof typeof mapboxStyles,
  duration: number = 1000
): void {
  const container = map.getContainer();

  // Create overlay for fade effect
  const overlay = document.createElement('div');
  overlay.style.cssText = `
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: black;
    opacity: 0;
    pointer-events: none;
    transition: opacity ${duration / 2}ms;
    z-index: 1000;
  `;
  container.appendChild(overlay);

  // Fade out
  requestAnimationFrame(() => {
    overlay.style.opacity = '1';
  });

  // Switch style at midpoint
  setTimeout(() => {
    switchMapboxStyle(newStyle);

    // Fade in
    setTimeout(() => {
      overlay.style.opacity = '0';
      setTimeout(() => overlay.remove(), duration / 2);
    }, 100);
  }, duration / 2);
}
```

---

## Performance Optimization

### Vector Tiles and Clustering

```typescript
/**
 * @swagger
 * /api/map/optimize-performance:
 *   post:
 *     summary: Optimize map performance
 *     description: Implements performance optimizations including clustering and vector tiles
 *     tags: [Mapbox, Performance]
 */

// Use vector tiles instead of GeoJSON when possible
map.addSource('large-dataset', {
  type: 'vector',
  url: 'mapbox://username.tileset-id'
});

// Cluster points for better performance
map.addSource('clustered-points', {
  type: 'geojson',
  data: pointsData,
  cluster: true,
  clusterMaxZoom: 14,
  clusterRadius: 50
});

// Add cluster circles
map.addLayer({
  id: 'clusters',
  type: 'circle',
  source: 'clustered-points',
  filter: ['has', 'point_count'],
  paint: {
    'circle-color': [
      'step',
      ['get', 'point_count'],
      '#51bbd6',
      100, '#f1f075',
      750, '#f28cb1'
    ],
    'circle-radius': [
      'step',
      ['get', 'point_count'],
      20,
      100, 30,
      750, 40
    ]
  }
});

// Add cluster count labels
map.addLayer({
  id: 'cluster-count',
  type: 'symbol',
  source: 'clustered-points',
  filter: ['has', 'point_count'],
  layout: {
    'text-field': '{point_count_abbreviated}',
    'text-font': ['DIN Offc Pro Medium', 'Arial Unicode MS Bold'],
    'text-size': 12
  }
});
```

### Efficient Data Updates

```typescript
/**
 * @swagger
 * /api/map/efficient-updates:
 *   post:
 *     summary: Efficiently update map data
 *     description: Demonstrates efficient techniques for updating map data without re-rendering
 *     tags: [Mapbox, Performance, Updates]
 */

/**
 * Efficiently update GeoJSON source
 * @param sourceId - Source identifier
 * @param newData - New GeoJSON data
 */
function updateSourceData(sourceId: string, newData: any): void {
  const source = map.getSource(sourceId) as mapboxgl.GeoJSONSource;
  if (source) {
    source.setData(newData);
  }
}

/**
 * Debounce expensive operations
 * @param func - Function to debounce
 * @param wait - Wait time in milliseconds
 */
function debounce<T extends (...args: any[]) => any>(
  func: T,
  wait: number
): (...args: Parameters<T>) => void {
  let timeout: NodeJS.Timeout;
  return function(this: any, ...args: Parameters<T>) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), wait);
  };
}

// Debounced map update handler
map.on('moveend', debounce(() => {
  // Update data based on viewport
  const bounds = map.getBounds();
  fetchDataInBounds(bounds).then(data => {
    updateSourceData('dynamic-source', data);
  });
}, 300));
```

### Layer Filtering and Visibility

```typescript
/**
 * @swagger
 * /api/map/layer-filtering:
 *   post:
 *     summary: Filter layers for performance
 *     description: Use layer filters to limit rendered features and improve performance
 *     tags: [Mapbox, Performance, Filtering]
 */

// Limit features rendered based on zoom
map.setFilter('layer-id', [
  'all',
  ['>=', 'zoom', 10],
  ['<=', 'zoom', 16]
]);

// Filter by property values
map.setFilter('population-layer', [
  'all',
  ['>=', ['get', 'population'], 10000],
  ['<', ['get', 'population'], 1000000]
]);

// Toggle layer visibility
function toggleLayerVisibility(layerId: string, visible: boolean): void {
  map.setLayoutProperty(
    layerId,
    'visibility',
    visible ? 'visible' : 'none'
  );
}
```

### Sprite Sheets for Icons

```typescript
/**
 * @swagger
 * /api/map/sprite-optimization:
 *   post:
 *     summary: Optimize icons with sprite sheets
 *     description: Load and use sprite sheets for efficient icon rendering
 *     tags: [Mapbox, Performance, Icons]
 */

/**
 * Load custom icon sprite
 * @param name - Icon name
 * @param url - Icon image URL
 */
function loadIconSprite(name: string, url: string): Promise<void> {
  return new Promise((resolve, reject) => {
    map.loadImage(url, (error, image) => {
      if (error) {
        reject(error);
        return;
      }
      if (image) {
        map.addImage(name, image);
        resolve();
      }
    });
  });
}

// Load multiple icons efficiently
async function loadAllIcons(): Promise<void> {
  const icons = [
    { name: 'marker-restaurant', url: '/icons/restaurant.png' },
    { name: 'marker-hotel', url: '/icons/hotel.png' },
    { name: 'marker-museum', url: '/icons/museum.png' }
  ];

  await Promise.all(
    icons.map(icon => loadIconSprite(icon.name, icon.url))
  );
}

// Use loaded icons in symbol layer
map.addLayer({
  id: 'poi-labels',
  type: 'symbol',
  source: 'poi',
  layout: {
    'icon-image': ['get', 'icon'], // Use icon property from data
    'icon-size': 0.8,
    'text-field': ['get', 'name'],
    'text-offset': [0, 1.5],
    'text-anchor': 'top'
  }
});
```

---

## Best Practices

### Performance Guidelines

1. **Vector Tiles Over GeoJSON**
   - Use vector tiles for large datasets
   - GeoJSON is suitable for small, dynamic data

2. **Implement Clustering**
   - Cluster point data at lower zoom levels
   - Use appropriate cluster radius

3. **Data-Driven Styling**
   - Use expressions instead of multiple layers
   - Leverage feature-state for interactivity

4. **Optimize Images**
   - Use sprite sheets for icons
   - Compress marker images
   - Use appropriate image formats (WebP when possible)

5. **Filter Strategically**
   - Apply zoom-based filters
   - Limit features rendered at each zoom level

6. **Debounce/Throttle Events**
   - Throttle move events
   - Debounce expensive operations

7. **Clean Up Resources**
   - Remove unused layers and sources
   - Clear event listeners when not needed

### Accessibility Considerations

```typescript
/**
 * @swagger
 * /api/map/accessibility:
 *   post:
 *     summary: Enhance map accessibility
 *     description: Implements accessibility features for map interactions
 *     tags: [Mapbox, Accessibility, A11y]
 */

/**
 * Add accessibility features to map
 */
function enhanceMapAccessibility(): void {
  const container = map.getContainer();

  // Add ARIA labels
  container.setAttribute('role', 'application');
  container.setAttribute('aria-label', 'Interactive map showing locations');

  // Add keyboard navigation for markers
  map.on('load', () => {
    const markers = document.querySelectorAll('.mapboxgl-marker');

    markers.forEach((marker, index) => {
      marker.setAttribute('tabindex', '0');
      marker.setAttribute('role', 'button');
      marker.setAttribute('aria-label', `Location marker ${index + 1}`);

      marker.addEventListener('keydown', (e) => {
        if (e.key === 'Enter' || e.key === ' ') {
          (marker as HTMLElement).click();
        }
      });
    });
  });

  // Provide skip link
  const skipLink = document.createElement('a');
  skipLink.href = '#map-controls';
  skipLink.textContent = 'Skip to map controls';
  skipLink.className = 'sr-only sr-only-focusable';
  container.prepend(skipLink);
}
```

### Styling Patterns Reference

**Common Visualization Patterns:**

1. **Choropleth Maps** - Color-coded regions based on data values
2. **Proportional Symbols** - Symbol size based on data magnitude
3. **Dot Density** - Point density represents data values
4. **Heat Maps** - Continuous density visualization
5. **Flow Maps** - Animated lines showing movement/connections
6. **3D Extrusion** - Height represents data values
7. **Graduated Symbols** - Stepped size categories
8. **Bivariate Choropleth** - Two variables encoded with color

**Color Scheme Considerations:**

- Use colorblind-friendly palettes
- Ensure sufficient contrast
- Sequential for continuous data
- Diverging for data with critical midpoint
- Categorical for discrete categories
- Limit to 7-9 categories for clarity

---

## Complete Example: Interactive Dashboard

```typescript
/**
 * @swagger
 * /api/map/interactive-dashboard:
 *   post:
 *     summary: Create complete interactive map dashboard
 *     description: Full-featured map with 3D, animations, data-driven styling, and controls
 *     tags: [Mapbox, Dashboard, Example]
 */

/**
 * Initialize complete interactive map dashboard
 */
class MapboxDashboard {
  private map: mapboxgl.Map;
  private currentTheme: 'light' | 'dark' = 'light';

  constructor(container: string) {
    mapboxgl.accessToken = 'YOUR_MAPBOX_ACCESS_TOKEN';

    // Initialize map
    this.map = new mapboxgl.Map({
      container,
      style: 'mapbox://styles/mapbox/dark-v11',
      center: [-74.5, 40],
      zoom: 12,
      pitch: 45,
      bearing: -17.6,
      antialias: true
    });

    this.map.on('load', () => {
      this.setup3DTerrain();
      this.addDataLayers();
      this.setupInteractions();
      this.addControls();
    });
  }

  private setup3DTerrain(): void {
    // Add terrain
    this.map.addSource('mapbox-dem', {
      type: 'raster-dem',
      url: 'mapbox://mapbox.mapbox-terrain-dem-v1',
      tileSize: 512,
      maxzoom: 14
    });

    this.map.setTerrain({ source: 'mapbox-dem', exaggeration: 1.5 });

    // Add 3D buildings
    this.map.addLayer({
      id: '3d-buildings',
      source: 'composite',
      'source-layer': 'building',
      filter: ['==', 'extrude', 'true'],
      type: 'fill-extrusion',
      minzoom: 15,
      paint: {
        'fill-extrusion-color': '#aaa',
        'fill-extrusion-height': ['get', 'height'],
        'fill-extrusion-base': ['get', 'min_height'],
        'fill-extrusion-opacity': 0.6
      }
    });

    // Add sky
    this.map.addLayer({
      id: 'sky',
      type: 'sky',
      paint: {
        'sky-type': 'atmosphere',
        'sky-atmosphere-sun': [0.0, 90.0],
        'sky-atmosphere-sun-intensity': 15
      }
    });
  }

  private addDataLayers(): void {
    // Add data source
    this.map.addSource('data-points', {
      type: 'geojson',
      data: '/api/data.geojson',
      cluster: true,
      clusterMaxZoom: 14,
      clusterRadius: 50
    });

    // Add layers
    this.map.addLayer({
      id: 'clusters',
      type: 'circle',
      source: 'data-points',
      filter: ['has', 'point_count'],
      paint: {
        'circle-color': [
          'step',
          ['get', 'point_count'],
          '#51bbd6', 100,
          '#f1f075', 750,
          '#f28cb1'
        ],
        'circle-radius': [
          'step',
          ['get', 'point_count'],
          20, 100, 30, 750, 40
        ]
      }
    });
  }

  private setupInteractions(): void {
    // Click handler for clusters
    this.map.on('click', 'clusters', (e) => {
      const features = this.map.queryRenderedFeatures(e.point, {
        layers: ['clusters']
      });

      if (features.length > 0) {
        const clusterId = features[0].properties?.cluster_id;
        const source = this.map.getSource('data-points') as mapboxgl.GeoJSONSource;

        source.getClusterExpansionZoom(clusterId, (err, zoom) => {
          if (err) return;

          const coordinates = (features[0].geometry as any).coordinates;
          this.map.easeTo({
            center: coordinates,
            zoom: zoom
          });
        });
      }
    });

    // Cursor style
    this.map.on('mouseenter', 'clusters', () => {
      this.map.getCanvas().style.cursor = 'pointer';
    });

    this.map.on('mouseleave', 'clusters', () => {
      this.map.getCanvas().style.cursor = '';
    });
  }

  private addControls(): void {
    // Navigation control
    this.map.addControl(new mapboxgl.NavigationControl(), 'top-right');

    // Fullscreen control
    this.map.addControl(new mapboxgl.FullscreenControl(), 'top-right');

    // Scale control
    this.map.addControl(new mapboxgl.ScaleControl(), 'bottom-left');
  }

  public switchTheme(theme: 'light' | 'dark'): void {
    const styles = {
      light: 'mapbox://styles/mapbox/streets-v12',
      dark: 'mapbox://styles/mapbox/dark-v11'
    };

    this.map.setStyle(styles[theme]);
    this.currentTheme = theme;
  }

  public destroy(): void {
    this.map.remove();
  }
}

// Usage
const dashboard = new MapboxDashboard('map');
