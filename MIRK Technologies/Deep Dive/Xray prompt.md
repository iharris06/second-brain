# MIRK Technologies — Business X-Ray: Codex Build Prompt

## Interactive AI Audit Deliverable ($1,000 tier)

---

## YOUR MISSION

Build a single self-contained HTML file called `business-xray.html` that serves as a premium interactive audit deliverable for MIRK Technologies' $1,000 Deep Dive service.

The file reads all business data from a JavaScript object called `AUDIT_DATA` at the top of the file. When MIRK delivers an audit, they replace that object with real client data and send the file. No backend, no server, no dependencies that require a CDN to be online — everything must work when the file is opened locally in a browser.

**The only exception:** You may load fonts from Google Fonts via a `<link>` tag, and you may use vanilla JavaScript. No frameworks, no npm, no build step.

---

## VISUAL IDENTITY

This is a premium, dark-mode, cinematic interface. Think mission control meets financial terminal. The aesthetic is:

- **Background:** True black `#000000` with very subtle dark panels (`#0a0a0a`, `#0d0d0d`)
- **Primary accent:** Electric green `#00ff88` — used for healthy/flowing states, positive numbers, recovered revenue
- **Warning accent:** Amber/gold `#f5a623` — used for nodes at risk, degrading states
- **Danger accent:** Hot red `#ff3b3b` — used for leaking nodes, money being lost, critical blockers
- **Text:** `#ffffff` primary, `#8a8a8a` secondary, `#444` for dividers
- **Font:** `Space Grotesk` (display/headers) + `JetBrains Mono` (numbers/data) from Google Fonts
- **Node size:** Circular nodes, ~70px diameter, with a dark inner circle and colored outer ring
- **Moving particles:** Dots travel along the connecting paths between nodes. Green = healthy flow, amber = at risk, red = leaking/blocked
- **Pulsing:** Leaking/critical nodes pulse their danger color with a CSS keyframe glow effect

The overall feel: you're watching this business's operations in real time. The money is literally bleeding out.

---

## DATA STRUCTURE

At the very top of the file, before any other code, define:

```javascript
const AUDIT_DATA = {
  meta: {
    businessName: "Crown Clean",
    industry: "Commercial Cleaning",
    location: "Charlotte, NC",
    annualRevenue: "$1.2M/yr",
    employeeCount: 22,
    auditDate: "June 2026",
    analystName: "Ian Harris"
  },

  // Summary financials (shown in top bar and executive summary)
  financials: {
    totalAnnualLeak: 116481,       // dollars/year being lost NOW
    monthlyBleed: 9700,            // dollars/month being lost NOW
    recoveredWithAI: 98900,        // dollars/year recovered after MIRK deployment
    residualLeakWithAI: 17500,     // dollars/year still leaking after AI (irreducible)
    totalTimeWastedHrsPerWeek: 19.6  // hours/week lost across all leaking nodes
  },

  // Each stage in the business workflow
  nodes: [
    {
      id: "lead-intake",
      label: "Lead Intake",
      status: "nominal",          // "nominal" | "at-risk" | "leaking"
      hoursWastedPerWeek: 0,
      monthlyBleed: 0,
      description: "Leads come in via phone and web form. Response handled manually.",
      aiFixAvailable: false,
      aiSystem: null
    },
    {
      id: "quoting",
      label: "Quoting",
      status: "leaking",
      hoursWastedPerWeek: 11,
      monthlyBleed: 2400,
      description: "Every quote requires a site visit, manual measurement, and a spreadsheet template only Dana knows how to drive. Quotes take 2–4 days to go out. 31% of bids die waiting. Owner spends 11 hrs/week building quotes himself.",
      aiFixAvailable: true,
      aiSystem: {
        name: "AI Quote Generator",
        description: "Crew lead snaps site photos on a phone → AI measures square footage, detects floor types and surface conditions, prices from your rate card, and emails a branded quote in under 10 minutes. Owner just hits approve.",
        buildCost: 3500,
        projectedRecovery: 28800,
        timeAfterAI: "45 min/wk",
        roiWeeks: 6
      }
    },
    {
      id: "scheduling",
      label: "Scheduling",
      status: "nominal",
      hoursWastedPerWeek: 0,
      monthlyBleed: 0,
      description: "Dispatching handled via group text and a shared Google Calendar. Works at current scale.",
      aiFixAvailable: false,
      aiSystem: null
    },
    {
      id: "crew-dispatch",
      label: "Crew Dispatch",
      status: "nominal",
      hoursWastedPerWeek: 0,
      monthlyBleed: 0,
      description: "Crews are dispatched morning of. Route optimization is manual but functional.",
      aiFixAvailable: false,
      aiSystem: null
    },
    {
      id: "job-completion",
      label: "Job Completion",
      status: "nominal",
      hoursWastedPerWeek: 0,
      monthlyBleed: 0,
      description: "Job sign-off via paper checklist. Photos taken inconsistently.",
      aiFixAvailable: false,
      aiSystem: null
    },
    {
      id: "invoicing",
      label: "Invoicing",
      status: "leaking",
      hoursWastedPerWeek: 8,
      monthlyBleed: 3100,
      description: "Invoices go out 3–7 days after job completion. 6 accounts are 30+ days overdue. No automated follow-up sequence. DSO is 41 days.",
      aiFixAvailable: true,
      aiSystem: {
        name: "Auto-Invoice + Collections Sequence",
        description: "Invoice fires within 1 hour of job completion. Automated SMS/email follow-up at day 7, 14, and 21. Escalation alert to owner at 30 days. DSO drops to under 12 days.",
        buildCost: 1800,
        projectedRecovery: 37200,
        timeAfterAI: "30 min/wk",
        roiWeeks: 3
      }
    },
    {
      id: "customer-follow-up",
      label: "Customer Follow-Up",
      status: "leaking",
      hoursWastedPerWeek: 0.6,
      monthlyBleed: 4200,
      description: "No structured reactivation or upsell sequence. Repeat business is entirely owner-relationship driven. Estimated $4,200/mo in missed reactivations and add-on services.",
      aiFixAvailable: true,
      aiSystem: {
        name: "Reactivation + Review Engine",
        description: "Automated 30/60/90-day follow-up sequences. Review request fires 48 hours after job close. Upsell offers triggered by service history. Owner approves messaging templates once.",
        buildCost: 1200,
        projectedRecovery: 32900,
        timeAfterAI: "15 min/wk",
        roiWeeks: 2
      }
    },
    {
      id: "collections",
      label: "Collections",
      status: "nominal",
      hoursWastedPerWeek: 0,
      monthlyBleed: 0,
      description: "Handled manually by owner when escalated. No formal process.",
      aiFixAvailable: false,
      aiSystem: null
    }
  ],

  // Connections between nodes — defines the workflow graph
  // "from" → "to" in workflow order
  connections: [
    { from: "lead-intake", to: "quoting" },
    { from: "quoting", to: "scheduling" },
    { from: "scheduling", to: "crew-dispatch" },
    { from: "crew-dispatch", to: "job-completion" },
    { from: "job-completion", to: "invoicing" },
    { from: "invoicing", to: "collections" },
    { from: "quoting", to: "customer-follow-up" },
    { from: "job-completion", to: "customer-follow-up" }
  ],

  // Executive summary page — recommendations in priority order
  recommendations: [
    {
      priority: 1,
      title: "Deploy auto-invoicing and collections sequence",
      urgency: "Critical",
      timeframe: "Week 1–2",
      investment: 1800,
      annualReturn: 37200,
      roiWeeks: 3,
      description: "Invoices leaving 3–7 days late with no automated follow-up is your largest single leak. 6 accounts 30+ days overdue represents ~$18,400 in locked receivables right now.",
      type: "quick-win"
    },
    {
      priority: 2,
      title: "Build AI quote generator",
      urgency: "High",
      timeframe: "Week 2–4",
      investment: 3500,
      annualReturn: 28800,
      roiWeeks: 6,
      description: "Owner spending 11 hrs/week on quotes is the most expensive use of his time. 31% bid death rate from slow turnaround is a direct revenue loss that compounds every month.",
      type: "quick-win"
    },
    {
      priority: 3,
      title: "Launch reactivation and review engine",
      urgency: "High",
      timeframe: "Week 3–5",
      investment: 1200,
      annualReturn: 32900,
      roiWeeks: 2,
      description: "No structured follow-up means repeat business is entirely relationship-dependent. This is the highest-ROI fix in the stack — $32,900/yr recovered for $1,200 build cost.",
      type: "quick-win"
    },
    {
      priority: 4,
      title: "Automate crew dispatch and route optimization",
      urgency: "Medium",
      timeframe: "Month 2–3",
      investment: 2200,
      annualReturn: 14400,
      roiWeeks: 8,
      description: "Current group-text dispatch works but doesn't scale past ~30 employees. Route optimization alone recovers 1–2 hours of drive time per crew per day.",
      type: "long-term"
    },
    {
      priority: 5,
      title: "Job completion documentation system",
      urgency: "Low",
      timeframe: "Month 3–4",
      investment: 900,
      annualReturn: 8700,
      roiWeeks: 6,
      description: "Paper checklists and inconsistent photos create liability exposure and make quality disputes hard to resolve. Structured digital sign-off with auto-photo upload closes this gap.",
      type: "long-term"
    }
  ]
};
```

---

## PAGE 1: THE X-RAY (Business Operations Map)

### Layout

```
┌─────────────────────────────────────────────────────────────────┐
│ HEADER BAR                                                      │
│  [BUSINESS X-RAY logo]  [Business name + meta]  [LEAK COUNTER] │
│                                           [AI TOGGLE]          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                    WORKFLOW CANVAS                              │
│          (full width, ~70vh, dark background)                   │
│                                                                 │
│   Nodes arranged in a W or zigzag pattern                       │
│   Connected by animated particle paths                          │
│   Leaking nodes pulse red, nominal are orange-ringed            │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│ BOTTOM STATUS BAR                                               │
│  [legend: JOBS • REVENUE • LEAK]  [scan info]  [mode badge]     │
└─────────────────────────────────────────────────────────────────┘
```

### Header Bar

Left side:

- Small eyebrow: `AI OPERATIONS AUDIT · LIVE`
- Logo text: `BUSINESS X-RAY` in Space Grotesk bold, white
- Below: `[businessName] · [industry] · [location] · [annualRevenue] · [employeeCount] EMPLOYEES`

Center:

- A bordered box containing:
    - Label: `◆ TOTAL ANNUAL LEAK ◆` in green/red depending on AI toggle
    - Large number: `$[totalAnnualLeak]/YR` in JetBrains Mono, huge (48px+)
    - Below: `[relevant category labels] · $[monthlyBleed]/MO BLEEDING` (current state) OR `AUTOMATED` (AI state)
- When in AI mode, show: `RECOVERED $[recoveredWithAI]/YEAR` in a green outlined box below the main counter

Right side:

- Toggle switch labeled `CURRENT STATE ●——— WITH AI SYSTEMS`
- Red = current state (left), Green = AI deployed state (right)
- Below: `— FLIP TO SIMULATE AI DEPLOYMENT —`

### The Live Leak Counter behavior

In CURRENT STATE mode:

- The leak counter animates upward slowly in real time — it's counting the money being lost
- Speed: `totalAnnualLeak / (365 * 24 * 3600)` dollars per second, shown as a continuously incrementing number
- This is the emotional gut-punch. The number is literally going up as they watch.
- Format: `$116,481.23/YR` — show cents ticking over

In AI SYSTEMS mode:

- Counter drops to `residualLeakWithAI` and stops climbing fast
- Show the RECOVERED amount prominently
- Nodes turn green (automated), particles turn green, pulsing stops

### Workflow Canvas

**Node placement:** Arrange nodes in an organic W/zigzag layout — NOT a straight left-to-right line. Reference the screenshot positions:

- Row 1 (left): Lead Intake (lower left)
- Row 1 (middle-high): Quoting (mid left, lower than Lead Intake)
- Row 2 (center-top): Scheduling (center, high)
- Row 2 (center): Crew Dispatch (center, lower)
- Row 3 (center): Customer Follow-Up (center-bottom)
- Row 3 (right-high): Job Completion (right, high)
- Row 4 (right): Invoicing (right, mid)
- Row 4 (far right): Collections (far right)

Use SVG for the canvas. Position nodes absolutely by percentage or fixed coordinates within the SVG viewBox. Make the SVG responsive.

**Node design (each node):**

```
        ┌── outer glow ring (color = status)
       ╱
 ┌────╱────┐
 │  ╱ ◉   │  ← dark inner circle with status dot
 │         │  ← colored outer ring (70px diameter)
 └─────────┘
   [LABEL]
   [status text]  ← "NOMINAL" or "-11 HRS/WK · -$2,400/MO" in red
```

Status colors:

- `nominal`: orange outer ring (`#f5a623`), no glow, no pulse — just sitting there
- `at-risk`: amber pulse animation
- `leaking`: red outer ring (`#ff3b3b`), red glow pulse animation, `⚠ LEAKING` badge above node

When hovering a leaking node: show tooltip `"△ VIEW AI FIX — [LABEL]"` (exact style from screenshots)

When clicking a leaking node with `aiFixAvailable: true`: slide in a panel from the right (see Panel spec below)

**Animated particle paths:**

Use SVG `<path>` elements for connections. Animate small dots traveling along each path using `stroke-dasharray` and `stroke-dashoffset` animation or a custom JS particle system.

- Current state: particles on paths TO a leaking node are amber/gold, paths FROM are red or gold based on severity
- AI state: all paths turn green, particles are green
- Particle speed should feel like data flow — not too fast, not slow. ~3–4 seconds to traverse a full path.
- Multiple particles per path (staggered offsets), so paths look continuously active

Path curvature: use SVG cubic bezier curves (`C` command), not straight lines. The curves should arc gracefully between nodes — it should feel organic, not like a flowchart.

**Clicking a leaking node — AI Fix Panel:**

Slide in from the right (300px wide, full canvas height). Dark panel `#0d0d0d` with a `1px solid #1a1a1a` left border.

Contents:

```
[NODE LABEL] ← title, white, 20px

DIAGNOSIS
[description text, ~3 sentences]

[TIME SPENT box]  [BLEED RATE box]  [AFTER AI box]
 11 HRS/WK         $2,400/MO         45 MIN/WK
 (red)             (red)             (green)

RECOMMENDED AI SYSTEM
┌──────────────────────────────────────┐
│ ◈ [aiSystem.name]                    │  ← amber/gold accent header
│                                      │
│ [aiSystem.description]               │
│                                      │
│ RECOMMENDED BUILD    $3,500 ONE-TIME │
└──────────────────────────────────────┘

PROJECTED IMPACT — Recovers $28,800/yr in won bids +
10 owner-hours a week. ROI in under 6 weeks.
```

### Bottom Status Bar

```
● JOBS  ● REVENUE  ● LEAK     [scan info]    SCAN // 8 PROCESS NODES · 3 CRITICAL
                                              T+00:01:03 · AUDIT MODE
```

The T+ counter increments in real time from when the page loaded (showing how long they've been looking at the audit).

---

## PAGE 2: EXECUTIVE SUMMARY

Accessible via a button/tab in the header: `[ X-RAY VIEW ] [ EXECUTIVE SUMMARY ]`

This page is a clean, document-style layout (still dark mode, same font system). Think a high-end PDF that came alive.

### Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  MIRK Technologies — AI Operations Audit                        │
│  [Business Name] · [Date] · Prepared by [analystName]          │
│                                                                 │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐            │
│  │ Total Leak   │ │ Recoverable  │ │ Time Wasted  │            │
│  │ $116,481/yr  │ │ $98,900/yr   │ │ 19.6 hrs/wk  │            │
│  └──────────────┘ └──────────────┘ └──────────────┘            │
│                                                                 │
│  FINDINGS — WHERE THE MONEY IS GOING                           │
│  [Table: Node | Status | Hrs/Wk | $/Mo | AI Fix Available]     │
│                                                                 │
│  RECOMMENDED ACTION PLAN                                        │
│  [Priority 1] [Priority 2] [Priority 3] ...                    │
│  Each as a card: priority number, urgency badge, title,        │
│  investment, annual return, ROI weeks, description             │
│                                                                 │
│  QUICK WINS vs LONG-TERM PROJECTS tabs                         │
│                                                                 │
│  TOTAL INVESTMENT SUMMARY                                       │
│  Total build cost: $X   Total annual return: $Y   Avg ROI: Z wks│
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│  Prepared by MIRK Technologies · mirktechnologies.com          │
│  Ian Harris, Founder · ian@mirktechnologies.com                │
└─────────────────────────────────────────────────────────────────┘
```

### Findings table

Columns: `PROCESS STAGE | STATUS | TIME LOST | MONTHLY BLEED | AI FIX`

Only show nodes that have `status !== "nominal"` OR still show all but gray out the nominal ones.

Status badges:

- `nominal` → gray `NOMINAL` badge
- `leaking` → red `⚠ LEAKING` badge with the dollar figure in red

### Recommendation cards

Each recommendation card:

```
┌─────────────────────────────────────────────────────┐
│ 01  [URGENCY BADGE: CRITICAL / HIGH / MEDIUM]       │
│     [title]                                         │
│                                                     │
│     [description]                                   │
│                                                     │
│     INVESTMENT   ANNUAL RETURN   ROI                │
│     $1,800       $37,200/yr      3 weeks            │
│                                                     │
│     Timeframe: Week 1–2                             │
└─────────────────────────────────────────────────────┘
```

Quick Wins (type: "quick-win") shown first, clearly separated from Long-Term Projects (type: "long-term").

### Investment summary bar at the bottom of recommendations

```
Total build investment: $8,700    Projected annual recovery: $98,900    Average ROI: 4.5 weeks
```

Calculated from `recommendations` array. Show in a dark highlighted row.

---

## ANIMATIONS AND MICRO-INTERACTIONS

1. **Page load:** nodes fade in sequentially (staggered 150ms each), then paths draw in, then particles start flowing. Total intro sequence ~2 seconds.
    
2. **Leak counter:** Continuously incrementing in real time. The cents column ticks over fast. The dollars column ticks slower. This is the most emotionally powerful element — implement it well.
    
3. **Node pulse:** Leaking nodes use a CSS keyframe:
    

```css
@keyframes leak-pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(255, 59, 59, 0.4); }
  50% { box-shadow: 0 0 0 20px rgba(255, 59, 59, 0); }
}
```

4. **AI toggle transition:** When toggling from Current → AI:
    
    - Leak counter smoothly transitions from red/climbing to green/lower fixed value
    - Nodes animate their ring colors from red → green (leaking nodes "heal")
    - Particle colors transition
    - Show a brief flash/sweep effect across the canvas
    - Duration: 800ms transition
5. **Panel slide-in:** 300ms ease-out from right
    
6. **Hover on nodes:** subtle scale(1.05) + brightness increase on the ring
    
7. **Respect `prefers-reduced-motion`** — disable particle animations and pulsing if set, keep everything else functional
    

---

## TECHNICAL REQUIREMENTS

- Single `.html` file, no external dependencies except Google Fonts
- All SVG elements for the canvas (no Canvas API — SVG is more readable for complex DOM manipulation)
- Responsive: works at 1280px+ (desktop primary), degrades gracefully at tablet
- No frameworks — vanilla JS, vanilla CSS
- The `AUDIT_DATA` object is at the very top, clearly commented: `/* MIRK AUDIT DATA — REPLACE FOR EACH CLIENT */`
- Particles implemented as SVG `<circle>` elements animated along path using `getPointAtLength()` in a `requestAnimationFrame` loop — NOT CSS animations (more control, better performance)
- Page navigation (X-Ray vs Executive Summary) is JavaScript `display` toggle — no routing
- Print styles on Executive Summary page: print-friendly layout, hide nav, remove dark bg, show content clearly

---

## SAMPLE OUTPUT EXPECTATIONS

When populated with the Crown Clean sample data above and opened in Chrome:

- Header shows: `BUSINESS X-RAY · Crown Clean · Commercial Cleaning · Charlotte, NC · $1.2M/yr · 22 Employees`
- Leak counter is running at approximately `$3.69/second` ($116,481 / 31,536,000 seconds per year)
- 3 nodes are red/pulsing: Quoting, Invoicing, Customer Follow-Up
- 5 nodes are nominal/orange
- Particles flow green on healthy paths, amber/red approaching leaking nodes
- Clicking "Invoicing" node opens the AI Fix panel showing invoicing fix details
- Toggle to "With AI Systems" → counter drops to $17,500 residual, counter nearly stops, all nodes go green
- Executive Summary tab shows all 5 recommendations with calculated totals

---

## DELIVERY

Output: a single complete `business-xray.html` file. No placeholders, no TODOs — fully functional with the Crown Clean sample data above. MIRK will swap in new `AUDIT_DATA` for each client.

The file should work when opened directly in Chrome from the local filesystem (no web server required). Test this assumption in your implementation — avoid any patterns that require `http://` context (some APIs like `fetch` won't work on `file://`).

---

_This prompt created by MIRK Technologies for internal use. Do not share externally._