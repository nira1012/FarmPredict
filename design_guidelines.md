# FertilizeIQ Design Guidelines

## Design Approach: Utility-First Dashboard System

**Selected Approach:** Custom Design System optimized for agricultural productivity tools
**Justification:** FertilizeIQ is a data-driven utility application where clarity, learnability, and efficiency are paramount. Farmers need quick data entry and clear visualization of results without visual distractions.

**Key Design Principles:**
- Data clarity over decorative elements
- Form efficiency for quick field use
- High contrast for outdoor/bright light readability
- Trust through professional, scientific presentation

---

## Core Design Elements

### A. Color Palette

**Light Mode (Primary):**
- Primary Green: 142 65% 45% (agricultural, growth, trust)
- Secondary Earth: 30 25% 35% (soil, stability)
- Success: 120 60% 50% (positive predictions)
- Warning: 45 95% 55% (attention needed)
- Background: 0 0% 98%
- Surface Cards: 0 0% 100%
- Text Primary: 0 0% 15%
- Text Secondary: 0 0% 45%

**Dark Mode:**
- Primary Green: 142 50% 55%
- Secondary Earth: 30 20% 50%
- Background: 0 0% 10%
- Surface Cards: 0 0% 15%
- Text Primary: 0 0% 95%
- Text Secondary: 0 0% 70%

### B. Typography

**Font Families:**
- Primary: Inter (via Google Fonts) - exceptional readability for data
- Monospace: JetBrains Mono (for numerical values and measurements)

**Hierarchy:**
- Hero/Page Title: 32px/2rem, font-bold (mobile: 24px/1.5rem)
- Section Headings: 24px/1.5rem, font-semibold
- Card Titles: 18px/1.125rem, font-medium
- Body Text: 16px/1rem, font-normal
- Input Labels: 14px/0.875rem, font-medium
- Helper Text: 13px/0.8125rem, font-normal
- Chart Labels: 12px/0.75rem, font-medium

### C. Layout System

**Spacing Primitives:** Tailwind units of 2, 4, 6, 8, 12, 16
- Micro spacing (within components): p-2, gap-2
- Component padding: p-4, p-6
- Section spacing: py-8, py-12
- Page margins: px-4 (mobile), px-8 (desktop)
- Large gaps: gap-8, gap-12

**Grid System:**
- Container: max-w-6xl mx-auto
- Form layout: Single column (mobile), 2-column grid (desktop md:grid-cols-2)
- Chart display: Full-width cards with appropriate padding

### D. Component Library

**Navigation/Header:**
- Fixed top bar with FertilizeIQ branding and leaf/plant icon
- Background: Surface color with subtle border-b
- Height: 64px with centered content

**Form Components:**
- Input fields: Rounded corners (rounded-lg), clear borders, focus states with primary color ring
- Labels: Above inputs, medium weight, with optional helper text below
- Dropdowns: Native select styled consistently with text inputs
- Radio buttons: Horizontal layout for prediction type selection with clear visual states
- Number inputs: With unit indicators (%, kg/acre, etc.) inside or adjacent
- All inputs: Dark mode compatible with proper contrast

**Cards:**
- Elevated surface (shadow-md), rounded-xl corners
- Padding: p-6 to p-8
- Clear hierarchy: Title, description, content area
- Chart cards: Extra padding for visual breathing room

**Buttons:**
- Primary (Predict): Solid primary green, white text, rounded-lg, py-3 px-6, font-medium
- Secondary: Outline style with primary border
- Full-width on mobile, auto-width on desktop
- Clear hover/focus states with subtle scale or shadow

**Charts (Chart.js):**
- Bar charts: Primary green bars with subtle grid lines
- Tooltips: Dark background, white text, rounded corners
- Responsive: Maintain aspect ratio, full card width
- Labels: Clear axis labels, units prominently displayed
- Legend: Top-right position for comparison charts

**Data Display:**
- Prediction results: Large numerical values with units
- Comparison metrics: Side-by-side layout showing before/after or different scenarios
- Status indicators: Color-coded badges (green for optimal, yellow for attention)

### E. Layout Structure

**Page Organization:**
1. **Header Section:**
   - FertilizeIQ logo/name with agricultural icon (leaf or plant)
   - Tagline: "Smart Farming Predictions"
   - Clean, minimal design

2. **Input Form Section:**
   - White/dark card with clear title "Enter Farm Data"
   - Form grid: 2 columns on desktop, stacked on mobile
   - Fields grouped logically: Soil Data, Crop Information
   - Radio buttons for prediction type (prominent, easy to spot)
   - Submit button at bottom, full-width on mobile

3. **Results Section:**
   - Initially hidden, revealed after prediction
   - Summary card with large prediction value
   - Chart visualization card below
   - Explanation text describing what the numbers mean
   - Recommendation section with actionable insights

4. **Instructions Panel:**
   - Collapsible "How to Use" section or always-visible sidebar on desktop
   - Step-by-step guidance with icons
   - Tooltips for complex fields

**Responsive Behavior:**
- Mobile-first approach
- Form: Single column, full-width inputs
- Desktop: Form in left column, instructions/tips in right sidebar
- Charts: Full-width on all viewports, scale appropriately

### F. Images

**No Hero Image Required** - This is a productivity tool, not a marketing page

**Supporting Graphics:**
- Small icon illustrations next to input field labels (soil droplet for moisture, NPK symbols for nutrients)
- Success state illustration when prediction is complete (small celebratory graphic)
- Empty state graphic before first prediction (simple line drawing of farm field)

All graphics should be simple, iconic, and support comprehension without distraction.

### G. Animations

**Minimal, Purposeful Only:**
- Form submission: Subtle loading spinner during prediction
- Results reveal: Gentle fade-in for result cards
- Chart animation: Chart.js default animation on data load (keep brief)
- Button states: Simple hover shadow/scale (CSS only)
- NO decorative or scroll-triggered animations

---

## Accessibility & Usability

- High contrast ratios (WCAG AA minimum)
- Large touch targets (min 44px) for mobile field use
- Clear error states with descriptive messages
- Keyboard navigation support
- Screen reader labels for all inputs
- Units clearly displayed with all numerical inputs
- Consistent dark mode implementation across all components including form inputs

**Critical UX Notes:**
- Prediction button should be prominent and clearly actionable
- Results should feel immediate and trustworthy
- All measurements must include units
- Error handling for invalid inputs (negative values, etc.)
- Progressive disclosure: Show advanced options only when needed