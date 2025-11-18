---
description: Interactive Material component generator with templates, theming, and accessibility built-in
---

I'll help you generate production-ready Angular Material components with complete templates, styles, and TypeScript code.

## What This Generates

A complete Material component package:
- TypeScript component file (standalone)
- HTML template file (separate, NO inline)
- SCSS style file with theming
- Complete Material imports
- Accessibility attributes (WCAG 2.1 AA)
- Responsive design patterns
- JSDoc documentation

## Component Types

### 1. Form Component
Complete form with Material form controls and validation.

**Includes:**
- Form fields (input, select, date picker, etc.)
- Reactive forms with validation
- Error messages
- Submit/cancel buttons
- Loading states
- Accessibility labels

**Example Output:**
```typescript
// user-form.component.ts
@Component({
  selector: 'app-user-form',
  standalone: true,
  imports: [
    CommonModule,
    ReactiveFormsModule,
    MatFormFieldModule,
    MatInputModule,
    MatButtonModule
  ],
  templateUrl: './user-form.component.html',
  styleUrls: ['./user-form.component.scss']
})
export class UserFormComponent {
  userForm = this.fb.group({
    name: ['', [Validators.required, Validators.minLength(2)]],
    email: ['', [Validators.required, Validators.email]]
  });
}
```

### 2. Data Table Component
Material table with sorting, filtering, and pagination.

**Includes:**
- MatTable with sorting
- MatPaginator
- Search/filter functionality
- Row selection (checkbox)
- Action buttons
- Responsive design
- Loading skeleton

**Features:**
- Virtual scrolling for large datasets
- Custom column templates
- Export functionality
- Bulk actions
- Status chips

### 3. Dashboard Component
Dashboard layout with Material cards and widgets.

**Includes:**
- Responsive grid layout
- Multiple card types
- Charts integration (optional)
- Stats widgets
- Recent activity list
- Quick actions
- Collapsible sections

### 4. Dialog Component
Material dialog with form or content.

**Includes:**
- MatDialog configuration
- Dialog component
- Data passing
- Close/cancel actions
- Validation before close
- Responsive sizing

**Types:**
- Confirmation dialog
- Form dialog
- Info dialog
- Alert dialog

### 5. Navigation Component
Complete navigation layout with sidenav.

**Includes:**
- MatSidenav with toolbar
- Responsive drawer (mobile)
- Navigation list
- User menu
- Breadcrumbs
- Theme toggle
- Notifications

### 6. Stepper Component
Multi-step form with Material stepper.

**Includes:**
- MatStepper (horizontal/vertical)
- Step validation
- Navigation buttons
- Progress indicator
- Review step
- Completion actions

### 7. List Component
Material list with actions and avatars.

**Includes:**
- MatList with dividers
- Avatar/icon support
- Secondary actions
- Item selection
- Virtual scrolling
- Empty state

### 8. Card Component
Material card with header, content, footer.

**Includes:**
- MatCard structure
- Card actions
- Card media
- Expandable content
- Loading state
- Interactive variants

## Quick Generation

Just tell me:
"Generate a [component type] named [name]"

**Examples:**
- "Generate a form component named UserProfile"
- "Generate a data table named ProductList"
- "Generate a dashboard component named AdminDashboard"
- "Generate a dialog named ConfirmDelete"

## Custom Generation

Provide details:

### For Forms:
- **Component name**: "user-registration"
- **Fields**: name, email, password, country, dateOfBirth
- **Validation**: required, email format, min length
- **Features**: password visibility toggle, autocomplete
- **Theme**: primary color for buttons

### For Tables:
- **Component name**: "user-management-table"
- **Columns**: id, name, email, role, status, actions
- **Features**: sorting, filtering, pagination, row selection
- **Actions**: edit, delete, view
- **Page size**: 25 rows per page

### For Dashboards:
- **Component name**: "sales-dashboard"
- **Widgets**: revenue card, orders card, customers card, chart
- **Layout**: 4-column responsive grid
- **Refresh**: auto-refresh every 30s

## Generated File Structure

```
components/
└── your-component/
    ├── your-component.component.ts      # Component logic
    ├── your-component.component.html    # Template (separate)
    ├── your-component.component.scss    # Styles with theming
    └── your-component.component.spec.ts # Unit tests
```

## Example: Generated Form Component

**your-form.component.ts:**
```typescript
/**
 * YourFormComponent
 *
 * @description Material form with validation and accessibility
 * @example <app-your-form (formSubmit)="onSubmit($event)"></app-your-form>
 */
@Component({
  selector: 'app-your-form',
  standalone: true,
  imports: [
    CommonModule,
    ReactiveFormsModule,
    MatFormFieldModule,
    MatInputModule,
    MatButtonModule,
    MatIconModule
  ],
  templateUrl: './your-form.component.html',
  styleUrls: ['./your-form.component.scss']
})
export class YourFormComponent implements OnInit {
  private fb = inject(FormBuilder);

  form = this.fb.group({
    name: ['', [Validators.required, Validators.minLength(2)]],
    email: ['', [Validators.required, Validators.email]]
  });

  isLoading = false;

  ngOnInit(): void {
    // Initialization logic
  }

  onSubmit(): void {
    if (this.form.valid) {
      this.isLoading = true;
      // Submit logic
    }
  }

  getErrorMessage(field: string): string {
    const control = this.form.get(field);
    if (control?.hasError('required')) {
      return `${field} is required`;
    }
    if (control?.hasError('email')) {
      return 'Invalid email format';
    }
    return '';
  }
}
```

**your-form.component.html:**
```html
<div class="form-container">
  <h2 class="form-title">Form Title</h2>

  <form [formGroup]="form" (ngSubmit)="onSubmit()" class="form">
    <!-- Name Field -->
    <mat-form-field appearance="outline" class="form-field">
      <mat-label>Name</mat-label>
      <input
        matInput
        formControlName="name"
        placeholder="Enter your name"
        required
      />
      <mat-icon matPrefix>person</mat-icon>
      <mat-error *ngIf="form.get('name')?.invalid">
        {{ getErrorMessage('name') }}
      </mat-error>
    </mat-form-field>

    <!-- Email Field -->
    <mat-form-field appearance="outline" class="form-field">
      <mat-label>Email</mat-label>
      <input
        matInput
        type="email"
        formControlName="email"
        placeholder="user@example.com"
        required
      />
      <mat-icon matPrefix>email</mat-icon>
      <mat-error *ngIf="form.get('email')?.invalid">
        {{ getErrorMessage('email') }}
      </mat-error>
    </mat-form-field>

    <!-- Actions -->
    <div class="form-actions">
      <button mat-button type="button" (click)="form.reset()">
        Reset
      </button>
      <button
        mat-raised-button
        color="primary"
        type="submit"
        [disabled]="form.invalid || isLoading"
      >
        @if (isLoading) {
          <mat-spinner diameter="20"></mat-spinner>
          Processing...
        } @else {
          Submit
        }
      </button>
    </div>
  </form>
</div>
```

**your-form.component.scss:**
```scss
.form-container {
  max-width: 600px;
  margin: 24px auto;
  padding: 24px;
}

.form-title {
  font-size: 24px;
  font-weight: 500;
  margin-bottom: 24px;
  color: var(--mat-sys-on-surface);
}

.form {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.form-field {
  width: 100%;
}

.form-actions {
  display: flex;
  justify-content: flex-end;
  gap: 16px;
  margin-top: 16px;
}

// Responsive
@media (max-width: 768px) {
  .form-container {
    padding: 16px;
  }

  .form-actions {
    flex-direction: column-reverse;

    button {
      width: 100%;
    }
  }
}
```

## Features Included

### Accessibility (WCAG 2.1 AA)
- ARIA labels on all interactive elements
- Keyboard navigation support
- Focus indicators
- Screen reader compatible
- Color contrast compliant
- Form error announcements

### Responsive Design
- Mobile-first approach
- Breakpoints for tablet and desktop
- Touch-friendly controls
- Flexible layouts
- Responsive typography

### Theming Support
- Material theme variables
- Light/dark mode compatible
- Custom color palettes
- Typography hierarchy
- Consistent spacing (8px grid)

### Performance
- OnPush change detection
- Lazy loading modules
- Virtual scrolling (tables)
- Efficient change tracking
- Minimal re-renders

### Best Practices
- Separate template files (NO inline)
- Reactive forms
- TypeScript strict mode
- JSDoc documentation
- Unit test scaffolds
- Error handling

## Configuration Options

When generating, you can specify:

**General:**
- Component name
- Selector prefix (default: 'app-')
- Change detection strategy
- View encapsulation

**Forms:**
- Form field types
- Validation rules
- Async validators
- Custom error messages
- Submit behavior

**Tables:**
- Column definitions
- Sort configuration
- Filter options
- Pagination settings
- Row actions

**Theming:**
- Color palette (primary, accent, warn)
- Typography scale
- Spacing multiplier
- Border radius
- Shadow elevation

## What Happens Next

1. I'll analyze your requirements
2. Generate TypeScript component file
3. Create HTML template (separate file)
4. Generate SCSS with theming
5. Add accessibility attributes
6. Include JSDoc documentation
7. Provide usage instructions
8. Add import statements

Let me know what Material component you'd like to generate!
