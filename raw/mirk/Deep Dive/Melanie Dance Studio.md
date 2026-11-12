# Dance Studio Audit & Operations Summary

## Overview

Audit playbook and operations summary designed for **MIRK Technologies** to conduct a comprehensive structural and technical evaluation of a rapidly scaling dance studio. This document serves as a guide to identifying administrative bottlenecks, assessing technological infrastructure, and establishing data fields for custom AI automation.

  

---

  

## 1. Core Audit Script & Prioritized Questions

  

### Phase 1: Scalability & Strategic Alignment

*   What are your current active enrollment numbers, and what is the absolute maximum capacity of your current physical studio spaces and scheduling slots?

*   What specific operational friction points are you experiencing as you try to transition from a small boutique studio to a large-scale business?

*   What is your primary goal for this operational audit?

*   What is your most hopeful, ideal outcome from implementing new systems or software?

  

### Phase 2: Core Workflows & Process Mapping

*   **Student Onboarding:** Can you walk me through the end-to-end journey of a new student, from their very first digital inquiry or website click to their official registration and attendance in their first class?

*   **Capacity Management:** How do you currently manage fluctuating class sizes, overflowing waitlists, and student class level placements?

*   **Instructor Logistics:** What is your process for assigning instructors to classes, tracking their teaching hours, and finding emergency substitutes?

*   **Studio Communication:** How do you distribute studio wide updates, critical emergency weather closures, or manual billing reminders to parents and students?

*   **Event Coordination:** What does the planning, costuming, ticketing, and volunteer coordination process look like for your annual recitals and special performances?

  

### Phase 3: Technical Infrastructure & Core Systems

*   What productivity software do you currently use for your back-office work (e.g., Google Workspace, Microsoft 365, or specialized tools)?

*   Are you currently using Artificial Intelligence (AI) anywhere in your business operations, marketing, or administrative workflows?

*   Are you actively trying to minimize the hiring of additional front-desk administrative staff during this high-growth phase?

*   Which repetitive, manual administrative tasks are taking up the most hours for your current staff each week?

  

### Phase 4: Financial Health & Marketing Engine

*   Can you describe your current billing and invoice process, and how do you track diverse revenue streams like monthly tuition, recital fees, custom costumes, and retail merchandise?

*   What are your primary fixed and variable overhead expenses?

*   What are your primary marketing channels for lead generation and new client acquisition?

*   What is your estimated conversion rate from an initial prospective inquiry or trial class into a fully paying, recurring member?

  

---

  

## 2. Common Scaling Bottlenecks & Operational Tasks

  

### The Realities of Rapid Growth

When a studio experiences an unexpected surge in demand, standard administrative tasks quickly collapse without adequate automation. The most common failures occur in:

1.  **Lead Processing:** Inundations of trial class requests sit unanswered because there is no automated intake or welcome email sequence.

2.  **Capacity Friction:** Waitlists are managed via manual spreadsheets, resulting in lost revenue or accidental classroom overcrowding.

3.  **Payment Collection:** Chasing declined credit cards and sending tuition reminders manually drains dozens of administrative hours monthly.

  

### Master Admin Checklist for Dance Studios

*   **Daily Tasks:** Managing student registrations, logging digital inquiries, processing daily point-of-sale or tuition payments, handling last-minute schedule changes, and coordinating substitute teachers.

*   **Weekly Tasks:** Running instructor payroll, formatting and broadcasting weekly studio newsletters, and auditing waitlists for highly demanded classes.

*   **Monthly/Seasonal Tasks:** Reconciling financial ledgers, auditing costume order sizes and shipping timelines, tracking retail/apparel inventory, and executing recital ticket sales.

  

---

  

## 3. Studio Management Software Recommendations

  

When evaluating options to recommend to the client, consider these platforms based on their operational scale and budget:

  

*   **StudioLAB:** An affordable, streamlined entry-point option. Plans generally start around **$29/month**, ideal for studios needing basic digital scheduling and foundational student tracking.

*   **Jackrabbit Dance:** The comprehensive industry leader. Offers robust tiered subscription pricing starting around **$49/month** for small student rosters, scaling upward based on enrollment. Advanced upgrades (up to **$93+/month** or custom enterprise rates) unlock premium functionalities such as custom-branded mobile apps for parent portals.

*   **Studio Pro / Class Manager:** High-utility, all-in-one solutions that tightly integrate automated billing, parent portals, digital scheduling, and automated recital performance coordination.

  

---

  

## 4. Custom AI Scheduling Algorithm Blueprint

  

To automate the complex puzzle of studio scheduling and completely eliminate manual clashes, a custom optimization algorithm (built via Python) is highly feasible. 

  

### Required Data Fields for Algorithm Generation

To build this custom logic, the client must provide raw data matching the following schema:

  

```json

{

  "room_inventory": [

    { "room_id": "Studio_A", "max_capacity": 25, "flooring_type": "Marley" }

  ],

  "instructor_profiles": [

    { 

      "instructor_name": "Sarah Jenkins", 

      "styles_qualified": ["Ballet", "Pointe", "Lyrical"], 

      "weekly_availability": ["Mon: 16:00-21:00", "Wed: 16:00-21:00"],

      "max_weekly_hours": 10

    }

  ],

  "class_requirements": [

    { 

      "class_name": "Advanced Ballet II", 

      "style": "Ballet", 

      "duration_minutes": 90, 

      "frequency_per_week": 2,

      "preferred_room_attributes": ["Marley"]

    }

  ],

  "student_enrollment_data": [

    { "class_name": "Advanced Ballet II", "current_enrolled_count": 18, "waitlist_count": 4 }

  ]

}

Technical Execution Plan

Once the studio provides the fields above, MIRK Technologies can implement constraint-satisfaction algorithms (such as genetic algorithms or linear programming libraries like Google OR-Tools) to process the variables and instantly generate optimized, conflict-free seasonal schedules.