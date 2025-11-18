---
description: Interactive wizard to select the best CSS methodology (BEM, OOCSS, SMACSS, ITCSS, CUBE CSS) for your project
---

I'll help you choose the perfect CSS methodology for your project through an interactive questionnaire.

## What This Does

This wizard will:
- Ask about your project requirements
- Analyze your team structure
- Evaluate technical constraints
- Recommend the best methodology
- Provide implementation guide
- Generate starter files

## Supported Methodologies

### BEM (Block Element Modifier)
**Best For:**
- Component libraries
- React/Vue/Angular applications
- Teams new to CSS methodologies
- Clear component boundaries

**Naming:** `.block__element--modifier`

**Example:**
```html
<div class="product-card product-card--featured">
  <div class="product-card__header">
    <h3 class="product-card__title">Product Name</h3>
  </div>
  <div class="product-card__body">
    <p class="product-card__description">Description</p>
  </div>
</div>
```

### OOCSS (Object-Oriented CSS)
**Best For:**
- Maximum CSS reusability
- Design systems
- Large applications
- OOP-familiar teams

**Principles:**
1. Separate structure from skin
2. Separate container from content

**Example:**
```html
<div class="media box box--primary">
  <div class="media-figure">
    <img src="avatar.jpg" alt="User" />
  </div>
  <div class="media-body">
    <h3>John Doe</h3>
  </div>
</div>
```

### SMACSS (Scalable and Modular Architecture)
**Best For:**
- Large applications
- Multi-theme projects
- State-heavy applications
- Clear categorization needed

**Categories:**
1. Base - Default styles
2. Layout - Major sections (l-)
3. Module - Reusable components
4. State - State-based (is-)
5. Theme - Color schemes (theme-)

**Example:**
```html
<div class="l-header">
  <nav class="nav">
    <a href="#" class="nav-link is-active">Home</a>
  </nav>
</div>
```

### ITCSS (Inverted Triangle CSS)
**Best For:**
- Enterprise applications
- Design systems
- Large teams
- Long-term maintainability

**7 Layers:** Settings → Tools → Generic → Elements → Objects → Components → Utilities

**Example:**
```scss
// Layer 5: Objects
.o-container { }

// Layer 6: Components
.c-button { }

// Layer 7: Utilities
.u-text-center { }
```

### CUBE CSS (Composition Utility Block Exception)
**Best For:**
- Modern CSS projects
- Progressive enhancement
- Flexible component systems
- CSS-first approach

**4 Layers:**
1. Composition - Layout (.stack, .cluster)
2. Utility - Helpers (.flow, .bg-primary)
3. Block - Components ([data-component="button"])
4. Exception - States ([data-state="active"])

**Example:**
```html
<div class="stack cluster">
  <button data-component="button" data-variant="primary">
    Click me
  </button>
</div>
```

## Decision Tree

### Question 1: Project Type
What type of project are you building?

**A. Component Library / Design System**
→ Recommendation: **BEM** or **ITCSS**
- BEM for simpler systems
- ITCSS for enterprise-scale

**B. Large Web Application**
→ Recommendation: **SMACSS** or **ITCSS**
- SMACSS for multi-theme needs
- ITCSS for maximum scalability

**C. Modern Progressive Web App**
→ Recommendation: **CUBE CSS** or **BEM**
- CUBE CSS for cutting-edge approach
- BEM for proven methodology

**D. Small to Medium Project**
→ Recommendation: **BEM**
- Easy to learn
- Widely adopted
- Good tooling support

### Question 2: Team Size
How large is your team?

**A. Solo Developer / 1-2 people**
→ **BEM** (simple, effective)

**B. Small Team (3-10 people)**
→ **BEM** or **OOCSS** (manageable complexity)

**C. Large Team (10-50 people)**
→ **SMACSS** or **ITCSS** (clear categorization)

**D. Enterprise (50+ people)**
→ **ITCSS** (maximum structure and governance)

### Question 3: Team Experience
What's your team's CSS experience level?

**A. Beginner**
→ **BEM** (easiest to learn)

**B. Intermediate**
→ **BEM** or **SMACSS** (moderate learning curve)

**C. Advanced**
→ **ITCSS** or **CUBE CSS** (can handle complexity)

### Question 4: Requirements
What are your key requirements?

**A. Maximum Reusability**
→ **OOCSS**

**B. Clear Component Boundaries**
→ **BEM**

**C. Multi-Theme Support**
→ **SMACSS**

**D. Long-Term Maintainability**
→ **ITCSS**

**E. Modern CSS Features**
→ **CUBE CSS**

## Comparison Matrix

| Feature | BEM | OOCSS | SMACSS | ITCSS | CUBE CSS |
|---------|-----|-------|--------|-------|----------|
| **Learning Curve** | Easy | Moderate | Moderate | Steep | Moderate |
| **Specificity** | Low | Low | Medium | Low | Low |
| **Scalability** | Large | Large | Large | Large | Medium |
| **Tooling** | Excellent | Good | Good | Good | Limited |
| **Community** | Largest | Large | Large | Large | Growing |
| **Flexibility** | Medium | High | High | Medium | High |

## What Gets Generated

Based on your selection, I'll generate:

### 1. File Structure
Appropriate folder organization for your chosen methodology.

### 2. Configuration Files
- Stylelint rules for your methodology
- Build configuration
- Naming convention guides

### 3. Starter Components
- Button component
- Card component
- Navigation component
- Form components

### 4. Documentation
- Methodology guide
- Best practices
- Code examples
- Team onboarding

### 5. Tooling Setup
- Linting configuration
- Editor snippets
- Git hooks
- CI/CD checks

## Quick Selection

Tell me about your project:
"I'm building a [project type] with a team of [size] developers"

**Examples:**
- "I'm building a component library with a team of 5 developers"
  → **BEM**

- "I'm building an enterprise application with a team of 30 developers"
  → **ITCSS**

- "I'm building a modern web app with a team of 3 developers"
  → **BEM** or **CUBE CSS**

- "I'm building a multi-theme dashboard with a team of 15 developers"
  → **SMACSS**

## Custom Selection

Answer these questions:
1. **Project type**: Component library / Application / Design system
2. **Team size**: 1-5 / 5-20 / 20+
3. **CSS experience**: Beginner / Intermediate / Advanced
4. **Key requirement**: Reusability / Scalability / Theming / Modern CSS
5. **Framework**: React / Vue / Angular / Vanilla
6. **Timeline**: < 3 months / 3-12 months / Long-term

## Hybrid Approaches

You can also combine methodologies:

**BEM + ITCSS (Recommended)**
- Use ITCSS layers for organization
- Use BEM naming for components
- Best of both worlds

**OOCSS + BEM**
- OOCSS principles for structure
- BEM naming for clarity
- Maximum reusability

**SMACSS + BEM**
- SMACSS categories for organization
- BEM naming within modules
- Clear categorization

## What Happens Next

1. I'll analyze your requirements
2. Recommend the best methodology
3. Explain the rationale
4. Generate all starter files
5. Provide implementation guide
6. Include migration path (if switching)

Let me know your project details, and I'll help you select the perfect CSS methodology!
