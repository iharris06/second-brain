Let me build this out properly. I want to make something you can literally paste into Hyperagent and have running in minutes.This is a two-part deliverable — the agent system prompt you paste into Hyperagent, plus a reference card for the output format it produces. Let me build both.Here's how to use this in practice — four tabs covering everything you need:

The "Agent system prompt" tab is what goes into Hyperagent's Instructions field when you create the agent. It's doing real work: it tells the agent exactly what to look for on Google Business Profiles and websites, how to score the gaps it finds, and critically — how Ian Harris writes, so the emails don't come out sounding like a SaaS marketing blast.

The "Task prompt" tab has three variants. The prospect-finding prompt is the one to run first if you don't already have a list — it'll search Google Maps for East Valley HVAC/plumbing businesses and filter them down to the ones worth researching, before you spend credits on deep dives. Then use single or batch mode for the actual research runs.

One thing worth noting on the email guardrails in the system prompt: the agent is instructed to never force a pitch on a business that's already well-automated, and to never fabricate review content. Both of those protect your reputation. The output format gives you the gap score up front so you can quickly triage — if something comes back 3/10, skip it without reading the email.

The realistic workflow is: run the prospect finder once (~$3–5), get back a list of 15 candidates, pick the 8 that show strong signals, run deep research on those ($40–60 total), personally edit and send the emails that come back. That's a full outreach batch for about $65 in credits, with emails that reference specific things about each business.

Want me to also write a follow-up sequence prompt — what the agent should draft if someone opens the email but doesn't reply within a week?