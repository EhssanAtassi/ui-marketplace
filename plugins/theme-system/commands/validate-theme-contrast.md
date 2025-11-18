---
description: Validate theme contrast ratios against WCAG 2.1/2.2 AA and AAA standards with automated fix suggestions
---

I'll help you validate your theme's color contrast ratios against WCAG accessibility standards and provide automated fixes for any issues found.

## What This Validates

Complete WCAG contrast validation:
- **Text on Backgrounds**: All foreground/background combinations
- **Interactive Elements**: Buttons, links, form controls
- **Focus Indicators**: Focus ring visibility
- **Borders and Dividers**: Visual distinction
- **Charts and Data Viz**: Color-coded information
- **WCAG 2.1 AA Compliance**: 4.5:1 for normal text, 3:1 for large text
- **WCAG 2.1 AAA Compliance**: 7:1 for normal text, 4.5:1 for large text

## Quick Validation

Just tell me:
1. **Theme to validate**: Light, dark, or custom theme object
2. **Standard**: AA (minimum) or AAA (enhanced)
3. **Auto-fix**: Whether to generate fixed colors

**Examples:**
- "Validate my light theme for WCAG AA compliance"
- "Check dark theme contrast and auto-fix issues"
- "Validate all themes for AAA compliance"

## Validation Modes

### 1. Quick Check

Validate most common combinations:
- Primary text on primary background
- Secondary text on secondary background
- Button text on button backgrounds
- Link colors on backgrounds

### 2. Comprehensive Validation

Check ALL color combinations:
- All foreground × background combinations
- All interactive state colors
- All semantic color combinations
- Border and focus indicators

### 3. Component-Specific

Validate specific components:
- Buttons (all variants)
- Forms (inputs, labels, validation)
- Cards and panels
- Navigation elements
- Badges and tags

## WCAG Standards Reference

### Contrast Ratio Requirements

```
Normal Text (< 18pt or < 14pt bold):
- WCAG AA:  4.5:1 minimum
- WCAG AAA: 7:1 minimum

Large Text (≥ 18pt or ≥ 14pt bold):
- WCAG AA:  3:1 minimum
- WCAG AAA: 4.5:1 minimum

UI Components & Graphics:
- WCAG AA:  3:1 minimum (non-text contrast)

Text against images/gradients:
- Must meet minimum ratio across entire range
```

### What Gets Validated

✅ **Text Contrast**
- Body text on all background colors
- Heading text on backgrounds
- Link text (default and hover states)
- Button text on button backgrounds
- Form labels and input text
- Error, warning, success messages

✅ **Interactive Elements**
- Button borders and backgrounds
- Form control borders
- Focus indicators (must be 3:1 against background)
- Active/selected state indicators

✅ **UI Components**
- Icons (when conveying information)
- Borders and dividers
- Chart colors (for data visualization)

❌ **Not Validated** (WCAG exempt)
- Logos and brand marks
- Inactive/disabled UI components
- Purely decorative elements

## Validation Report

```typescript
/**
 * Contrast Validation Report
 */
interface ValidationReport {
  valid: boolean;
  standard: 'AA' | 'AAA';
  timestamp: string;
  summary: {
    totalChecks: number;
    passed: number;
    failures: number;
    warnings: number;
  };
  issues: ContrastIssue[];
  warnings: ContrastWarning[];
  recommendations: Recommendation[];
}

interface ContrastIssue {
  type: 'error';
  severity: 'critical' | 'high';
  foreground: string;
  foregroundValue: string;
  background: string;
  backgroundValue: string;
  ratio: number;
  required: number;
  context: 'normal-text' | 'large-text' | 'ui-component';
  suggestion: ColorSuggestion;
}

interface ContrastWarning {
  type: 'warning';
  foreground: string;
  background: string;
  ratio: number;
  message: string;
  recommendation: string;
}
```

## Example Validation Output

```
=== Theme Contrast Validation Report ===

Standard: WCAG 2.1 AA
Theme: Light Theme
Date: 2024-01-15

✅ Summary:
- Total Checks: 48
- Passed: 42 (87.5%)
- Failed: 4 (8.3%)
- Warnings: 2 (4.2%)

❌ FAILURES (4):

1. [CRITICAL] foreground.tertiary on background.primary
   Colors: #9ca3af on #ffffff
   Ratio: 2.85:1 (need 4.5:1)
   Context: Normal text
   ⚠️  This fails WCAG AA for normal text

   ✨ Suggested Fix:
   Change foreground.tertiary from #9ca3af to #6b7280
   New ratio: 4.54:1 ✓ (passes AA)

2. [HIGH] interactive.secondary.default on background.primary
   Colors: #6b7280 on #ffffff
   Ratio: 4.37:1 (need 4.5:1)
   Context: UI component
   ⚠️  Just below AA threshold

   ✨ Suggested Fix:
   Change interactive.secondary.default from #6b7280 to #4b5563
   New ratio: 6.36:1 ✓ (passes AA and AAA)

3. [CRITICAL] Button secondary text on background
   Colors: #9ca3af on #f3f4f6
   Ratio: 2.14:1 (need 3:1)
   Context: UI component
   ⚠️  Fails minimum contrast for UI components

   ✨ Suggested Fix:
   Change button text from #9ca3af to #374151
   New ratio: 8.42:1 ✓ (passes AAA)

4. [HIGH] Border default visibility
   Colors: #e5e7eb on #ffffff
   Ratio: 1.28:1 (need 3:1)
   Context: UI component
   ⚠️  Border not sufficiently visible

   ✨ Suggested Fix:
   Change border.default from #e5e7eb to #d1d5db
   New ratio: 3.04:1 ✓ (passes AA for UI)

⚠️  WARNINGS (2):

1. foreground.secondary on background.secondary
   Colors: #4b5563 on #f9fafb
   Ratio: 6.82:1
   ⚠️  Passes AA (4.5:1) but not AAA (7:1)
   💡 Recommendation: Consider darker shade for AAA compliance

2. Link hover state
   Colors: #1d4ed8 on #ffffff
   Ratio: 7.12:1
   ⚠️  Good contrast, but ensure focus indicator is also 3:1
   💡 Recommendation: Validate focus ring separately

✅ EXCELLENT (Sample):

1. foreground.primary on background.primary
   Colors: #111827 on #ffffff
   Ratio: 15.46:1 ✓✓✓ (AAA)

2. Interactive primary button
   Colors: #ffffff on #3b82f6
   Ratio: 5.89:1 ✓✓ (AA)

3. Success message
   Colors: #047857 on #f0fdf4
   Ratio: 8.24:1 ✓✓✓ (AAA)

=== Auto-Fix Available ===

I can automatically generate a fixed theme with all issues resolved.
Would you like me to:
1. Generate fixed theme
2. Show side-by-side comparison
3. Export as new theme file
```

## Validation Functions

```typescript
/**
 * Contrast Checker
 * @description WCAG 2.1 contrast validation
 */
export class ContrastChecker {
  /**
   * Check Single Contrast Ratio
   */
  static checkContrast(
    foreground: string,
    background: string
  ): ContrastResult {
    const ratio = this.calculateRatio(foreground, background);

    return {
      ratio: parseFloat(ratio.toFixed(2)),
      normalText: {
        aa: ratio >= 4.5,
        aaa: ratio >= 7,
      },
      largeText: {
        aa: ratio >= 3,
        aaa: ratio >= 4.5,
      },
      uiComponent: {
        aa: ratio >= 3,
      },
    };
  }

  /**
   * Validate Entire Theme
   */
  static validateTheme(
    theme: Theme,
    standard: 'AA' | 'AAA' = 'AA'
  ): ValidationReport {
    const issues: ContrastIssue[] = [];
    const warnings: ContrastWarning[] = [];
    let totalChecks = 0;

    // Check foreground on backgrounds
    Object.entries(theme.colors.foreground).forEach(([fgKey, fgColor]) => {
      Object.entries(theme.colors.background).forEach(([bgKey, bgColor]) => {
        totalChecks++;
        const result = this.checkContrast(fgColor, bgColor);

        const meetsStandard = standard === 'AA'
          ? result.normalText.aa
          : result.normalText.aaa;

        if (!meetsStandard) {
          issues.push({
            type: 'error',
            severity: result.ratio < 3 ? 'critical' : 'high',
            foreground: `foreground.${fgKey}`,
            foregroundValue: fgColor,
            background: `background.${bgKey}`,
            backgroundValue: bgColor,
            ratio: result.ratio,
            required: standard === 'AA' ? 4.5 : 7,
            context: 'normal-text',
            suggestion: this.suggestFix(fgColor, bgColor, standard),
          });
        } else if (standard === 'AA' && !result.normalText.aaa) {
          // Passes AA but not AAA
          warnings.push({
            type: 'warning',
            foreground: `foreground.${fgKey}`,
            background: `background.${bgKey}`,
            ratio: result.ratio,
            message: `Passes AA (${result.ratio}:1) but not AAA (need 7:1)`,
            recommendation: 'Consider darker shade for AAA compliance',
          });
        }
      });
    });

    // Check interactive elements
    Object.entries(theme.colors.interactive).forEach(([variant, states]) => {
      Object.entries(states).forEach(([state, color]) => {
        totalChecks++;
        const result = this.checkContrast(
          color,
          theme.colors.background.primary
        );

        if (!result.uiComponent.aa) {
          issues.push({
            type: 'error',
            severity: 'high',
            foreground: `interactive.${variant}.${state}`,
            foregroundValue: color,
            background: 'background.primary',
            backgroundValue: theme.colors.background.primary,
            ratio: result.ratio,
            required: 3,
            context: 'ui-component',
            suggestion: this.suggestFix(
              color,
              theme.colors.background.primary,
              'AA',
              true
            ),
          });
        }
      });
    });

    // Check borders
    Object.entries(theme.colors.border).forEach(([key, borderColor]) => {
      totalChecks++;
      const result = this.checkContrast(
        borderColor,
        theme.colors.background.primary
      );

      if (!result.uiComponent.aa && key !== 'focus') {
        issues.push({
          type: 'error',
          severity: 'high',
          foreground: `border.${key}`,
          foregroundValue: borderColor,
          background: 'background.primary',
          backgroundValue: theme.colors.background.primary,
          ratio: result.ratio,
          required: 3,
          context: 'ui-component',
          suggestion: this.suggestFix(
            borderColor,
            theme.colors.background.primary,
            'AA',
            true
          ),
        });
      }
    });

    return {
      valid: issues.length === 0,
      standard,
      timestamp: new Date().toISOString(),
      summary: {
        totalChecks,
        passed: totalChecks - issues.length - warnings.length,
        failures: issues.length,
        warnings: warnings.length,
      },
      issues,
      warnings,
      recommendations: this.generateRecommendations(issues, warnings),
    };
  }

  /**
   * Calculate Contrast Ratio
   * @description WCAG formula: (L1 + 0.05) / (L2 + 0.05)
   */
  private static calculateRatio(color1: string, color2: string): number {
    const l1 = this.getLuminance(color1);
    const l2 = this.getLuminance(color2);
    const lighter = Math.max(l1, l2);
    const darker = Math.min(l1, l2);
    return (lighter + 0.05) / (darker + 0.05);
  }

  /**
   * Get Relative Luminance
   * @description WCAG formula for relative luminance
   */
  private static getLuminance(color: string): number {
    const rgb = this.hexToRgb(color);
    const [r, g, b] = rgb.map(val => {
      val = val / 255;
      return val <= 0.03928
        ? val / 12.92
        : Math.pow((val + 0.055) / 1.055, 2.4);
    });
    return 0.2126 * r + 0.7152 * g + 0.0722 * b;
  }

  /**
   * Hex to RGB
   */
  private static hexToRgb(hex: string): number[] {
    const result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
    return result
      ? [
          parseInt(result[1], 16),
          parseInt(result[2], 16),
          parseInt(result[3], 16),
        ]
      : [0, 0, 0];
  }

  /**
   * Suggest Color Fix
   * @description Find nearest color that meets contrast requirement
   */
  private static suggestFix(
    foreground: string,
    background: string,
    standard: 'AA' | 'AAA',
    isUIComponent = false
  ): ColorSuggestion {
    const targetRatio = isUIComponent ? 3 : (standard === 'AA' ? 4.5 : 7);

    // Try darkening foreground
    let suggested = foreground;
    let ratio = this.calculateRatio(suggested, background);

    const rgb = this.hexToRgb(foreground);
    const step = 10;

    // Darken until we meet the target
    while (ratio < targetRatio && rgb.every(c => c > 0)) {
      rgb.forEach((_, i) => {
        rgb[i] = Math.max(0, rgb[i] - step);
      });
      suggested = this.rgbToHex(rgb);
      ratio = this.calculateRatio(suggested, background);
    }

    return {
      originalColor: foreground,
      suggestedColor: suggested,
      newRatio: ratio,
      meetsRequirement: ratio >= targetRatio,
    };
  }

  /**
   * RGB to Hex
   */
  private static rgbToHex(rgb: number[]): string {
    return '#' + rgb.map(c => {
      const hex = c.toString(16);
      return hex.length === 1 ? '0' + hex : hex;
    }).join('');
  }
}
```

## Auto-Fix Theme Generator

```typescript
/**
 * Auto-Fix Theme
 * @description Generate fixed theme with all contrast issues resolved
 */
export function autoFixTheme(
  theme: Theme,
  standard: 'AA' | 'AAA' = 'AA'
): {
  fixedTheme: Theme;
  changes: ThemeChange[];
} {
  const report = ContrastChecker.validateTheme(theme, standard);
  const fixedTheme = { ...theme };
  const changes: ThemeChange[] = [];

  // Apply all suggested fixes
  report.issues.forEach(issue => {
    if (issue.suggestion.meetsRequirement) {
      // Parse path like "foreground.tertiary"
      const path = issue.foreground.split('.');
      let current: any = fixedTheme.colors;

      // Navigate to the property
      for (let i = 0; i < path.length - 1; i++) {
        current = current[path[i]];
      }

      // Apply fix
      const oldValue = current[path[path.length - 1]];
      current[path[path.length - 1]] = issue.suggestion.suggestedColor;

      changes.push({
        path: issue.foreground,
        oldValue,
        newValue: issue.suggestion.suggestedColor,
        reason: `Improve contrast from ${issue.ratio}:1 to ${issue.suggestion.newRatio}:1`,
      });
    }
  });

  return { fixedTheme, changes };
}
```

## Usage Examples

```typescript
/**
 * Example 1: Quick Validation
 */
import { ContrastChecker } from './validation';
import { lightTheme } from './theme';

const report = ContrastChecker.validateTheme(lightTheme, 'AA');

if (!report.valid) {
  console.log(`Found ${report.summary.failures} contrast issues`);
  report.issues.forEach(issue => {
    console.log(`❌ ${issue.foreground} on ${issue.background}`);
    console.log(`   Current: ${issue.ratio}:1, Need: ${issue.required}:1`);
    console.log(`   Fix: Use ${issue.suggestion.suggestedColor}`);
  });
}

/**
 * Example 2: Auto-Fix Theme
 */
const { fixedTheme, changes } = autoFixTheme(lightTheme, 'AA');

console.log('Theme Fixes Applied:');
changes.forEach(change => {
  console.log(`✓ ${change.path}: ${change.oldValue} → ${change.newValue}`);
  console.log(`  ${change.reason}`);
});

// Export fixed theme
export { fixedTheme as lightThemeFixed };

/**
 * Example 3: Component-Specific Validation
 */
const buttonContrast = ContrastChecker.checkContrast(
  '#ffffff',  // button text
  '#3b82f6'   // button background
);

console.log(`Button contrast: ${buttonContrast.ratio}:1`);
console.log(`Passes AA: ${buttonContrast.normalText.aa ? '✓' : '✗'}`);
```

## CI/CD Integration

```typescript
/**
 * Validate in CI/CD Pipeline
 */
import { ContrastChecker } from './validation';
import * as themes from './themes';

// Validate all themes
const results = Object.entries(themes).map(([name, theme]) => {
  const report = ContrastChecker.validateTheme(theme, 'AA');
  return { name, report };
});

// Check if any theme fails
const hasFailures = results.some(r => !r.report.valid);

if (hasFailures) {
  console.error('❌ Theme contrast validation failed!');
  results.forEach(({ name, report }) => {
    if (!report.valid) {
      console.error(`\n${name}:`);
      report.issues.forEach(issue => {
        console.error(`  - ${issue.foreground} on ${issue.background}: ${issue.ratio}:1`);
      });
    }
  });
  process.exit(1);
}

console.log('✓ All themes pass WCAG AA contrast requirements');
```

## What Happens Next

1. You provide your theme(s) to validate
2. I run comprehensive contrast checks
3. Generate detailed validation report
4. Identify all WCAG failures and warnings
5. Provide specific fix suggestions for each issue
6. Optionally generate auto-fixed theme
7. Provide side-by-side comparison
8. Export validation results (JSON, HTML report)

**Provide your theme, and I'll validate its accessibility compliance!**
