# Design Guidelines: مكتب القبلان E-Commerce System

## Design Approach
**Selected Approach:** Design System (Utility-Focused)  
**System:** Material Design with Arabic/RTL adaptations  
**Rationale:** This is a wholesale distribution management tool requiring clarity, efficiency, and ease of use for both customers and sales representatives. The focus is on operational functionality rather than marketing appeal.

## Core Design Principles
1. **RTL-First Design:** All layouts flow right-to-left for Arabic interface
2. **Clarity Over Decoration:** Clean, uncluttered interface for fast transactions
3. **Touch-Friendly:** Large tap targets (min 44x44px) for mobile use
4. **Data Hierarchy:** Clear visual distinction between product info, pricing, and actions

## Color Palette

### Light Mode
- **Primary:** 200 85% 45% (Deep blue for trust/professionalism)
- **Primary Hover:** 200 85% 35%
- **Secondary:** 25 90% 55% (Warm orange for CTAs)
- **Background:** 0 0% 98%
- **Surface:** 0 0% 100%
- **Text Primary:** 220 20% 15%
- **Text Secondary:** 220 15% 45%
- **Border:** 220 15% 85%
- **Success:** 145 65% 45% (order confirmations)
- **Error:** 0 75% 55% (deletions, warnings)
- **Offer Badge:** 350 85% 55% (special pricing highlights)

### Dark Mode
- **Primary:** 200 75% 55%
- **Background:** 220 20% 10%
- **Surface:** 220 18% 14%
- **Text Primary:** 0 0% 95%
- **Border:** 220 15% 25%

## Typography
- **Primary Font:** Cairo (Google Fonts) - Excellent Arabic support
- **Display/Headers:** Bold 700, sizes 2xl to 4xl
- **Body Text:** Regular 400, size base to lg
- **Product Names:** SemiBold 600
- **Prices:** Bold 700 for emphasis
- **Line Height:** 1.6 for Arabic readability

## Layout System

### Spacing Primitives
Use Tailwind units: **2, 3, 4, 6, 8, 12, 16** for consistent rhythm
- Component padding: p-4 or p-6
- Section spacing: gap-4 or gap-6
- Card margins: m-3 or m-4
- Container max-width: max-w-7xl

### Grid System
- **Category Grid:** grid-cols-2 md:grid-cols-3 lg:grid-cols-4
- **Product List:** Single column stack with horizontal product cards
- **Order Table:** Full-width responsive table with sticky headers
- **Admin Panel:** Two-column layout (actions sidebar + main content)

## Component Library

### Authentication Modal
- Centered dialog with backdrop blur
- Two prominent option cards: "زبون" and "مندوب"
- Input fields: Large, rounded, with clear labels
- Password field for representatives only
- Primary action button at bottom

### Product Categories
- Large card-style buttons with icon + label
- Badge showing product count per category
- Active state with border highlight
- Grid layout: 2 columns mobile, 4 desktop

### Product Cards
- Horizontal layout (RTL): Image right, content left
- Product image: 100x100px rounded, object-cover
- Name: SemiBold, text-lg
- Price display: Large, bold with unit label
- Unit selector: Pill-style toggle (كارتون/نص كارتون/باكيت)
- Quantity controls: -/+ buttons with number input
- "اطلب المنتج" button: Full-width, primary color

### Special Offers Section
- Product cards with TWO price displays:
  - Old price: Strikethrough, muted color, smaller text
  - New price: Bold, large, primary color
- "عرض خاص" badge in top-left corner

### Shopping Cart/Order Summary
- Sticky bottom sheet on mobile
- Sidebar panel on desktop
- Table layout: Product | Qty | Unit | Price | Subtotal | Remove
- Totals section: Prominent, bottom of cart
- Action buttons: "حفظ وإرسال عبر واتساب" (primary), "حفظ PDF" (secondary)

### Admin Menu (Representatives Only)
- Three-dot menu icon (top-right)
- Dropdown panel with icon + label for each action:
  - إضافة منتج
  - حذف منتج
  - تعديل منتج
  - عرض الطلبيات
  - إيقاف/تشغيل الموقع
  - حفظ البيانات
- Danger actions (delete, disable) in red color

### Product Management Forms
- Clean form layout with labeled inputs
- Image upload: Drag-drop area with preview
- Category selector: Dropdown with search
- Price inputs: Number fields with "دينار" suffix
- Unit toggles for carton/packet pricing
- "حفظ" button (primary), "إلغاء" (outline)

### Orders List View
- Card-based list of saved orders
- Each order shows: Date, Total, Items count
- Tap to expand full order details
- Export options: WhatsApp icon, PDF icon
- Search/filter bar at top

### Status Indicators
- Website status toggle: Large switch with "مفعل/موقوف" label
- Order status badges: Colored pills (pending/sent/saved)
- Product availability: Simple "متوفر/غير متوفر" text

## Interactive Elements

### Buttons
- Primary: Solid fill, rounded-lg, py-3 px-6
- Secondary: Outline variant with hover bg
- Icon buttons: Square 44x44px, rounded-md
- Disabled state: 50% opacity, no pointer

### Inputs
- Text/Number: Rounded-lg, border-2, py-3 px-4
- Focus state: Primary color border, subtle shadow
- Error state: Red border with error text below

### Quantity Controls
- Minus/Plus: Circular buttons, border style
- Number display: Center, read-only, bold
- Minimum: 0, disable minus at 0

## Animations
**Minimal approach - only essential feedback:**
- Modal entry/exit: Fade + scale (200ms)
- Cart updates: Number change with brief highlight
- Button press: Scale 0.98 on active
- Loading states: Simple spinner, no elaborate animations

## Navigation
- Top bar: Logo left (RTL), menu right, cart icon
- Breadcrumb: For category navigation
- Back button: Always visible when in product view
- Bottom tab bar (mobile): Categories | Cart | Orders | Profile(admin)

## Responsive Breakpoints
- Mobile: < 768px (single column, bottom sheets)
- Tablet: 768px - 1024px (2-column grids)
- Desktop: > 1024px (sidebar layouts, 4-column grids)

## Images
**Product Images:**
- Aspect ratio: 1:1 (square)
- Resolution: 400x400px minimum
- Format: WebP with JPG fallback
- Placeholder: Branded icon with product category color

**No hero image needed** - This is a functional catalog system, not a marketing site. The interface should load directly into the category selection or product browsing view.

## Accessibility
- Minimum contrast ratio: 4.5:1 for text
- All interactive elements: keyboard accessible
- Arabic screen reader optimization
- Form labels properly associated
- Error messages clear and descriptive