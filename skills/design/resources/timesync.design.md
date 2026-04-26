# TimeSync Design System Tokens

> Project: TimeSync (Timesheet — Azure DevOps + Harvest Integration)
> Stack: Angular + PrimeNG + Custom Theme

---

## Color Tokens

```scss
// Primary Palette
--color-primary:         #0078D4;   // Azure-inspired blue
--color-primary-hover:   #005A9E;
--color-primary-light:   #EFF6FC;

// Accent
--color-accent:          #00B294;   // Harvest teal — used for logged/approved states
--color-accent-light:    #E6F7F5;

// Semantic
--color-success:         #107C10;   // Submitted / approved
--color-warning:         #FF8C00;   // Pending / draft
--color-danger:          #D13438;   // Rejected / overdue
--color-info:            #0078D4;

// Neutrals
--color-gray-50:         #FAF9F8;
--color-gray-100:        #F3F2F1;
--color-gray-200:        #EDEBE9;
--color-gray-400:        #A19F9D;
--color-gray-600:        #605E5C;
--color-gray-900:        #201F1E;

// Surfaces
--color-bg-page:         #F3F2F1;
--color-bg-card:         #FFFFFF;
--color-bg-sidebar:      #252423;   // Dark sidebar (Fluent-style)
--color-border:          #EDEBE9;
```

---

## Typography Tokens

```scss
// Font Family
--font-family-base:      'Segoe UI', system-ui, sans-serif;

// Font Sizes
--font-size-xs:          0.75rem;   // 12px — timestamps, helper text
--font-size-sm:          0.875rem;  // 14px — table cells, labels
--font-size-base:        1rem;      // 16px — body
--font-size-md:          1.125rem;  // 18px — section headings
--font-size-lg:          1.375rem;  // 22px — card titles
--font-size-xl:          1.75rem;   // 28px — page headings

// Font Weights
--font-weight-normal:    400;
--font-weight-medium:    500;
--font-weight-semibold:  600;
--font-weight-bold:      700;

// Line Heights
--line-height-tight:     1.25;
--line-height-base:      1.5;
```

---

## Spacing / Sizing Tokens

```scss
// Base unit: 4px (Fluent Design)
--spacing-1:   0.25rem;   // 4px
--spacing-2:   0.5rem;    // 8px
--spacing-3:   0.75rem;   // 12px
--spacing-4:   1rem;      // 16px
--spacing-5:   1.25rem;   // 20px
--spacing-6:   1.5rem;    // 24px
--spacing-8:   2rem;      // 32px
--spacing-10:  2.5rem;    // 40px

// Border Radius
--radius-sm:   2px;       // chips, tags
--radius-md:   4px;       // buttons, inputs, cards
--radius-lg:   8px;       // modals, panels

// Shadows (Fluent-style)
--shadow-sm:   0 1.6px 3.6px rgba(0,0,0,0.13), 0 0.3px 0.9px rgba(0,0,0,0.1);
--shadow-md:   0 6.4px 14.4px rgba(0,0,0,0.13), 0 1.2px 3.6px rgba(0,0,0,0.1);
```

---

## Component-Level Guidelines (PrimeNG)

### p-calendar (Timesheet Week Picker)
- Always use `[selectionMode]="'range'"` for week selection
- Show week numbers: `[showWeek]="true"`
- Format: `dd/MM/yyyy`
- Highlight current week row on load

### p-table (Timesheet Grid)
- Frozen first column: employee/task name
- Column headers: week days (Mon–Sun), auto-generated from selected week
- Cell input: inline `p-inputNumber` with `[min]="0"` and `[max]="24"`
- Row footer: auto-sum of daily hours
- Color coding rows by status:
  - Draft → no highlight
  - Submitted → `--color-primary-light` row background
  - Approved → `--color-accent-light` row background
  - Rejected → `rgba(209,52,56,0.08)` row background

### p-dropdown (Project / Task selectors)
- Always show project code + name: `[optionLabel]="'displayName'"`
- Group by client when listing projects
- Set `[filter]="true"` always (project lists can be long)

### p-badge (Status indicators)
- Draft: `severity="secondary"`
- Submitted: `severity="info"`
- Approved: `severity="success"`
- Rejected: `severity="danger"`
- Overdue: `severity="warning"`

### p-progressBar (Weekly hour target)
- Show percentage of target hours logged (e.g. 32/40h = 80%)
- Color: use `--color-accent` for on-track, `--color-warning` for under, `--color-danger` for over

### p-dialog (Submit / Approve confirmation)
- Width: `480px` — compact confirmation dialogs only
- No scrollable content inside confirmation dialogs

---

## Grid / Layout Rules

```
Page layout:     Dark sidebar (collapsible) + main content area
Sidebar width:   220px (expanded), 48px (icon-only collapsed)
Content padding: 24px all sides
Card gutter:     16px (--spacing-4)

Breakpoints:
  Mobile:   < 768px   — sidebar hidden, hamburger toggle
  Tablet:   768–1280px — sidebar icon-only collapsed by default
  Desktop:  > 1280px  — sidebar fully expanded

Timesheet grid:  Horizontal scroll on tablet/mobile
                 Sticky header row + frozen first column always
Form layout:     Single column, label above input
                 Max form width: 560px centered

Status bar:      Fixed top bar showing week, total hours, submit button
                 Height: 52px, background: --color-bg-card, border-bottom: --color-border
```
