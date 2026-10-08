---
title: Design Your Training
---

::: {.callout-tip}
#### Learning Objectives

- Synthesize andragogical principles, instructional strategies, and computational concepts into an end-to-end bioinformatics training proposal.
- Formulate a context-driven workshop plan tailored to the specific infrastructure constraints (bandwidth, hardware, power, OS) of a target institution or region.
- Construct a complete training blueprint: learner persona, Bloom-aligned learning outcomes, backward-designed assessment, and a 6-stage modular schedule.
- Architect an offline-resilient technical strategy utilizing micro-datasets, user-space software deployment, and a robust contingency matrix.
- Deliver an effective, structured presentation pitching the training plan to peers and facilitators.
- Provide and receive constructive peer feedback using a structured evaluation rubric.
:::

## Introduction: The Capstone Challenge

Throughout this course, you have explored both **how to teach** (adult learning principles, participatory live coding, paired programming, backward design, and formative assessment) and **what to teach** (computational fundamentals, UNIX streaming, containers, software deployment, cloud platforms, HPC clusters, micro-datasets, and data interpretation).

Now, it is time to transition from being a student of pedagogy to becoming an **architect of bioinformatics training**.

```
┌────────────────────────────────────────────────────────────────────────┐
│                        THE CAPSTONE JOURNEY                            │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│   [ How to Teach ]                [ What to Teach ]                    │
│   • Andragogy                     • Core Concepts                      │
│   • Live Coding                   • Practical Unix                     │
│   • Backward Design               • Containers & Installation          │
│   • Formative Assessment          • Micro-datasets & Interpretation    │
│           │                               │                            │
│           └───────────────────────┬───────┘                            │
│                                   │                                    │
│                                   ▼                                    │
│             ┌───────────────────────────────────────────┐              │
│             │     YOUR ACTIONABLE TRAINING PROPOSAL     │              │
│             │   "A battle-tested, resource-resilient    │              │
│             │    workshop plan for your home community" │              │
│             └─────────────────────┬─────────────────────┘              │
│                                   │                                    │
│                                   ▼                                    │
│             ┌───────────────────────────────────────────┐              │
│             │         PEER REVIEW & PRESENTATION        │              │
│             └───────────────────────────────────────────┘              │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

The goal of this capstone activity is not to complete an abstract theoretical assignment. Your deliverable is a **fully developed, practical workshop plan** that you can take back to your home institution, research group, or national network and deliver to real learners.


## The 7 Components of a Robust Training Plan

Your training plan must address seven essential components. As you design, ensure that every decision directly accounts for the real-world constraints of your target audience:

| Component | Details |
| :--- | :--- |
| 1. Context & venue profile | • Institution, power, internet |
| 2. Target learner persona | • Background, goals, hurdles |
| 3. Measurable outcomes (Bloom) | • 3–5 observable action verbs |
| 4. Curriculum & tool selection | • Right-sized for constraints |
| 5. Instructional delivery model | • Live coding, pair roles, TAs |
| 6. Technical & logistics plan | • Micro-data, offline Plan B |
| 7. Assessment & evaluation strategy | • Formative telemetry (stickies/MCQs) + authentic capstone task |

: Table 1: The 7 core proposal components

### Component 1: Context & Institutional Profile
- **Target Institution / Location:** Where will the workshop take place?
- **Duration & Format:** (e.g. 2-day in-person intensive, 5-day half-day workshop, or distributed hub-and-spoke).
- **Infrastructural Reality:** What is the electrical grid reliability? What is the actual internet bandwidth (e.g. 3 Mbps shared mobile hotspot)? What hardware is available (institutional lab desktops vs. personal student laptops)?

### Component 2: Target Learner Persona
- Develop one concrete persona representing your audience (Role, Domain Expertise, Computational Baseline, Motivations, and Pain Points).
- *Remember:* Avoid designing for "anyone." Tailor the course to this specific persona.

### Component 3: Measurable Learning Outcomes (Backward Design)
- Write 3 to 5 clear learning outcomes using **Bloom’s Revised Taxonomy** action verbs (*execute, differentiate, diagnose, validate*).
- Ensure they describe observable learner capabilities, not instructor activities.

### Component 4: Curriculum & Content Strategy
- What specific topics will you teach?
- How do these topics connect to solve a locally relevant biological or clinical problem (e.g. pathogen surveillance, crop improvement, neglected tropical diseases)?
- What topics did you deliberately choose **not** to teach to prevent curriculum bloat?

### Component 5: Instructional Delivery & Human Staffing
- How will you teach? (e.g. participatory live coding, faded examples, paired programming).
- How will you manage cognitive load (enforcing the 15-minute rule and the Rule of Thirds)?
- What is your helper staffing plan? How many roving teaching assistants will you recruit and how will they be briefed?

### Component 6: Technical Logistics & Contingency Plan (Plan B)
- **Data Strategy:** What micro-datasets will you engineer? Where will you use pre-computed outputs?
- **Software Strategy:** How will software be deployed without administrative root permissions (e.g. standalone static binaries, Micromamba, Apptainer `.sif` files)?
- **Offline Protocol:** How will you distribute data and tools without relying on live classroom internet downloads?
- **Contingency Matrix:** What is your exact fallback plan if power cuts or network blackouts occur?

### Component 7: Assessment & Impact Strategy
- **Formative Assessment:** What low-tech diagnostic techniques will you use during class (e.g. two-color sticky notes, chest finger voting, diagnostic MCQs)?
- **Authentic Summative Task:** What real-world deliverable will learners construct on the final afternoon?
- **Impact Measurement:** How will you measure self-efficacy gains (pre/post-surveys) and track 6-month research translation?


## Workshop Development Workflow: Step-by-Step

Participants will work individually over a dedicated **day long design sprint** structured into five phases:

| Phase | Key milestone |
| :--- | :--- |
| 1. Context & persona  | Complete venue profile & learner persona card |
| 2. Backward design | Draft Bloom outcomes & authentic assessment task |
| 3. Technical plan | Micro-dataset specs, install method, and Plan B matrix |
| 4. Peer tuning exchange | Structured peer review with other participants |
| 5. Pitch preparation | Prepare training plan to pitch to room and facilitators |

: Table 2: The 5-phase design timeline


## Pitching Your Training Plan: Presentation Guidelines

Each individual  deliver a **10 minute pitch** followed by **3–4 minutes of facilitator and peer Q&A**.

### Recommended 6-Slide Presentation Structure:

1. **Slide 1: Title, Local Need & Venue Context**
   - Workshop title, target institution/region, duration, and the local health/agricultural challenge driving the need.
2. **Slide 2: The Learner Persona**
   - Meet your learner: domain background, computational baseline, and specific hardware/connectivity constraints.
3. **Slide 3: Measurable Learning Outcomes (Backward Design)**
   - 3 to 4 Bloom-aligned learning outcomes stating what trainees will be able to do.
4. **Slide 4: Curriculum Architecture & Delivery Model**
   - High-level modular schedule applying the Rule of Thirds; participatory live-coding and paired-programming strategy.
5. **Slide 5: Technical Plan, Micro-datasets & Contingency Matrix**
   - Software deployment method (user-space / containers); micro-dataset design; Plan B for power and internet failure.
6. **Slide 6: Assessment Deliverable & Evaluation**
   - The authentic capstone task learners will solve; pre/post-survey strategy to measure long-term impact.


## Peer Review Rubric: The "Tuning Protocol"

During the peer exchange phase, use the following evaluation rubric to give constructive, actionable feedback:

| Dimension | Guiding evaluation questions |
| :--- | :--- |
| 1. Constructive alignment | Do the learning outcomes use measurable action verbs? Does the assessment truly measure them? |
| 2. Empathy & persona relevance | Is the pace realistic for the defined persona? Does it solve the "Expert-Novice Paradox"? |
| 3. Resource realism | Is the plan 100% viable offline? Will datasets run on 4 GB RAM laptops without crashing? |
| 4. Contingency preparedness | Is Plan B robust? What happens if power or internet cuts out unexpectedly? |
| 5. Interactive pacing | Does the plan obey the Rule of Thirds and the 15-minute instructional rule? |

: Table 3: Peer evaluation rubric

::: {.callout-note}
## Warm vs. Cool Feedback
When reviewing peer proposals, structure your verbal and written critique:

- **Warm Feedback (Affirmations):** *"I really like how your micro-dataset specifically targets the malaria rpoB locus—that makes the exercise biologically authentic while keeping file sizes under 2 MB."*
- **Cool Feedback (Posing Inquiries):** *"I noticed that on Day 2, you have three hours of continuous command-line tools scheduled before lunch. How might you introduce a sticky-note checkpoint or a 15-minute paired exercise to prevent cognitive fatigue?"*
:::


## Capstone Worksheets & Practical Exercises

Use these guided exercises to assemble and stress-test your training proposal.

::: {.callout-exercise}
## Training Plan Blueprint Worksheet

Complete the following master blueprint for your proposed training program:

1. **Course Identity:**
   - Course Title:
   - Target Institution & Country:
   - Course Duration (Days / Hours per day):
   - Local Problem Addressed:

2. **Venue & Infrastructure Audit:**
   - Power Reliability (Outages expected? UPS available?):
   - Internet Speed & Reliability (Mbps, limits):
   - Participant Laptops (OS distribution, RAM ceiling):
   - Administrative Permissions (Do learners have root/admin access?):

3. **Learner Persona:**
   - Name & Professional Role:
   - Biological Background:
   - Computational Baseline:
   - Primary Motivation:
   - Key Frustration / Fear:

4. **Backward-Designed Learning Outcomes (3–4 Bloom Outcomes):**
   - Outcome 1:
   - Outcome 2:
   - Outcome 3:

5. **Resource-Conscious Technical Architecture:**
   - Software Deployment Strategy (Conda / Static Binaries / Apptainer):
   - Micro-dataset Design (How was data subsetted? What size?):
   - Offline Distribution Method (USB / Local LAN):

6. **The Contingency Matrix:**
   - What happens if the internet dies completely on Day 1?
   - What happens if municipal electricity blackouts occur for 2 hours?
   - What happens if an older student laptop crashes repeatedly?

7. **Authentic Assessment Task:**
   - What real-world biological challenge will learners solve on the final afternoon?
   - What specific deliverable will they produce?

::: {.callout-answer}
### Self-Audit Checklist Before Presentation

Before presenting your blueprint to the room, verify that:

- [ ] Every learning outcome starts with an observable action verb (no "understand", "learn", or "appreciate").
- [ ] No tool requires live downloading during workshop hours.
- [ ] All datasets run in under 60 seconds on a 4 GB RAM dual-core laptop.
- [ ] The schedule contains at least 30% dedicated buffer time for questions, helper catch-up, and breaks.
- [ ] The authentic assessment deliverable can be evaluated without traditional grading exams.
:::
:::

::: {.callout-exercise}
## Defending Your Proposal Against Simulated Disruptions

During your presentation, the facilitators will introduce a surprise simulated disruption to test your plan's resilience. Prepare your defense for the following two scenarios:

- **Disruption 1:** *"The venue administrator informs you that due to a network security audit, the classroom Wi-Fi will be turned off for the entire week. How does your plan survive?"*
- **Disruption 2:** *"A participant brings an institutional laptop that cannot execute your container image due to locked administrative security policies. How do you ensure they don't spend three days sitting idle?"*

::: {.callout-answer}
### Model Trainer Responses

- **Response to Disruption 1 (Zero Internet):**
  *"Our entire curriculum is designed offline-first. All software packages have been pre-compiled into static binaries and bundled into an offline USB drive alongside our HTML course book. All micro-datasets and reference files are contained in the same USB bundle. We will not use the internet for a single minute of the workshop."*

- **Response to Disruption 2 (Locked Laptop):**
  *"We have a multi-tiered fallback. First, we pair this learner with a neighboring participant using the Driver-Navigator paired-programming model, immediately engaging them in hands-on active learning. Second, we can transition them to a pre-configured lightweight Linux live USB stick that boots into an open operating system without touching their internal hard drive, or provide a loaner machine."*
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- **The Capstone is Your Launchpad:** This exercise transitions you from absorbing pedagogical theory to becoming an empowered training designer equipped with a viable course proposal.
- **Context is King:** The best bioinformatics training plans are not copies of Western university courses; they are custom-tailored to local learner personas, institutional infrastructure, and regional biological priorities.
- **Backward Design Guarantees Impact:** Start with measurable Bloom outcomes and authentic assessments before selecting tools or drafting lesson slides.
- **Resilience Through Preparation:** Anticipate low-resource realities by enforcing offline distribution, micro-datasets, low-memory footprints, and robust Plan B contingency protocols.
- **Pitch with Conviction:** Present your training proposal clearly, defend your design choices against real-world disruptions, and leverage constructive peer feedback to refine your curriculum.
:::
