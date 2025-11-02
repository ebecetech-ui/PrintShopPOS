# Design Guidelines: Aplikasi POS Percetakan

## Design Approach

**Selected System:** Material Design 3
**Rationale:** Business application requiring data-dense interfaces, clear hierarchy, and efficient workflow patterns. Material Design provides robust components for dashboards, forms, tables, and role-based navigation essential for POS systems.

**Key Design Principles:**
- Efficiency first: Minimize clicks to complete tasks
- Clear data hierarchy: Information must be scannable at a glance
- Role-appropriate interfaces: Each user sees only relevant functions
- Consistent workflows: Similar tasks follow identical patterns

## Typography System

**Font Family:** Inter (via Google Fonts CDN)

**Type Scale:**
- Display: 32px/bold - Dashboard headers, page titles
- H1: 24px/semibold - Section headers, modal titles
- H2: 20px/semibold - Card headers, subsection titles
- H3: 18px/medium - Table headers, form section labels
- Body Large: 16px/regular - Primary content, form inputs
- Body: 14px/regular - Table data, secondary content
- Caption: 12px/regular - Helper text, metadata, timestamps
- Label: 14px/medium - Form labels, button text

**Line Height:** 1.5 for body text, 1.2 for headings

## Layout System

**Spacing Primitives:** Tailwind units of 1, 2, 3, 4, 6, 8, 12, 16
- Micro spacing (within components): 1, 2
- Component padding: 3, 4, 6
- Section spacing: 8, 12, 16
- Page margins: 6, 8

**Grid System:**
- Sidebar navigation: 240px fixed width (desktop)
- Main content: flex-1 with max-width constraints
- Dashboard cards: grid-cols-1 md:grid-cols-2 lg:grid-cols-4
- Form layouts: max-w-4xl with two-column responsive grids
- Table containers: w-full with horizontal scroll on mobile

**Container Widths:**
- Dashboard: w-full (edge-to-edge cards)
- Forms: max-w-4xl
- Settings pages: max-w-6xl
- Data tables: w-full with overflow handling

## Component Library

### Navigation Structure

**Sidebar Navigation (Desktop):**
- Fixed left sidebar, 240px width
- Collapsible to icon-only (64px) view
- Role-based menu items with icons (Material Icons via CDN)
- Active state with subtle indicator
- Nested menu expansion for submenu items
- User profile section at bottom with role badge

**Mobile Navigation:**
- Bottom navigation bar for primary sections
- Hamburger menu for secondary features
- Overlay drawer for full menu access

### Dashboard Components

**Metric Cards:**
- Elevated cards with rounded corners (rounded-lg)
- Icon + Label + Large number format
- Optional trend indicator (arrow up/down with percentage)
- Grid layout: 4 columns desktop, 2 tablet, 1 mobile
- Padding: p-6
- Shadow: subtle elevation

**Chart Containers:**
- White background cards
- Header with title + date range selector
- Chart area with proper aspect ratio
- Use Chart.js for line/bar charts
- Responsive height adjustment

### Data Tables

**Table Structure:**
- Sticky header row
- Alternating row backgrounds for readability
- Hover state on rows
- Action column (right-aligned) with icon buttons
- Pagination controls at bottom
- Search and filter toolbar above table
- Responsive: cards on mobile, table on desktop

**Table Toolbar:**
- Search input (left)
- Filter dropdown buttons
- Action buttons (Add New, Export) right-aligned
- Spacing: p-4 with gap-3

### Forms

**Form Layout:**
- Two-column grid on desktop (grid-cols-2 gap-6)
- Single column on mobile
- Full-width for textareas and special inputs
- Grouped related fields with subtle dividers

**Form Controls:**
- Text inputs: h-12, border, rounded-md, px-4
- Labels: above input, font-medium, mb-2
- Helper text: text-sm below input
- Error states: border highlight + error message
- Dropdowns: consistent height with inputs
- Date pickers: calendar icon right-aligned

**Action Buttons:**
- Primary: filled, prominent (Submit, Save)
- Secondary: outlined (Cancel, Reset)
- Height: h-12, padding: px-6
- Positioned: right-aligned in footer
- Spacing between buttons: gap-3

### Modal Patterns

**Standard Modals:**
- Centered overlay with backdrop blur
- Max width: max-w-2xl (forms), max-w-4xl (data views)
- Header: title + close button
- Content area: p-6
- Footer: action buttons right-aligned
- Mobile: full-screen with slide-up animation

### Cards & Containers

**Content Cards:**
- Rounded corners: rounded-lg
- Padding: p-6
- Subtle shadow for elevation
- Header with title + optional action button
- Content area with appropriate spacing

**Invoice Display:**
- Clean layout with clear sections
- Company info header
- Line items in table format
- Summary totals clearly separated
- Print button prominently placed

## Special Components

### Order Form:**
- Product selection dropdown with search
- Quantity + unit selector inline
- Dynamic item list with add/remove
- Real-time price calculation display
- Customer selection with quick-add option
- Notes textarea
- Payment method selector
- Submit generates invoice

### Pembukuan Dashboard:**
- Summary cards (Total Piutang, Uang Masuk, Pengeluaran)
- Date range filter prominent
- Transaction list with filtering
- Export button for reports
- Chart visualization for trends

### Role Management:**
- User table with role badges
- Inline role editing
- Permission matrix view
- Add user form in modal

## Responsive Behavior

**Breakpoints:**
- Mobile: < 768px - Single column, bottom nav, simplified tables as cards
- Tablet: 768px - 1024px - Two columns, sidebar visible
- Desktop: > 1024px - Full layout with sidebar, multi-column grids

**Mobile Optimizations:**
- Collapsible filters in accordion
- Card-based data display instead of tables
- Touch-friendly button sizes (min h-12)
- Reduced padding for space efficiency
- Bottom sheet for actions

## Data Visualization

**Chart Guidelines:**
- Use Chart.js library
- Omset charts: Line chart with gradient fill
- Product breakdown: Doughnut or bar chart
- Trend indicators: Sparklines in metric cards
- Consistent spacing around charts: p-6

## Accessibility & Usability

**Focus States:**
- Clear outline on keyboard focus
- Skip navigation for keyboard users
- Form fields accessible with proper labels

**Loading States:**
- Skeleton screens for tables
- Spinner for actions
- Progress indicators for multi-step forms

**Empty States:**
- Centered message with icon
- Call-to-action button
- Helpful guidance text

## Images

**No hero images needed** - This is a business application focused on functionality.

**Icon Usage:**
- Material Icons (via CDN) for all UI icons
- Consistent sizing: 20px for buttons, 24px for navigation
- Product placeholder icons where needed

This design creates a professional, efficient POS system optimized for daily business operations with clear role-based workflows.