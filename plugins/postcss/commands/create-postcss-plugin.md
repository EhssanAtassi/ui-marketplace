---
description: Generate custom PostCSS plugin with boilerplate code and examples
---

I'll help you create a custom PostCSS plugin.

## Quick Generation

Tell me what your plugin should do:
- **Utility generator** - "Create utility class generator plugin"
- **Color transformer** - "Generate color modification plugin"
- **Custom syntax** - "Create custom CSS syntax plugin"
- **Validator** - "Generate CSS validation plugin"

## Plugin Types

1. **Utility Generator** - Auto-generate utility classes
2. **Transformer** - Modify CSS values/properties
3. **Syntax Extension** - Add custom CSS syntax
4. **Linter/Validator** - Check CSS rules
5. **Optimizer** - Performance improvements

## Generated Plugin Template

```javascript
/**
 * PostCSS Plugin: [Your Plugin Name]
 * @description [Plugin description]
 */
const postcss = require('postcss');

module.exports = postcss.plugin('postcss-your-plugin', (options = {}) => {
  // Plugin options with defaults
  const { prefix = 'u-', ...otherOptions } = options;

  return (root, result) => {
    // Process CSS AST
    root.walkRules((rule) => {
      // Modify selectors
      rule.selector = processSelector(rule.selector, prefix);

      // Modify declarations
      rule.walkDecls((decl) => {
        decl.value = processValue(decl.value);
      });
    });
  };
});

function processSelector(selector, prefix) {
  // Your selector logic
  return selector;
}

function processValue(value) {
  // Your value logic
  return value;
}
```

## Example: Utility Class Generator

```javascript
const postcss = require('postcss');

module.exports = postcss.plugin('postcss-utility-generator', (options = {}) => {
  const { prefix = 'u-', spacing = [0, 8, 16, 24, 32] } = options;

  return (root) => {
    const utilities = postcss.root();

    // Generate margin utilities
    spacing.forEach(value => {
      ['top', 'right', 'bottom', 'left'].forEach(side => {
        const rule = postcss.rule({ selector: `.${prefix}m-${side}-${value}` });
        rule.append({ prop: `margin-${side}`, value: `${value}px` });
        utilities.append(rule);
      });
    });

    root.append(utilities);
  };
});
```

## Usage

```javascript
// postcss.config.js
module.exports = {
  plugins: [
    require('./postcss-your-plugin')({
      prefix: 'u-',
      spacing: [0, 4, 8, 12, 16],
    }),
  ],
};
```

**Tell me what plugin you need!**
