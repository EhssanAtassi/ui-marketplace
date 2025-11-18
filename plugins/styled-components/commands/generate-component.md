---
description: Generate styled React components with TypeScript, variants, responsive design, and animations
---

I'll help you generate production-ready styled components with complete TypeScript definitions, variants, responsive behavior, and animations.

## What This Generates

Complete component files:
- TypeScript component file
- Styled components definitions
- Props interface with full typing
- Variant system (sizes, colors, states)
- Responsive design patterns
- Animation support
- Accessibility attributes
- JSDoc documentation
- Usage examples

## Component Types

### 1. Button Component
Complete button with variants and states.

**Includes:**
- Primary, secondary, outline, ghost variants
- Small, medium, large sizes
- Loading state with spinner
- Disabled state
- Full-width option
- Icon support
- Ripple effect (optional)

**Example:**
```typescript
<Button variant="primary" size="large" loading>
  Click Me
</Button>
```

### 2. Card Component
Flexible card with header, body, footer.

**Includes:**
- Card container with elevation
- Header, body, footer sections
- Hover effects
- Image support
- Clickable variant
- Loading skeleton
- Responsive padding

**Example:**
```typescript
<Card hoverable>
  <Card.Header>
    <Card.Title>Title</Card.Title>
  </Card.Header>
  <Card.Body>Content</Card.Body>
  <Card.Footer>Actions</Card.Footer>
</Card>
```

### 3. Input Component
Form input with validation styling.

**Includes:**
- Text, password, email, number types
- Label and helper text
- Error state styling
- Disabled state
- Icon prefix/suffix
- Character counter
- Accessibility labels

**Example:**
```typescript
<Input
  label="Email"
  type="email"
  error="Invalid email"
  icon={<EmailIcon />}
/>
```

### 4. Modal Component
Accessible modal/dialog.

**Includes:**
- Overlay with backdrop
- Modal container
- Header with close button
- Body with scroll
- Footer with actions
- Animation enter/exit
- Focus trap
- ESC key support

**Example:**
```typescript
<Modal isOpen={isOpen} onClose={onClose}>
  <Modal.Header>Title</Modal.Header>
  <Modal.Body>Content</Modal.Body>
  <Modal.Footer>
    <Button onClick={onClose}>Close</Button>
  </Modal.Footer>
</Modal>
```

### 5. Grid Component
Responsive grid layout.

**Includes:**
- CSS Grid implementation
- Column configuration
- Gap control
- Auto-fit/auto-fill
- Min column width
- Responsive breakpoints

**Example:**
```typescript
<Grid columns={3} gap="lg" minColumnWidth="250px">
  <GridItem>Item 1</GridItem>
  <GridItem>Item 2</GridItem>
  <GridItem>Item 3</GridItem>
</Grid>
```

### 6. Dropdown Component
Dropdown/select component.

**Includes:**
- Trigger button
- Dropdown menu
- Option list
- Search/filter
- Multi-select
- Keyboard navigation
- Portal positioning

**Example:**
```typescript
<Dropdown>
  <Dropdown.Trigger>Select</Dropdown.Trigger>
  <Dropdown.Menu>
    <Dropdown.Item value="1">Option 1</Dropdown.Item>
    <Dropdown.Item value="2">Option 2</Dropdown.Item>
  </Dropdown.Menu>
</Dropdown>
```

### 7. Toast/Notification Component
Toast notifications.

**Includes:**
- Success, warning, error, info variants
- Auto-dismiss timer
- Close button
- Animation enter/exit
- Position options
- Queue management

**Example:**
```typescript
<Toast variant="success" duration={3000} onClose={onClose}>
  Operation successful!
</Toast>
```

### 8. Skeleton Loader
Loading placeholder.

**Includes:**
- Text skeleton
- Circle skeleton
- Rectangle skeleton
- Shimmer animation
- Customizable dimensions

**Example:**
```typescript
<Skeleton width="100%" height="200px" />
<Skeleton circle width="40px" height="40px" />
```

## Quick Generation

Just tell me:
"Generate a [component type]"

**Examples:**
- "Generate a Button component with variants"
- "Generate a Card component with hover effects"
- "Generate a Modal component"
- "Generate an Input component with validation"

## Custom Generation

Specify requirements:

**Component name**: "PrimaryButton"
**Variants**: primary, secondary, danger
**Sizes**: small, medium, large
**Features**: loading state, icon support, ripple effect
**Responsive**: yes
**Animations**: fade in, scale on click
**Accessibility**: WCAG 2.1 AA

## Example: Generated Button Component

**Button.tsx:**
```typescript
/**
 * Button Component
 * @description Flexible button component with multiple variants and states
 * @example
 * <Button variant="primary" size="large" loading>
 *   Click Me
 * </Button>
 */
import React from 'react';
import styled, { css, keyframes } from 'styled-components';

/**
 * Button props interface
 */
export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  /** Visual variant of the button */
  variant?: 'primary' | 'secondary' | 'outline' | 'ghost' | 'danger';
  /** Size variant */
  size?: 'small' | 'medium' | 'large';
  /** Loading state with spinner */
  loading?: boolean;
  /** Full width button */
  fullWidth?: boolean;
  /** Icon element (before text) */
  icon?: React.ReactNode;
  /** Icon position */
  iconPosition?: 'left' | 'right';
}

/**
 * Spin animation for loading spinner
 */
const spin = keyframes`
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
`;

/**
 * Base button styles
 */
const StyledButton = styled.button<ButtonProps>`
  /* Base styles */
  position: relative;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: ${({ theme }) => theme.spacing.sm};
  border: none;
  font-family: ${({ theme }) => theme.typography.fontFamily.primary};
  font-weight: ${({ theme }) => theme.typography.fontWeight.semibold};
  cursor: pointer;
  user-select: none;
  transition: ${({ theme }) => theme.transitions.fast};
  white-space: nowrap;

  /* Prevent double-tap zoom on mobile */
  touch-action: manipulation;

  /* Size variants */
  ${({ size = 'medium', theme }) => {
    switch (size) {
      case 'small':
        return css`
          padding: ${theme.spacing.xs} ${theme.spacing.md};
          font-size: ${theme.typography.fontSize.sm};
          line-height: ${theme.typography.lineHeight.tight};
          border-radius: ${theme.borderRadius.md};
        `;
      case 'large':
        return css`
          padding: ${theme.spacing.md} ${theme.spacing.xl};
          font-size: ${theme.typography.fontSize.lg};
          line-height: ${theme.typography.lineHeight.normal};
          border-radius: ${theme.borderRadius.lg};
        `;
      default: // medium
        return css`
          padding: ${theme.spacing.sm} ${theme.spacing.lg};
          font-size: ${theme.typography.fontSize.base};
          line-height: ${theme.typography.lineHeight.normal};
          border-radius: ${theme.borderRadius.md};
        `;
    }
  }}

  /* Variant styles */
  ${({ variant = 'primary', theme }) => {
    switch (variant) {
      case 'secondary':
        return css`
          background-color: ${theme.colors.secondary};
          color: white;

          &:hover:not(:disabled) {
            background-color: ${theme.colors.secondaryHover};
          }

          &:active:not(:disabled) {
            background-color: ${theme.colors.secondaryActive};
          }
        `;

      case 'outline':
        return css`
          background-color: transparent;
          color: ${theme.colors.primary};
          border: 2px solid ${theme.colors.primary};

          &:hover:not(:disabled) {
            background-color: ${theme.colors.primaryLight};
          }

          &:active:not(:disabled) {
            background-color: ${theme.colors.primary};
            color: white;
          }
        `;

      case 'ghost':
        return css`
          background-color: transparent;
          color: ${theme.colors.primary};

          &:hover:not(:disabled) {
            background-color: ${theme.colors.primaryLight};
          }

          &:active:not(:disabled) {
            background-color: ${theme.colors.surface};
          }
        `;

      case 'danger':
        return css`
          background-color: ${theme.colors.danger};
          color: white;

          &:hover:not(:disabled) {
            background-color: ${theme.colors.dangerDark};
          }

          &:active:not(:disabled) {
            background-color: ${theme.colors.danger};
            filter: brightness(0.9);
          }
        `;

      default: // primary
        return css`
          background-color: ${theme.colors.primary};
          color: white;

          &:hover:not(:disabled) {
            background-color: ${theme.colors.primaryHover};
          }

          &:active:not(:disabled) {
            background-color: ${theme.colors.primaryActive};
            transform: scale(0.98);
          }
        `;
    }
  }}

  /* Full width */
  ${({ fullWidth }) =>
    fullWidth &&
    css`
      width: 100%;
    `}

  /* Disabled state */
  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    pointer-events: none;
  }

  /* Focus state for accessibility */
  &:focus-visible {
    outline: 2px solid ${({ theme }) => theme.colors.primary};
    outline-offset: 2px;
  }

  /* Loading state */
  ${({ loading }) =>
    loading &&
    css`
      position: relative;
      color: transparent;
      pointer-events: none;
    `}
`;

/**
 * Loading spinner
 */
const Spinner = styled.span`
  position: absolute;
  width: 16px;
  height: 16px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-top-color: white;
  border-radius: 50%;
  animation: ${spin} 0.6s linear infinite;
`;

/**
 * Icon wrapper
 */
const IconWrapper = styled.span`
  display: inline-flex;
  align-items: center;
  justify-content: center;
`;

/**
 * Button Component
 */
export const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  (
    {
      children,
      variant = 'primary',
      size = 'medium',
      loading = false,
      fullWidth = false,
      icon,
      iconPosition = 'left',
      disabled,
      ...props
    },
    ref
  ) => {
    return (
      <StyledButton
        ref={ref}
        variant={variant}
        size={size}
        loading={loading}
        fullWidth={fullWidth}
        disabled={disabled || loading}
        aria-busy={loading}
        {...props}
      >
        {loading && <Spinner />}
        {icon && iconPosition === 'left' && <IconWrapper>{icon}</IconWrapper>}
        {children}
        {icon && iconPosition === 'right' && <IconWrapper>{icon}</IconWrapper>}
      </StyledButton>
    );
  }
);

Button.displayName = 'Button';

export default Button;
```

**Button.stories.tsx** (Storybook example):
```typescript
/**
 * Button Stories
 * @description Storybook stories for Button component
 */
import type { Meta, StoryObj } from '@storybook/react';
import { Button } from './Button';

const meta: Meta<typeof Button> = {
  title: 'Components/Button',
  component: Button,
  tags: ['autodocs'],
  argTypes: {
    variant: {
      control: 'select',
      options: ['primary', 'secondary', 'outline', 'ghost', 'danger'],
    },
    size: {
      control: 'select',
      options: ['small', 'medium', 'large'],
    },
    loading: { control: 'boolean' },
    fullWidth: { control: 'boolean' },
    disabled: { control: 'boolean' },
  },
};

export default meta;
type Story = StoryObj<typeof Button>;

export const Primary: Story = {
  args: {
    children: 'Primary Button',
    variant: 'primary',
  },
};

export const Secondary: Story = {
  args: {
    children: 'Secondary Button',
    variant: 'secondary',
  },
};

export const Outline: Story = {
  args: {
    children: 'Outline Button',
    variant: 'outline',
  },
};

export const Loading: Story = {
  args: {
    children: 'Loading Button',
    loading: true,
  },
};

export const WithIcon: Story = {
  args: {
    children: 'Button with Icon',
    icon: <span>→</span>,
  },
};

export const Sizes: Story = {
  render: () => (
    <div style={{ display: 'flex', gap: '16px', alignItems: 'center' }}>
      <Button size="small">Small</Button>
      <Button size="medium">Medium</Button>
      <Button size="large">Large</Button>
    </div>
  ),
};

export const AllVariants: Story = {
  render: () => (
    <div style={{ display: 'flex', flexDirection: 'column', gap: '16px' }}>
      <Button variant="primary">Primary</Button>
      <Button variant="secondary">Secondary</Button>
      <Button variant="outline">Outline</Button>
      <Button variant="ghost">Ghost</Button>
      <Button variant="danger">Danger</Button>
    </div>
  ),
};
```

## Generated Assets

For each component, I'll generate:

### 1. Component File
- Complete TypeScript implementation
- Styled component definitions
- Props interface
- JSDoc documentation
- Forward ref support
- Accessibility attributes

### 2. Type Definitions
- Props interface
- Variant types
- Event handler types
- Ref types

### 3. Storybook Stories (optional)
- All variant examples
- Interactive controls
- Documentation
- Accessibility checks

### 4. Unit Tests (optional)
- Render tests
- Props tests
- Event handler tests
- Accessibility tests

### 5. Usage Examples
- Basic usage
- Advanced usage
- Composition examples
- Responsive examples

## Features Included

### TypeScript
- Full type safety
- Autocomplete support
- Props validation
- Generic types

### Responsive Design
- Media query breakpoints
- Mobile-first approach
- Flexible sizing
- Touch-friendly

### Animations
- Enter/exit animations
- Hover effects
- Loading states
- Smooth transitions

### Accessibility
- ARIA attributes
- Keyboard navigation
- Focus indicators
- Screen reader support

### Performance
- Memoization where needed
- Lazy loading support
- Optimized re-renders
- Small bundle size

## What Happens Next

1. I'll analyze your requirements
2. Generate complete component file
3. Add all variant styles
4. Include TypeScript definitions
5. Add accessibility features
6. Provide usage examples
7. Include Storybook stories (optional)
8. Add unit tests (optional)

Let me know what component you'd like to generate!
