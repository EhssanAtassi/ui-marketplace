---
name: generate-architecture
description: Generate a complete CSS architecture structure (ITCSS, BEM, or custom) with files and folders
---

You are tasked with generating a complete CSS architecture for the user's project.

## Instructions

1. **Ask the user** what type of CSS architecture they want:
   - ITCSS (Inverted Triangle)
   - BEM (Block Element Modifier)
   - SMACSS (Scalable and Modular Architecture)
   - Atomic CSS
   - Custom hybrid approach

2. **Ask about their project stack**:
   - Framework (React, Angular, Vue, vanilla)
   - Preprocessor (SCSS, SASS, PostCSS, CSS)
   - Build tool (Webpack, Vite, Parcel)
   - Design system (if any)

3. **Generate the complete file structure** including:
   - Folder organization
   - All necessary files (settings, tools, base, components, utilities)
   - Configuration files (if needed)
   - Import/index files
   - README with architecture documentation

4. **Create starter code** for:
   - Main entry point
   - Configuration variables
   - Utility mixins/functions
   - Reset/normalize
   - Example components following the chosen architecture

5. **Add comprehensive documentation**:
   - Naming conventions
   - File organization rules
   - How to add new components
   - Best practices
   - Examples

6. **Include**:
   - Full Swagger-style comments
   - Usage examples
   - Architecture decision rationale

## Example Output Structure

For ITCSS, generate:
```
styles/
├── settings/
│   ├── _settings.global.scss
│   ├── _settings.colors.scss
│   └── _settings.breakpoints.scss
├── tools/
│   ├── _tools.mixins.scss
│   └── _tools.functions.scss
├── generic/
│   └── _generic.reset.scss
├── elements/
│   ├── _elements.headings.scss
│   └── _elements.links.scss
├── objects/
│   ├── _objects.wrapper.scss
│   └── _objects.layout.scss
├── components/
│   ├── _components.button.scss
│   └── _components.card.scss
├── utilities/
│   ├── _utilities.spacing.scss
│   └── _utilities.text.scss
└── main.scss
```

Generate all files with appropriate content based on the user's answers.
