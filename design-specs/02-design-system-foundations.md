# 🏗️ Design System Foundations - ricevuta.studio

> **Document Type**: Design System Specifications  
> **Platform**: ricevuta.studio  
> **Version**: 1.0  
> **Created**: 2026-01-22  
> **Purpose**: Define comprehensive, scalable design system with reusable components and patterns

---

## 📌 Design System Philosophy

### Core Principles

**1. Consistency First**
- Same patterns for same actions across entire platform
- Predictable user experience reduces cognitive load
- Shared component library ensures consistency

**2. Accessibility by Default**
- WCAG 2.1 Level AA minimum (AAA preferred)
- Keyboard navigation, screen reader support
- Color + icon/text for status (never color alone)
- Touch targets minimum 44x44px

**3. Scalability & Maintainability**
- Modular, composable components
- Clear naming conventions
- Documentation with usage examples
- Version control for design tokens

**4. Performance Optimized**
- Lightweight components
- Lazy loading strategies
- Minimal animation complexity
- Optimized asset delivery

---

## 🎨 Design Tokens

### Color Tokens

**Primary Colors**
```css
--color-primary-50:  #EFF6FF;
--color-primary-100: #DBEAFE;
--color-primary-200: #BFDBFE;
--color-primary-300: #93C5FD;
--color-primary-400: #60A5FA;
--color-primary-500: #3B82F6;
--color-primary-600: #2563EB; /* Main brand color */
--color-primary-700: #1D4ED8;
--color-primary-800: #1E40AF;
--color-primary-900: #1E3A8A;
```

**Neutral Colors**
```css
--color-gray-50:  #F9FAFB;
--color-gray-100: #F3F4F6;
--color-gray-200: #E5E7EB;
--color-gray-300: #D1D5DB;
--color-gray-400: #9CA3AF;
--color-gray-500: #6B7280;
--color-gray-600: #4B5563;
--color-gray-700: #374151;
--color-gray-800: #1F2937;
--color-gray-900: #111827;
```

**Semantic Colors**
```css
/* Success */
--color-success-50:  #ECFDF5;
--color-success-100: #D1FAE5;
--color-success-500: #10B981;
--color-success-700: #047857;

/* Warning */
--color-warning-50:  #FFFBEB;
--color-warning-100: #FEF3C7;
--color-warning-500: #F59E0B;
--color-warning-700: #B45309;

/* Error */
--color-error-50:  #FEF2F2;
--color-error-100: #FEE2E2;
--color-error-500: #EF4444;
--color-error-700: #B91C1C;

/* Info */
--color-info-50:  #EFF6FF;
--color-info-100: #DBEAFE;
--color-info-500: #3B82F6;
--color-info-700: #1D4ED8;
```

### Typography Tokens

**Font Families**
```css
--font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', sans-serif;
--font-mono: 'JetBrains Mono', 'Fira Code', 'Courier New', monospace;
```

**Font Sizes**
```css
--text-xs:   0.75rem;   /* 12px */
--text-sm:   0.875rem;  /* 14px */
--text-base: 1rem;      /* 16px */
--text-lg:   1.125rem;  /* 18px */
--text-xl:   1.25rem;   /* 20px */
--text-2xl:  1.5rem;    /* 24px */
--text-3xl:  1.875rem;  /* 30px */
--text-4xl:  2.25rem;   /* 36px */
--text-5xl:  3rem;      /* 48px */
```

**Font Weights**
```css
--font-normal:    400;
--font-medium:    500;
--font-semibold:  600;
--font-bold:      700;
```

**Line Heights**
```css
--leading-none:   1;
--leading-tight:  1.25;
--leading-snug:   1.375;
--leading-normal: 1.5;
--leading-relaxed: 1.625;
--leading-loose:  1.75;
```

### Spacing Tokens

```css
--space-0:  0;
--space-1:  0.25rem;  /* 4px */
--space-2:  0.5rem;   /* 8px */
--space-3:  0.75rem;  /* 12px */
--space-4:  1rem;     /* 16px */
--space-5:  1.25rem;  /* 20px */
--space-6:  1.5rem;   /* 24px */
--space-8:  2rem;     /* 32px */
--space-10: 2.5rem;   /* 40px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
--space-20: 5rem;     /* 80px */
--space-24: 6rem;     /* 96px */
```

### Border Radius Tokens

```css
--radius-none: 0;
--radius-sm:   0.25rem;  /* 4px */
--radius-md:   0.5rem;   /* 8px */
--radius-lg:   0.75rem;  /* 12px */
--radius-xl:   1rem;     /* 16px */
--radius-full: 9999px;   /* Full circle */
```

### Shadow Tokens

```css
--shadow-xs: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
--shadow-sm: 0 1px 3px 0 rgba(0, 0, 0, 0.1),
             0 1px 2px 0 rgba(0, 0, 0, 0.06);
--shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
             0 2px 4px -1px rgba(0, 0, 0, 0.06);
--shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
             0 4px 6px -2px rgba(0, 0, 0, 0.05);
--shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
             0 10px 10px -5px rgba(0, 0, 0, 0.04);
```

### Animation Tokens

```css
--duration-fast: 150ms;
--duration-base: 250ms;
--duration-slow: 350ms;

--easing-linear:  linear;
--easing-in:      cubic-bezier(0.4, 0, 1, 1);
--easing-out:     cubic-bezier(0, 0, 0.2, 1);
--easing-in-out:  cubic-bezier(0.4, 0, 0.2, 1);
```

---

## 🧩 Component Library

### Buttons

#### Primary Button
**Usage**: Main call-to-action, primary actions
**Visual**:
- Background: `--color-primary-600`
- Text: White
- Padding: `12px 24px` (base), `10px 20px` (small), `14px 28px` (large)
- Border Radius: `--radius-md`
- Font Weight: `--font-medium`
- Hover: Background darkens to `--color-primary-700`
- Focus: 3px outline in `--color-primary-300`
- Disabled: Opacity 50%, cursor not-allowed

**Example**:
```html
<button class="btn btn-primary">
  Crea Ricevuta
</button>
```

#### Secondary Button
**Usage**: Secondary actions, cancel operations
**Visual**:
- Background: Transparent
- Border: 1px solid `--color-gray-300`
- Text: `--color-gray-700`
- Padding: Same as primary
- Hover: Background `--color-gray-50`, border `--color-gray-400`

#### Destructive Button
**Usage**: Delete, remove, dangerous actions
**Visual**:
- Background: Transparent
- Text: `--color-error-600`
- Hover: Background `--color-error-50`

#### Icon Button
**Usage**: Actions with icon only (no text)
**Visual**:
- Square: 40x40px (base), 36x36px (small), 44x44px (large)
- Icon: 20px (base), 18px (small), 24px (large)
- Border Radius: `--radius-md`
- Hover: Background `--color-gray-100`

---

### Form Elements

#### Text Input
**Visual**:
- Height: 40px (base), 36px (small), 44px (large)
- Padding: `10px 12px`
- Border: 1px solid `--color-gray-300`
- Border Radius: `--radius-md`
- Font Size: `--text-base`
- Placeholder: `--color-gray-400`
- Focus: Border `--color-primary-600`, outline 3px `--color-primary-200`
- Error: Border `--color-error-500`, text `--color-error-700`
- Disabled: Background `--color-gray-100`, cursor not-allowed

**States**:
```html
<!-- Default -->
<input type="text" placeholder="Inserisci importo">

<!-- Error -->
<input type="text" class="error" aria-invalid="true">
<span class="error-message">Campo obbligatorio</span>

<!-- Disabled -->
<input type="text" disabled>
```

#### Select Dropdown
**Visual**: Similar to text input
- Chevron icon on right
- Options list: White background, shadow-lg
- Selected option: Background `--color-primary-50`
- Hover option: Background `--color-gray-50`

#### Checkbox
**Visual**:
- Size: 20x20px
- Border: 2px solid `--color-gray-400`
- Border Radius: `--radius-sm`
- Checked: Background `--color-primary-600`, white checkmark
- Focus: Outline 3px `--color-primary-200`

#### Radio Button
**Visual**: Similar to checkbox but circular
- Border Radius: `--radius-full`
- Selected: Inner circle `--color-primary-600`

#### Toggle Switch
**Visual**:
- Width: 44px, Height: 24px
- Border Radius: `--radius-full`
- Off: Background `--color-gray-300`
- On: Background `--color-primary-600`
- Knob: 20px circle, white

#### Label
**Visual**:
- Font Size: `--text-sm`
- Font Weight: `--font-medium`
- Color: `--color-gray-700`
- Margin Bottom: `--space-2`

#### Helper Text
**Visual**:
- Font Size: `--text-sm`
- Color: `--color-gray-500`
- Margin Top: `--space-1`

---

### Cards

#### Basic Card
**Usage**: Content containers, dashboard widgets
**Visual**:
- Background: White
- Border: 1px solid `--color-gray-200` (optional)
- Border Radius: `--radius-lg`
- Padding: `--space-6` (24px)
- Shadow: `--shadow-sm`
- Hover: Shadow transitions to `--shadow-md`

**Anatomy**:
```html
<div class="card">
  <div class="card-header">
    <h3 class="card-title">Titolo Card</h3>
    <button class="card-action">...</button>
  </div>
  <div class="card-body">
    Content goes here
  </div>
  <div class="card-footer">
    <button>Azione</button>
  </div>
</div>
```

#### Elevated Card
**Usage**: Important content, modals
**Visual**: Same as basic card but `--shadow-lg`

#### Outlined Card
**Usage**: Secondary content, less emphasis
**Visual**:
- Background: Transparent
- Border: 2px solid `--color-gray-200`
- No shadow
- Hover: Border `--color-gray-300`

---

### Alerts & Notifications

#### Alert Component
**Variants**: Info, Success, Warning, Error

**Info Alert**:
```html
<div class="alert alert-info">
  <svg class="alert-icon"><!-- Info icon --></svg>
  <div class="alert-content">
    <h4 class="alert-title">Informazione</h4>
    <p class="alert-message">Messaggio informativo</p>
  </div>
  <button class="alert-close">×</button>
</div>
```

**Visual**:
- Background: Semantic color -50 variant
- Border-left: 4px solid semantic color -500
- Icon: Semantic color -500
- Padding: `--space-4`
- Border Radius: `--radius-md`

**Success**: Green theme
**Warning**: Amber theme
**Error**: Red theme
**Info**: Blue theme

#### Toast Notification
**Usage**: Temporary feedback messages
**Visual**:
- Position: Fixed, top-right or bottom-right
- Width: Max 400px
- Background: White
- Shadow: `--shadow-xl`
- Border Radius: `--radius-lg`
- Animation: Slide in from right, auto-dismiss after 5s
- Close button: Top-right corner

---

### Badges & Tags

#### Badge
**Usage**: Status indicators, counts
**Visual**:
- Height: 20px (small), 24px (base)
- Padding: `4px 8px`
- Border Radius: `--radius-full`
- Font Size: `--text-xs` (small), `--text-sm` (base)
- Font Weight: `--font-medium`

**Variants**:
```html
<span class="badge badge-primary">Attiva</span>
<span class="badge badge-success">Completata</span>
<span class="badge badge-warning">In Attesa</span>
<span class="badge badge-error">Errore</span>
<span class="badge badge-gray">Archiviata</span>
```

#### Tag (Pill)
**Usage**: Categories, filters, removable items
**Visual**: Similar to badge
- Optional close button (×)
- Hover: Background darkens

---

### Loading States

#### Spinner
**Usage**: Loading indicator
**Visual**:
- Size: 16px (small), 24px (base), 32px (large)
- Color: `--color-primary-600` or `--color-gray-400`
- Animation: 0.75s linear infinite rotation

#### Skeleton Loader
**Usage**: Content placeholder while loading
**Visual**:
- Background: `--color-gray-200`
- Border Radius: Matches content shape
- Animation: Shimmer effect (gradient moving)

**Example**:
```html
<div class="skeleton skeleton-text"></div>
<div class="skeleton skeleton-avatar"></div>
<div class="skeleton skeleton-card"></div>
```

#### Progress Bar
**Usage**: Upload progress, multi-step processes
**Visual**:
- Height: 8px (base), 6px (small), 12px (large)
- Background: `--color-gray-200`
- Fill: `--color-primary-600`
- Border Radius: `--radius-full`
- Transition: Smooth width animation

---

### Navigation

#### Top Navigation Bar
**Visual**:
- Height: 64px
- Background: White
- Border Bottom: 1px solid `--color-gray-200`
- Shadow: `--shadow-sm`
- Padding: `0 --space-6`
- Logo: Left side
- Nav items: Center or right
- User menu: Far right

**Mobile**: 
- Hamburger menu icon
- Slide-out drawer

#### Sidebar Navigation
**Visual**:
- Width: 240px (collapsed: 64px)
- Background: White or `--color-gray-50`
- Border Right: 1px solid `--color-gray-200`
- Item height: 40px
- Item padding: `--space-3 --space-4`
- Active item: Background `--color-primary-50`, left border `--color-primary-600`
- Hover: Background `--color-gray-100`
- Icon: 20px, left aligned
- Text: `--text-sm`

#### Tabs
**Visual**:
- Border Bottom: 2px solid `--color-gray-200`
- Tab padding: `--space-3 --space-4`
- Active tab: Border-bottom `--color-primary-600`, text `--color-primary-600`
- Inactive tab: Text `--color-gray-500`
- Hover: Text `--color-gray-700`

#### Breadcrumbs
**Visual**:
- Font Size: `--text-sm`
- Color: `--color-gray-500`
- Separator: "/" or "›" in `--color-gray-400`
- Current page: `--color-gray-900`, not a link
- Links: Hover underline

---

### Modal/Dialog

**Visual**:
- Overlay: Black 50% opacity
- Container: White, centered
- Max Width: 500px (small), 700px (medium), 900px (large)
- Border Radius: `--radius-xl`
- Shadow: `--shadow-xl`
- Padding: `--space-6`

**Anatomy**:
```html
<div class="modal-overlay">
  <div class="modal">
    <div class="modal-header">
      <h3>Titolo Modal</h3>
      <button class="modal-close">×</button>
    </div>
    <div class="modal-body">
      Content
    </div>
    <div class="modal-footer">
      <button class="btn-secondary">Annulla</button>
      <button class="btn-primary">Conferma</button>
    </div>
  </div>
</div>
```

**Animation**:
- Fade in overlay: 200ms
- Scale modal from 0.95 to 1: 250ms ease-out
- Reverse on close

---

### Tables

**Visual**:
- Border: 1px solid `--color-gray-200`
- Border Radius: `--radius-lg` (table container)
- Header: Background `--color-gray-50`, font-weight `--font-semibold`
- Cell padding: `--space-3 --space-4`
- Row hover: Background `--color-gray-50`
- Striped rows (optional): Alternating `--color-gray-50`
- Sorting: Icon next to header text

**Responsive**:
- Mobile: Convert to card-based layout
- Or: Horizontal scroll with fixed columns

---

### Tooltips

**Visual**:
- Background: `--color-gray-900`
- Text: White
- Font Size: `--text-sm`
- Padding: `--space-2 --space-3`
- Border Radius: `--radius-md`
- Shadow: `--shadow-lg`
- Arrow: 8px triangle pointing to trigger

**Behavior**:
- Trigger: Hover or focus
- Position: Auto (top, bottom, left, right based on space)
- Delay: 300ms before showing
- Max width: 200px

---

### Dropdowns

**Visual**:
- Container: White background
- Border: 1px solid `--color-gray-200`
- Border Radius: `--radius-md`
- Shadow: `--shadow-lg`
- Max height: 300px (scrollable)
- Item padding: `--space-2 --space-3`
- Item hover: Background `--color-gray-100`
- Selected item: Background `--color-primary-50`
- Divider: 1px solid `--color-gray-200`

---

## 📱 Responsive Breakpoints

```css
/* Mobile First Approach */
--breakpoint-sm: 640px;   /* Small tablets */
--breakpoint-md: 768px;   /* Tablets */
--breakpoint-lg: 1024px;  /* Desktop */
--breakpoint-xl: 1280px;  /* Large desktop */
--breakpoint-2xl: 1536px; /* Extra large */
```

### Layout Grid

**Desktop**: 12-column grid
- Gutter: `--space-6` (24px)
- Max width: 1280px (centered)

**Tablet**: 8-column grid
- Gutter: `--space-4` (16px)

**Mobile**: 4-column grid
- Gutter: `--space-4` (16px)
- Padding: `--space-4` (16px)

---

## ♿ Accessibility Standards

### Color Contrast
- Text (base): Minimum 4.5:1 (WCAG AA)
- Text (large): Minimum 3:1
- UI components: Minimum 3:1
- Target: AAA where possible

### Keyboard Navigation
- All interactive elements focusable
- Focus indicators visible (3px outline)
- Logical tab order
- Skip links for main content

### Screen Readers
- Semantic HTML elements
- ARIA labels where needed
- Alt text for images
- Announce dynamic content changes

### Touch Targets
- Minimum size: 44x44px
- Adequate spacing: 8px between targets

---

## 🎨 Dark Mode (Future)

Prepare design system for dark mode support:
- Use CSS custom properties for all colors
- Define dark mode color palette
- Test contrast ratios in both modes
- Consider user preference (prefers-color-scheme)

---

## 📦 Component States

Every interactive component should have:
1. **Default**: Resting state
2. **Hover**: Mouse over
3. **Focus**: Keyboard focused
4. **Active**: Being clicked/pressed
5. **Disabled**: Non-interactive
6. **Loading**: Processing action
7. **Error**: Invalid or failed state
8. **Success**: Completed successfully

---

## 🔧 Implementation Guidelines

### CSS Architecture
- Use CSS custom properties for tokens
- BEM naming convention or CSS modules
- Utility classes for common patterns
- Component-specific styles scoped

### Component Documentation
Each component should document:
- Purpose and usage
- Props/attributes
- Variants and sizes
- Accessibility considerations
- Code examples
- Do's and don'ts

---

*This design system is a living document and will evolve with the platform.*
