---
type: topic
updated: 2026-11-12
---
# AI Audit Process

How MIRK runs an audit end to end: intake, discovery call, AI synthesis, deliverable, walkthrough. The positioning is a platform-agnostic "AI solutions architect" who recommends the best tools, not only ones MIRK builds ([[Ai Audit Call flow]]).

## 1. Intake survey (GHL)
- Multi-step GHL Survey: multiple-choice plus context boxes so the AI can categorize answers ([[AI Audit Survey Flow]]). There is also an industry-neutral version ([[AI Audit Survey Flow  Generic]]).
- GHL field → prompt variable mapping: [[Survey response map]]. Test data: [[Survey Sample responses]] (used to test the Make.com → JSON → HTML-to-PDF pipeline).
- Blank HTML assessment template: [[AI Template]], ![[AI Tools Assessment Template.html]].

## 2. Discovery call (20–30 min)
- Script: [[Deep Dive Call Script]]. Question bank: [[Questions list for assessment]].
- Operations-mapping method: where leads arrive, who sees them first, response speed, what info is missing ([[Audit Key point]]).
- Team version: 1:1 interviews with dept heads plus an employee survey ([[$3000 package]]).

## 3. Synthesis
- "Ghost Architect" pipeline: GHL call recording → Call Ended workflow (>15 min) → webhook to Make.com → Claude API with web search → PDF proposal ([[Ai Audit Call flow]]).
- Team audits: one NotebookLM notebook per client, one source per employee; use briefing docs and audio overview as the upsell ([[$3000 notebookllm]]).

## 4. Deliverable: Business X-Ray
- Self-contained dark-mode HTML file driven by an `AUDIT_DATA` JS object; no backend ([[Xray prompt]]). Example output: ![[Business Xray Revenue Wins.html]] ([[Xray - html base]]).
- PDF variant: "System Architecture Blueprint" test output from the Make.com pipeline ![[MIRK_Audit_Doo Doo.pdf]].
- Revenue calculator embed: [[Revenue calculator script]].
- Personalize with the prospect's real review gaps, estimated missed calls and $ lost per month ([[7 Day Plan]]).

## 5. Walkthrough
- 15–20 min: quantify the leak (missed calls × avg job value), then pitch the plan ([[7 Day Plan]]). See [[mirk-offers-and-pricing]].

## Worked example
- Dance studio audit playbook, with phased questions, admin checklist, software picks and scheduling-algorithm data fields ([[Melanie Dance Studio]]).

## Reference material
- Whitepaper on aligning people, process and tech for production AI: ![[The Agentic Operating Model.pdf]].
- Example "AI bot team" roster for a business owner (chief-of-staff bot routing to content, video and research bots), a model for agent offers: ![[advisory_bot-roster_v1.pdf]].
- [[AI Concierge playbook]] (Notion link).

## Other audit types
- Google Maps / GBP ranking audit: 5×5 grid scan, relevance/distance/prominence, monthly rescans, don't serve same-industry competitors within 20 miles ([[Google Maps Audit]]).
