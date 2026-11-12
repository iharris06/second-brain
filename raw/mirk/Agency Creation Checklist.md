# Agency Creation Checklist

This checklist is synthesized from the GHL Agency Setup workshop discussions (April 2026).

## 1. Legal & Business Foundation
- [x] **File LLC in Arizona:** Use Bizee (formerly Incfile) for $0 + state fee.
    - [ ] Pay the **$35 expedited fee** for 3-5 business day turnaround.
    - [ ] Note: Maricopa County handles mandatory newspaper publication automatically.
- [x] **Obtain EIN (Tax ID):** Required for business bank accounts and A2P 10DLC registration.
- [x] **Business Purpose:** Use a broad clause: *"Software consulting, digital automation, and related marketing services."*
- [x] **Address Consistency:** Ensure the LLC address matches your GHL "Company" settings exactly.

## 2. GHL Account Setup (Agency View)
- [x] **Subscription:** Start on the **$297 Unlimited Plan** for the first 30 days.
- [x] **Explore Vertical Snapshots:** Go to **Agency Settings > Snapshot** and import a test sub-account (e.g., "Automotive" or "Home Services") to study the backend.
- [x] **Connect Domain:** Point your agency domain (e.g., `www.youragency.com`) to GHL via CNAME or A-Record in **Settings > Domains**.
- [x] **Toll-Free Number:** Register a Toll-Free number initially for faster A2P verification (2-5 days vs. 2-4 weeks for local).

## 3. Website & Funnel Design (Material Design)
- [x] **Initialize Design System:** Inject Material Design 3 tokens into **Settings > Custom CSS**.
    - [ ] Define primary colors, surfaces, and elevation (shadows).
    - [ ] Style GHL buttons globally with 100px border-radius.
- [x] **Build Agency Site:** Use GHL's Website builder for the multi-page structure.
- [x] **Create Sales Funnel:** Use the Funnel builder for the "Essentials Bundle" landing page.
- [x] **Custom JS:** Add AOS (Animate On Scroll) or ripple effects in the **Footer Tracking Code**.

## 4. A2P 10DLC Compliance & Registration
- [x] **Privacy Policy Page:** Create a live URL (e.g., `/privacy-policy`) with explicit SMS disclosure.
    - *Required text:* "No mobile information will be shared with third parties/affiliates for marketing/promotional purposes."
- [x] **SMS Disclosure on Forms:** Add the mandatory disclaimer to all lead forms: *"By calling or texting, you agree to receive SMS... Reply STOP to opt out."*
- [x] **Submit Registration:** In the GHL **Trust Center**, submit the Brand, Campaign, and Opt-in details.

## 5. Product Development (The "Essentials" Bundle)
- [x] **Configure "Missed Call Text-Back":**
    - [ ] Trigger: Inbound Call = No Answer.
    - [ ] Action: Send SMS ("Hey, saw we missed your call...").
- [x] **Configure "Review Booster":**
    - [ ] Generate Review Link in **Sub-Account Settings > Reputation**.
    - [ ] Create workflow from "Send Review Request" template.
- [x] **Local Test:** Run a test call to your GHL number to verify the text-back fires and the lead appears in the pipeline.

## 6. Launch & Outreach
- [x] **7-Day Sprint Goal:**
    - Day 1: File LLC.
    - Day 2: Connect Domain.
    - Day 3: Privacy/Terms pages live.
    - Day 4: Register Toll-Free number.
    - Day 5: Load Snapshot & apply CSS.
    - Day 6: Verification & Testing.
    - Day 7: **GO LIVE.**
- [ ] **Local Outreach:** Target Mesa/East Valley home service businesses (Plumbers, HVAC, Landscapers).
- [ ] **Land and Expand Strategy:** Start with the "Essentials" ($197-$297/mo) and upsell to AI Agents in Week 4.
