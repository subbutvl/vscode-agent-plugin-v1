# MGC Design System Tokens

> Project: MGC (PrimeNG + Metronic Theme)
> Stack: Angular + PrimeNG + SCSS

---

## Color Tokens

```scss
// Primary Palette
--color-primary:         #3699FF;   // Metronic blue — buttons, links, active states
--color-primary-hover:   #187DE4;
--color-primary-light:   #E1F0FF;   // Backgrounds, badges

// Secondary
--color-secondary:       #E4E6EF;
--color-secondary-dark:  #D1D3E0;

// Semantic
--color-success:         #1BC5BD;
--color-warning:         #FFA800;
--color-danger:          #F64E60;
--color-info:            #8950FC;

// Neutrals
--color-gray-100:        #F3F6F9;
--color-gray-200:        #EBEDF3;
--color-gray-500:        #B5B5C3;
--color-gray-700:        #5E6278;
--color-gray-900:        #181C32;

// Surfaces
--color-bg-page:         #EEF0F8;
--color-bg-card:         #FFFFFF;
--color-border:          #E4E6EF;
```

---

## Typography Tokens

```scss
// Font Family
--font-family-base:      'Poppins', sans-serif;

// Font Sizes
--font-size-xs:          0.75rem;   // 12px — labels, badges
--font-size-sm:          0.85rem;   // 13.6px — secondary text
--font-size-base:        1rem;      // 16px — body
--font-size-md:          1.075rem;  // 17.2px — subtitles
--font-size-lg:          1.25rem;   // 20px — card headings
--font-size-xl:          1.5rem;    // 24px — page titles
--font-size-2xl:         2rem;      // 32px — hero headings

// Font Weights
--font-weight-normal:    400;
--font-weight-medium:    500;
--font-weight-semibold:  600;
--font-weight-bold:      700;

// Line Heights
--line-height-tight:     1.2;
--line-height-base:      1.5;
--line-height-loose:     1.75;
```

---

## Spacing / Sizing Tokens

```scss
// Base unit: 4px
--spacing-1:   0.25rem;   // 4px
--spacing-2:   0.5rem;    // 8px
--spacing-3:   0.75rem;   // 12px
--spacing-4:   1rem;      // 16px
--spacing-5:   1.25rem;   // 20px
--spacing-6:   1.5rem;    // 24px
--spacing-8:   2rem;      // 32px
--spacing-10:  2.5rem;    // 40px
--spacing-12:  3rem;      // 48px
--spacing-16:  4rem;      // 64px

// Border Radius
--radius-sm:   0.275rem;  // inputs, small chips
--radius-md:   0.475rem;  // buttons, cards
--radius-lg:   0.85rem;   // modals, panels
--radius-pill: 50rem;     // badge pills

// Shadows
--shadow-sm:   0 0 20px 0 rgba(76,87,125,0.02);
--shadow-md:   0 0 50px 0 rgba(82,63,105,0.15);
```

---

## Component-Level Guidelines (PrimeNG)

### p-button
- Use `severity` prop for semantic variants: `success`, `warning`, `danger`, `info`
- Default size: no `size` prop (medium)
- Icon-only buttons must include `pTooltip` for accessibility
- Avoid inline `style` — use `styleClass` with Metronic utility classes

### p-table
- Always set `[responsiveLayout]="'scroll'"`
- Use `stripedRows` for data-heavy tables
- Header cells: `font-weight: 600`, color `--color-gray-700`
- Row hover: background `--color-primary-light`
- Pagination: use `p-paginator` with `[rowsPerPageOptions]="[10, 25, 50]"`

### p-dialog / p-dynamicDialog
- Max width: `600px` for forms, `900px` for data views
- Always include header and footer slots
- Footer: right-aligned, Cancel (secondary) + Confirm (primary) button order

### p-dropdown / p-multiSelect
- Set `[filter]="true"` when options > 8
- Placeholder text must describe the field, not just say "Select"
- Always bind `optionLabel` and `optionValue` explicitly

### p-card
- Use for grouping related form sections
- Header slot: page section title in `--font-size-md`, `--font-weight-semibold`
- Padding: `--spacing-6` on all sides

### p-toast / p-messages
- p-toast: position `top-right`, life `4000ms`
- p-messages: inline, use for form-level validation errors only

---

## Grid / Layout Rules

```
Page layout:     Metronic aside + content wrapper
Aside width:     265px (expanded), 75px (collapsed)
Content padding: 30px horizontal, 25px vertical
Card gutter:     24px (--spacing-6)

Breakpoints:
  Mobile:   < 768px
  Tablet:   768px – 1024px
  Desktop:  > 1024px

Column grid:     12-column, gutters 24px
Form layout:     2-column on desktop, 1-column on mobile
                 Label above input (not inline)
Table layout:    Full width, scroll container on mobile
Modal overlay:   rgba(0,0,0,0.5) backdrop
```
