# AI CFO MVP - Design Guidelines

## Design Approach: Modern SaaS Financial Tool

**Selected Approach:** Design System with inspiration from Linear, Stripe Dashboard, and Ramp
**Core Principle:** Professional trust meets modern AI aesthetics - clean, data-forward, intelligent

## Color Palette

**Primary Colors:**
- Brand Primary: 220 90% 56% (Professional blue - trust and finance)
- Brand Dark: 220 85% 45%
- Background Dark: 222 47% 11%
- Surface: 217 33% 17%

**Functional Colors:**
- Success: 142 71% 45% (positive insights, invoice approved)
- Warning: 38 92% 50% (pending actions, review needed)
- Error: 0 84% 60% (issues, overdue invoices)
- Info: 199 89% 48% (AI insights, suggestions)

**Text & Borders:**
- Text Primary: 210 40% 98%
- Text Secondary: 215 20% 65%
- Border Subtle: 217 33% 25%

## Typography

**Font System:**
- Primary: Inter (headings, UI elements, data)
- Monospace: JetBrains Mono (financial figures, invoice numbers)

**Scale:**
- Hero Display: text-5xl font-bold (landing hero)
- Section Headers: text-3xl font-semibold
- Card Headers: text-xl font-semibold
- Body: text-base
- Data Labels: text-sm font-medium
- Financial Figures: text-2xl font-mono font-semibold

## Layout System

**Spacing Primitives:** Use Tailwind units of 2, 4, 6, 8, 12, 16
- Micro spacing: p-2, gap-2
- Component padding: p-4, p-6
- Section spacing: py-12, py-16, py-20
- Large gaps: gap-8, gap-12

**Container Strategy:**
- Landing page: max-w-7xl
- Dashboard: Full width with sidebar (w-64 sidebar, remaining main area)
- Content areas: max-w-6xl for optimal data density

## Landing Page Structure

**Hero Section (80vh):**
- Full-width with subtle gradient background (from background-dark to surface)
- Large hero image showing dashboard preview or AI analyzing invoices
- Centered headline emphasizing AI-powered financial intelligence
- Subheading explaining core value (invoice parsing + insights)
- Primary CTA: "Start Free Trial" + Secondary: "See Demo"
- Trust indicators: "SOC 2 Certified" badge, "Bank-level encryption"

**Problem-Solution Section (2 columns on desktop):**
- Left: Current pain points (manual invoice entry, missed insights, delayed decisions)
- Right: AI CFO solutions with icons (automated parsing, real-time insights, proactive alerts)

**Features Showcase (3-column grid):**
- Invoice Intelligence: OCR parsing with accuracy metrics
- Conversational AI: Natural language problem-solving interface
- Predictive Insights: Cash flow forecasting, spend analysis
Each with icon, title, description, and micro-visual (small screenshot or illustration)

**How It Works (Horizontal timeline, 4 steps):**
- Upload Invoices → AI Parses Data → Ask Questions → Receive Insights
- Connected with subtle lines/arrows
- Each step has icon + brief description

**Trust & Social Proof:**
- Testimonials with company logos (2-column grid)
- Security certifications display
- Integration partners (accounting software logos)

**CTA Section:**
- Dark surface background
- Prominent heading: "Ready to make smarter financial decisions?"
- Primary CTA + Secondary action
- Note: "No credit card required • 14-day free trial"

**Footer (multi-column):**
- Column 1: Product links (Features, Pricing, Security)
- Column 2: Resources (Documentation, API, Blog)
- Column 3: Company (About, Careers, Contact)
- Column 4: Newsletter signup + Social links
- Bottom: Copyright, Privacy Policy, Terms

## Dashboard Application Components

**Navigation:**
- Side navigation (w-64, fixed left)
- Sections: Dashboard, Invoices, Insights, Chat, Settings
- Active state: background accent + border-l-4 in primary color

**Dashboard Layout:**
- Top: KPI cards (4-column grid) - Revenue, Outstanding, Avg Payment Time, AI Recommendations
- Middle: Invoice status chart (bar/line chart with Chart.js or Recharts)
- Bottom: Recent activity feed + Quick actions

**Invoice Parser Interface:**
- Drag-drop upload zone with border-dashed
- Table view of parsed invoices with status badges
- Preview pane showing original + extracted data side-by-side
- Edit capability for AI corrections

**AI Chat Interface:**
- Clean chat layout (max-w-3xl centered)
- User messages: align-right with surface background
- AI responses: align-left with subtle border, includes insights cards
- Input: Fixed bottom with send button, file attachment option

**Data Visualization:**
- Use charts for spend trends, category breakdown, cash flow forecast
- Color-coded by functional colors
- Tooltips with detailed data on hover

## Component Library

**Buttons:**
- Primary: bg-primary, rounded-lg, px-6 py-3
- Secondary: border border-primary, text-primary
- Ghost: hover:bg-surface for sidebar navigation

**Cards:**
- Background: surface color
- Border: border-subtle
- Padding: p-6
- Rounded: rounded-xl
- Shadow: shadow-lg on hover

**Input Fields:**
- Dark mode: bg-surface, border-subtle
- Focus: border-primary ring-2 ring-primary/20
- Labels: text-sm text-secondary above input

**Badges:**
- Status: rounded-full px-3 py-1 text-xs
- Colors based on status (success/warning/error)

**Tables:**
- Header: bg-surface, sticky top-0
- Rows: hover:bg-surface/50
- Borders: border-b border-subtle
- Zebra striping for dense data

## Images

**Landing Page Hero:** Full-width screenshot of the dashboard showing invoice parsing in action with AI insights panel visible - modern, clean interface with subtle glow effects. Place at top of hero section with overlay gradient for text readability.

**Feature Cards:** Small preview images (16:9 aspect) showing specific features - invoice upload interface, chat with AI, insights dashboard. Place within each feature card.

**Social Proof:** Customer company logos in grayscale, color on hover

## Animations

**Minimal & Purposeful:**
- Button hover: subtle scale (scale-105)
- Card hover: shadow elevation only
- Page transitions: fade in only
- NO: Scroll animations, complex entrance effects, parallax

## Accessibility

- Consistent dark mode throughout
- Input fields maintain dark surface backgrounds
- High contrast ratios (WCAG AA minimum)
- Focus indicators visible on all interactive elements
- Semantic HTML structure for screen readers