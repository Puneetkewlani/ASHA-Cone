# ASHA-Cone

# Design Guidelines: Mobile EHR Companion for ASHA Workers

## Design Approach

**Selected System:** Material Design
**Justification:** Material Design excels at mobile-first interfaces with strong visual hierarchy, accessibility features, and clear interaction patterns - essential for healthcare workers in field conditions requiring quick data entry and high readability.

**Key Principles:**
1. Touch-first interaction with generous tap targets
2. Clear visual hierarchy for scanning patient data
3. Minimal cognitive load - essential healthcare info prioritized
4. Robust offline state indicators
5. Consistent patterns for predictable navigation

---

## Typography System

**Font Family:** Roboto (via Google Fonts CDN)
- Primary: Roboto (400, 500, 700)
- Fallback: system-ui, -apple-system, sans-serif

**Type Scale:**
- Page Titles: text-2xl (24px), font-bold
- Section Headers: text-xl (20px), font-semibold
- Card Titles/Labels: text-base (16px), font-medium
- Body Text/Input Fields: text-base (16px), font-normal
- Helper Text/Metadata: text-sm (14px), font-normal
- Buttons: text-base (16px), font-medium, uppercase tracking-wide

**Readability Standards:**
- Minimum line height: leading-relaxed (1.625)
- Form labels: leading-tight for compactness
- Body content: leading-normal

---

## Layout System

**Spacing Primitives:** Use Tailwind units of **2, 4, 6, 8, 12, 16**
- Component padding: p-4, p-6
- Section spacing: space-y-6, space-y-8
- Form field gaps: gap-4
- Card spacing: p-6
- Button padding: px-6 py-3

**Container Strategy:**
- Mobile-first: Full width with px-4 gutters
- Max-width: max-w-7xl for tablet/desktop breakpoints
- Card containers: rounded-lg with shadow-md
- Form containers: max-w-2xl mx-auto for optimal data entry

**Grid Patterns:**
- Patient lists: Single column stack on mobile
- Dashboard metrics: grid-cols-2 on mobile, grid-cols-4 on tablet+
- Form layouts: Single column for mobile, grid-cols-2 for tablet+ where appropriate

---

## Component Library

### Navigation
**Bottom Navigation Bar** (Mobile Primary)
- Fixed bottom navigation with 4-5 primary actions
- Icon + label combination
- Active state with elevated indicator
- Height: h-16 with safe-area-inset-bottom

**Top App Bar**
- Height: h-14
- Left: Back/Menu icon
- Center: Page title (text-lg font-semibold)
- Right: Action icons (sync status, language switcher, profile)
- Elevation: shadow-sm

### Dashboard Components
**Metric Cards**
- Elevated cards (shadow-md, rounded-lg)
- Large number display (text-4xl font-bold)
- Small label below (text-sm)
- Icon positioned top-right
- Padding: p-6
- Minimum tap target: min-h-24

**Patient List Items**
- Card-based list with shadow-sm
- Left: Patient avatar or initials in circle (w-12 h-12)
- Center: Name (text-base font-semibold), ID/Age (text-sm)
- Right: Status badge + chevron
- Padding: p-4
- Gap between items: space-y-2

**Status Badges**
- Rounded-full px-3 py-1
- text-xs font-medium
- Categories: Pending, Synced, Overdue, Completed

### Forms & Input Fields

**Text Inputs**
- Height: h-12 for optimal touch
- Padding: px-4
- Border: border-2 with focus ring
- Rounded: rounded-md
- Label above field: text-sm font-medium mb-2
- Helper text below: text-xs
- Error states with icon and message

**Voice Input Button**
- Floating action button style when active
- Positioned as suffix icon in input fields
- Icon: Microphone (Material Icons)
- Size: w-10 h-10 rounded-full

**Select Dropdowns**
- Same height as text inputs (h-12)
- Chevron-down icon suffix
- Custom styling for mobile picker

**Radio/Checkbox Groups**
- Large tap targets: min-h-12 per option
- Clear visual spacing: space-y-3
- Label positioned right with adequate padding-left

**Date Pickers**
- Calendar icon prefix
- Native mobile picker integration
- Height: h-12

### Buttons

**Primary Action Button**
- Height: h-12
- Padding: px-6
- Rounded: rounded-md
- Full width on mobile: w-full
- Icon + text combination where needed
- Disabled state clearly differentiated

**Secondary Button**
- Outlined variant with border-2
- Same dimensions as primary

**Icon Buttons**
- Size: w-10 h-10 or w-12 h-12
- Rounded: rounded-full
- Ripple effect area

**Floating Action Button (FAB)**
- Size: w-14 h-14
- Rounded: rounded-full
- Elevation: shadow-lg
- Fixed positioning: bottom-20 right-4 (above bottom nav)
- Primary use: Quick patient add

### Data Display

**Info Sections**
- Header with icon + title
- Divider line
- Key-value pairs in grid or stack
- Padding: p-4
- Background elevation for grouping

**Timeline/History View**
- Vertical timeline with connecting line
- Date markers on left
- Event cards on right
- Icon indicators for event types
- Padding between events: space-y-4

**Vital Signs Display**
- Grid layout: grid-cols-2 gap-4
- Each vital: Icon, value (large), unit (small)
- Visual indicators for abnormal ranges

### Modals & Overlays

**Bottom Sheets** (Primary modal pattern)
- Slide up from bottom
- Rounded top corners: rounded-t-2xl
- Handle indicator at top
- Max height: max-h-[90vh]
- Backdrop with opacity

**Dialogs**
- Centered modal for critical actions
- Max-width: max-w-sm
- Padding: p-6
- Actions at bottom

### Reminder/Notification Cards
- Elevated cards with left accent border (border-l-4)
- Icon on left
- Title + description stacked
- Due date/time prominent
- Action button inline
- Dismissible with swipe gesture indicator

### Sync Status Indicator
**Top Bar Indicator**
- Small badge next to app bar title
- States: Syncing (animated), Synced, Pending (count), Offline
- Icon + text or icon only
- Tappable to show sync details

**Full Status Panel**
- List of pending records
- Last sync timestamp
- Manual sync trigger button
- Upload/download progress

### Language Switcher
- Dropdown or bottom sheet
- Flag icons + language names
- Current language highlighted
- Positioned in app bar or settings

---

## Accessibility Standards

**Touch Targets:**
- Minimum: 44x44px (h-11 w-11)
- Preferred: 48x48px (h-12 w-12)
- List items: min-h-16

**Form Accessibility:**
- All inputs have visible labels
- Error messages use icons + text
- Required fields marked clearly
- Field hints positioned consistently

**Contrast Requirements:**
- Text meets WCAG AA standards
- Focus indicators clearly visible
- Error states use both color and icons

**Voice Support Integration:**
- Microphone icon consistently positioned
- Visual feedback during recording
- Transcription preview before submission

---

## Layout Patterns

### Dashboard Screen
- Top App Bar with sync status
- Metrics grid (2 columns mobile, 4 desktop)
- Quick actions section with large buttons
- Recent patients list (3-5 visible)
- Bottom Navigation

### Patient List Screen
- Search bar at top
- Filter chips below search
- Scrollable card list
- FAB for new patient
- Pull-to-refresh capability

### Patient Detail Screen
- Top: Patient header card with photo, name, demographics
- Tabs: Overview, Visits, Vaccinations, ANC
- Content sections with clear headers
- Edit FAB when applicable

### Data Entry Forms
- Progress indicator if multi-step
- Section headers with icons
- Grouped related fields
- Validation inline
- Sticky bottom action bar with Save/Cancel

### Offline State Screens
- Clear messaging with illustration concept
- Pending actions count
- Local data access still available
- Sync button prominent

---

## Animation Guidelines

**Minimal Use - Performance Priority**
- Page transitions: Simple fade or slide (200ms)
- List item entry: Subtle fade-in on load
- Sync indicator: Rotating icon during active sync
- Bottom sheet: Slide up with spring (300ms)
- No decorative animations
- Focus on functional feedback only

---

## Images

**No hero images required** - This is a utility application focused on data entry and efficiency.

**Functional Images Only:**
- Patient avatar placeholders (circular, initials-based)
- Offline/empty state illustrations (simple, medical-themed line art)
- Icon library: Material Icons via CDN

---

## Mobile-Specific Considerations

**Safe Areas:**
- Account for notches: pb-safe, pt-safe
- Bottom nav above system gestures
- Full-bleed content with proper padding

**Orientation:**
- Portrait-primary locked for consistency
- Form optimized for single-hand use where possible

**Performance:**
- Lazy load patient lists
- Virtual scrolling for large datasets
- Optimistic UI updates for offline actions
