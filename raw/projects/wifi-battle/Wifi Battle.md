### App Overview

WiFi Battle is a dark-themed, AI-powered network performance testing tool. Users configure two WiFi networks, select home locations, run speed tests at each location, and get an AI-generated winner analysis. The app is a single-page React app with a linear workflow: **Setup → Test → Results**.

---

### Design Direction

Replace the current purple/blue gradient-heavy aesthetic with a clean, high-contrast dark interface. Think **terminal meets dashboard** — precise, data-forward, minimal decoration. Inspired by tools like Linear, Vercel, or Raycast. Dark background, sharp typography, subtle borders, and color used only for data meaning (not decoration).

**Palette:**

- Background: near-black (
    
    ```plaintext
    #0a0a0a
    ```
    
     / 
    
    ```plaintext
    #111
    ```
    
    )
    
- Surface: 
    
    ```plaintext
    #1a1a1a
    ```
    
    , 
    
    ```plaintext
    #222
    ```
    
- Border: 
    
    ```plaintext
    #2a2a2a
    ```
    
    , 
    
    ```plaintext
    #333
    ```
    
- Text primary: 
    
    ```plaintext
    #f0f0f0
    ```
    
- Text secondary: 
    
    ```plaintext
    #888
    ```
    
- Accent: single color — electric green 
    
    ```plaintext
    #00ff88
    ```
    
     or amber 
    
    ```plaintext
    #f59e0b
    ```
    
     (pick one, use sparingly)
    
- Status colors: green = good, amber = warning, red = poor (for metrics only)
    
- No gradients except subtle ones on the primary CTA button
    

**Typography:** Monospace for all metric values (download/upload/ping/jitter numbers). Sans-serif for labels and body. Large, bold numbers for metrics — they are the hero content.

---

### Layout Structure

**1. Header (fixed, top)**

- Left: App name "WiFi Battle" in small caps or monospace, with a minimal wifi icon
    
- Right: Live indicator dot (pulsing green) + "Secure" label
    
- Height: compact, ~48px
    
- No gradients — solid dark surface with a 1px bottom border
    

**2. Hero Section (below header, centered)**

- Remove the large "WiFi Battle" h1 — the header already has the name
    
- Keep the three badge pills (AI-Powered, Local Testing, Secure APIs) but make them smaller, inline, text-only with a subtle border
    
- Replace with a single-line subtitle: _"Compare two networks. Find the winner."_
    
- This section should be minimal — it's not a landing page, it's a tool
    

**3. Setup Panel (collapsible, full-width, max ~700px centered)**  
Priority: HIGH — this is step 1 of the workflow

Contains two sub-components stacked vertically:

**3a. NetworkStatus (Network Configuration card)**

- Shows current connection status (connected/disconnected) + ISP name inline at top
    
- Lists up to 2 configured networks as rows, not cards
    
    - Each row: colored dot (active = accent color, inactive = gray) + nickname + expected speeds (DL/UL as small inline tags) + delete button (trash icon, right-aligned, appears on hover)
        
    - Active network has a subtle left border accent, not a full gradient background
        
- "Add Network" is a text button with a 
    
    ```plaintext
    +
    ```
    
     icon, not a full-width button
    
- Add Network form: inline expand below the list, not a separate section. Fields: nickname, expected DL, expected UL — in a compact 3-column row
    
- Status messages ("Ready for battle!", "Add one more network") appear as small inline text below the list, not centered banners
    

**3b. LocationSelector (Battle Locations card)**

- Header: "Locations" with a count badge showing selected count
    
- Default locations and custom locations in a single flat list (remove the "Default" / "Custom" section headers — they add noise)
    
- Each location: checkbox-style toggle row. Selected = accent-colored checkbox + slightly highlighted row background. Unselected = gray checkbox + normal row
    
- No scale transforms on hover — just background color change
    
- "Add Custom Location" is a small text link at the bottom of the list, not a full button
    
- Selected locations summary: a compact horizontal chip list below the location list, each chip has an 
    
    ```plaintext
    ×
    ```
    
     to deselect
    

**4. Testing Controls (primary CTA area)**  
Priority: HIGHEST — this is the main action

**4a. SpeedTestButton**

- Full-width, tall button (~64px) — this is the most important element on the page
    
- States:
    
    - Ready: solid accent-colored background, "Start Battle ⚔" with sword icon
        
    - Disabled: muted gray, shows what's missing ("Configure 2 Networks" / "Select Locations")
        
    - Running: dark background with animated border or progress bar along the bottom edge, shows "Battle Running... 42%"
        
    - Stopped: red-tinted, "Stop"
        
- No gradient overlays or shimmer effects — the button state communicates through color and text only
    

**4b. BattleLocationTest (appears only when battle is running)**

- Shown inline below the Start Battle button, not in a separate card
    
- Progress bar: thin (4px), full-width, accent color fill
    
- Location list: compact rows showing location name + status icon (pending = gray dot, testing = spinning indicator, done = green checkmark)
    
- "Start [Location] Test" button per row: small, right-aligned, secondary style
    
- "All locations tested" state: green banner with "Generate AI Analysis" button — this button should be prominent (primary style)
    

**5. Results & Analysis (right column on desktop, below on mobile)**  
Priority: HIGH — this is the payoff

**5a. TestResults**

- Empty state: minimal — just an icon and "Run a test to see results"
    
- Current metrics: 4 metric tiles in a 2×2 grid
    
    - Each tile: metric name (small, secondary color) + large monospace number + unit
        
    - Color-coded by performance: green/amber/red based on thresholds
        
    - No colored backgrounds — just the number color changes
        
- Test history: compact table-style list, not cards. Columns: location, network, DL, UL, timestamp. Max 10 rows, scrollable
    

**5b. WiFiBattleAnalysis**

- Loading state: single line "Analyzing battle results..." with a spinner — no full card
    
- Result: prominent card with:
    
    - Winner name in large text with a trophy icon
        
    - AI analysis text in readable body size
        
    - Two stat tiles at bottom: "Champion" (winner name) + "Analysis Method" (AI-Powered)
        
- The winner announcement should feel like a reveal — high contrast, clear hierarchy
    

**5c. ClearHistoryButton**

- Only visible when there's history
    
- Small, destructive-style text button ("Clear History") at the very bottom of the results section
    
- Confirmation modal: minimal dark modal, centered, with item counts and Cancel/Confirm buttons
    

---

### Responsive Behavior

- Desktop (≥1024px): Setup panel full-width centered, then Testing Controls + Results in a 2-column grid below
    
- Mobile: single column, stacked in workflow order: Setup → Test Controls → Results
    

---

### Interaction Patterns

- Setup panel auto-collapses (opacity + height) when a battle starts — keep this behavior
    
- Collapse toggle button uses a chevron icon, not Shield icon
    
- Error banner: stays at top, rose/red background, dismissible with 
    
    ```plaintext
    ×
    ```
    
- No page-level animations except the setup collapse transition and the analysis fade-in
    

---

### What to Remove

- The large hero h1 "WiFi Battle" (redundant with header)
    
- All 
    
    ```plaintext
    blur-3xl
    ```
    
     decorative background orbs
    
- The grid pattern SVG overlay
    
- Gradient text on section headings — use plain white/light gray
    
- ```plaintext
    hover:scale-[1.02]
    ```
    
     transforms on location rows and network rows
    
- The "Testing Controls" and "Results & Analysis" section headings — the components are self-explanatory
    
- ```plaintext
    card-premium
    ```
    
     distinction — use one card style
    

---

### Component Priority Order (top to bottom on page)

1. Header
    
2. Subtitle / badges
    
3. Network Configuration (NetworkStatus + LocationSelector)
    
4. Start Battle button (SpeedTestButton)
    
5. Battle progress (BattleLocationTest) — conditional
    
6. Test Results (TestResults)
    
7. AI Analysis (WiFiBattleAnalysis)
    
8. Insights (if surfaced)
    
9. Clear History