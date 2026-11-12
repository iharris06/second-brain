## Phase 1: The Questionnaire Engine (The "Invisible Logic")

Build a **Survey** (not a Form) under **Sites > Surveys**. Use a multi-step layout with one or two questions per slide so it feels like a high-end application rather than a chore.

To ensure the AI can parse and categorize the answers flawlessly without getting confused by vague human language, use **multiple-choice dropdowns or radio buttons** paired with open-ended context textboxes.

### The 10 Essential Architecture Questions

#### Category 1: Workflows & Bottlenecks (Filters to Solution A: Automations)

- **Q1: How frequently do you or your team manually move data between different software applications or spreadsheets?**
    
    - _Options:_ Heavily (Multiple times an hour) | Moderately (A few times a day) | Rarely | We don't.
        
- **Q2: What is the single biggest operational bottleneck that slows down your business days?**
    
    - _Options:_ Data entry and admin updates | Invoicing/Chasing clients | Answering repetitive questions | Staffing/Onboarding new hires.
        
- **Q3: Describe a repetitive administrative task that you wish could happen instantly in the background.**
    
    - _Type:_ Open Textbox.
        

#### Category 2: Information Retrieval & Communications (Filters to Solution B: Knowledge Base/Voice)

- **Q4: When a customer sends an inquiry, how long does it typically take for your team to locate the answer and reply?**
    
    - _Options:_ Instantly (under 5 mins) | Within a few hours | By the next day | Things occasionally slip through the cracks.
        
- **Q5: Where does your company’s core operational knowledge live? (e.g., training guides, FAQs, SOPs, past emails)**
    
    - _Options:_ Scattered across multiple files/docs | Documented cleanly in one place | Mostly in the team’s heads | Non-existent.
        
- **Q6: What percentage of incoming customer or team inquiries are asking for the exact same information repeatedly?**
    
    - _Options:_ Over 70% (Very repetitive) | 30% - 70% | Under 30% (Mostly unique requests).
        
- **Q7: What specific documents, PDFs, or standard operating procedures do you find yourself constantly looking up?**
    
    - _Type:_ Open Textbox.
        

#### Category 3: Execution & Task Management (Filters to Solution C: AI Agent Skills)

- **Q8: Are there critical, multi-step processes in your business that rely on a strict compliance or operational checklist?**
    
    - _Options:_ Yes, heavily checklist-dependent | Somewhat structured | No, we wing it every time.
        
- **Q9: If you could duplicate your best employee’s ability to handle one specific operational task, what would that task be?**
    
    - _Options:_ Triaging and sorting incoming leads/emails | Reviewing documents/approving work | Setting appointments and updating the CRM | Analyzing data and generating customer reports.
        
- **Q10: Briefly describe the exact steps a human takes to complete that specific task from start to finish.**
    
    - _Type:_ Open Textbox.
        

## Phase 2: The HighLevel Funnel Blueprint

Set up a 2-page funnel under **Sites > Funnels**.

```
[Page 1: Sales Page] ---> [Stripe Check-out] ---> [Page 2: Survey Page]
```

### Page 1: The Sales & Value Proposition Page

- **Headline:** "Stop Burning Billions of Seconds on Tasks an AI Can Do in Milliseconds."
    
- **Subheadline:** "Get a custom operational AI blueprint mapping your business’s top 3 automation, knowledge base, and digital worker opportunities."
    
- **Two Clear Call-to-Actions (Price Anchoring):**
    
    - **Option A (The Express Audit):** $47. "Submit your business profile and get your custom AI architecture roadmap sent straight to your inbox within 10 minutes."
        
    - **Option B (The Deep-Dive Strategy Session):** $297. "A 30-minute consultation call with a senior systems engineer to map out your implementation architecture + receive the full structured PDF blueprint."
        
- **Product Mapping:** Attach a $47 digital product to this page via the GHL Products tab linked to your Stripe account. Set the redirect URL to **Page 2**.
    

### Page 2: The Assessment Portal

- **Headline:** "Payment Successful. Let's Build Your Blueprint."
    
- **Action:** Embed the Survey built in Phase 1 directly onto this page.
    

## Phase 3: The Automated AI Engine (Backend Workflow)

Go to **Automation > Workflows** and build a fresh automation from scratch. This engine processes the answers instantly, segments the lead, and creates the report body via AI.

```
Trigger: Survey Submitted (Select your AI Audit Survey)
  │
  ▼
Action: AI Agent (Workflow AI Section)
  │
  ▼
Action: Send Email (Deliver custom results)
```

### Step-by-Step Workflow Configuration

#### 1. Add the Trigger

- Select **Survey Submitted**. Add a filter: _Survey is [Your AI Audit Survey Name]_.
    

#### 2. Add the "AI Agent" Action

- Scroll to the **Workflow AI** section and select **AI Agent**.
    
- Set **Output Format** to `Text` and give it a clear description like "AI Audit Report Generation".
    
- Paste the following optimized technical prompt into the **Instructions** block:
    

Plaintext

```
You are a Senior AI Enterprise Consultant and Automation Architect. Your goal is to analyze the survey responses submitted by the contact and generate a precise, hyper-targeted AI Opportunity Report.

Analyze the following custom contact variables containing their answers:
- Volumetric Manual Movements: {{survey.q1_response}}
- Primary Operational Bottleneck: {{survey.q2_response}}
- Target Admin Pain Point: {{survey.q3_response}}
- Response Latency: {{survey.q4_response}}
- Knowledge Base State: {{survey.q5_response}}
- Query Repetitiveness: {{survey.q6_response}}
- Target Documentation: {{survey.q7_response}}
- Checklist Dependency: {{survey.q8_response}}
- High-Value Replicated Task: {{survey.q9_response}}
- Execution Mechanics: {{survey.q10_response}}

Based on this structural data, generate exactly three sections for their report:

1. EXECUTIVE SUMMARY & TARGET BOTTLENECK: Identify their single biggest operational drain based on their answers to Q1, Q2, and Q3. Explain why this specific bottleneck is costing them money and execution velocity.

2. YOUR 3-TIERED AI IMPLEMENTATION ROADMAP:
   - TIER 1: AUTOMATIONS & WORKFLOWS (Based on Q1-Q3). Provide a concrete automation solution using tools like Zapier, Make, or HighLevel to eliminate manual data entry.
   - TIER 2: KNOWLEDGE BASE & COGNITIVE SEARCH (Based on Q4-Q7). Detail how turning their scattered documentation into a centralized semantic knowledge base or conversational AI assistant can reduce their response latency and employee search time.
   - TIER 3: DIGITAL AGENT EXECUTION SKILLS (Based on Q8-Q10). Outline a specific AI Agent or LLM-driven checklist executor that can handle or augment the high-value task they described.

3. IMMEDIATE NEXT STEPS: Give them a highly actionable, 3-step technical deployment plan to execute this month.

Maintain a professional, authoritative, and direct tone. Do not use generic fluff. Focus heavily on ROI, time retrieval, and system efficiency.
```

#### 3. Add the "Send Email" Action

- **To:** `{{contact.email}}`
    
- **Subject:** `Your Custom Business AI Architecture Blueprint is Ready`
    
- **Body:**
    
    HTML
    
    ```
    Hi {{contact.first_name}},
    
    Thank you for completing the AI Opportunity Assessment. Based on the structural architecture of your current business operations, our system has mapped out your custom AI Implementation Blueprint.
    
    Below is the raw text engine of your architectural roadmap. Review these sections closely:
    
    ---
    
    {{digital_worker_ai_agent.output}}
    
    ---
    
    If you would like to fast-track the development and implementation of these specific AI systems, let's hop on a technical review call to look at the exact custom code and APIs required.
    
    Book your implementation session here: [Insert Your GHL Calendar Link]
    
    Best regards,
    [Your Name/Agency Name]
    ```
    

## Phase 4: The High-Ticket Call Infrastructure

For the $800 Tier, configure an automated processing pipeline that transforms raw conversational call transcripts into structured developer specs.

```
Trigger: Call Status (Direction: Inbound/Outbound, Call Duration > 600 seconds)
  │
  ▼
Action: AI Agent (Extract Specs from Transcript)
  │
  ▼
Action: Create Task / Internal Notification (Review draft)
```

### The Call Spec Extraction Prompt

Create a separate workflow for your Calendar bookings. When a call ends and the transcription is generated natively inside HighLevel, pass the transcript custom variable (`{{communication.call_transcript}}`) into an **AI Agent Workflow Step** using this instruction:

Plaintext

```
You are an advanced Systems Engineering Analyst. Analyze the attached call transcript between our agency and the client.

Extract and structure the conversation into the following technical specifications:
1. CURRENT TECH STACK: List all software tools, CRMs, and databases mentioned by the client.
2. DISCOVERED CHECKLISTS: Identify any step-by-step human processes, validation checklists, or repetitive operational routines discussed during the call.
3. COGNITIVE REPOSITORIES: Document what internal data sources, file shares, or training assets they need mapped into an AI system.
4. TARGET AI SPECIFICATION: Write a functional architectural specification for a custom solution matching our core service offerings:
   - Solution A: Backend Integration/Workflow Automation
   - Solution B: Vector-based Knowledge Base System
   - Solution C: Specialized Autonomous AI Agent

Output this configuration in clear Markdown format so that it can be reviewed, white-labeled, and sent as a high-ticket deployment proposal.
```

### Immediate Deployment Checklist

- [ ] Connect your custom domain and active Stripe account to your GHL Subaccount.
    
- [ ] Go to **Sites > Surveys > Create Survey** and build out the 10 structural questions.
    
- [ ] Create a 2-page funnel, drop the product checkout on Page 1, and embed the Survey on Page 2.
    
- [ ] Build the **Survey Submitted Automation Workflow** and run a mock contact submission through it to verify the AI outputs clean data fields.