---
title: Course Introduction & Orientation
---

::: {.callout-tip}
#### Learning Objectives

- Articulate the overarching philosophy, scope, and target outcomes of this train-the-trainer programme.
- Identify the dual challenges confronting bioinformatics trainers in resource-constrained settings: cognitive friction and infrastructural precarity.
- Navigate the three-part curriculum roadmap spanning pedagogical theory, defensive computing tools, and sustainable community architecture.
- Adopt the dual mindset of "learner-participant" and "reflective educator" throughout the workshop.
- Establish a personal baseline teaching context profile to guide your capstone training design.
:::

## Welcome to Teaching Bioinformatics

Welcome to *Teaching Bioinformatics in Low-resource Settings*. This course is not a standard bioinformatics workshop where you learn how to assemble a genome or call variants. Instead, it is an intensive **train-the-trainer programme** designed to transform subject-matter specialists (researchers, core facility analysts, clinicians, and university lecturers) into resilient, empathetic, and highly effective computational educators.

Worldwide, bioinformatics has transitioned from an niche academic sub-discipline into the operational backbone of modern life sciences, clinical diagnostics, and public health surveillance. Yet, the vast majority of bioinformatics educational resources and training methodologies originate in high-income research hubs. These curricula routinely take foundational infrastructure for granted:

- Unmetered, multi-gigabit fibre-optic campus Wi-Fi.
- Immediate access to institutional High-Performance Computing (HPC) clusters or pre-funded cloud accounts.
- Homogeneous cohorts equipped with high-spec Apple Silicon or Linux workstations.
- An abundance of local systems administrators, teaching assistants, and experienced computational mentors.

When trainers attempt to transplant these high-resource curricula directly into low- and middle-income countries (LMICs) or under-resourced regional institutions, the training frequently breaks down. Instructors encounter what we term the **Infrastructure Shock**: download commands fail halfway through due to bandwidth throttling, outdated student laptops run out of RAM, power cuts terminate running pipelines, and adult learners sit paralyzed by command-line anxiety.

This course exists to demonstrate that **world-class bioinformatics training does not require luxury infrastructure**. By combining modern, evidence-based adult learning theory with defensive computational design, you will learn how to build workshops that are pedagogically empowering, technically bulletproof, and fully sustainable in any setting.


## The Double Hurdle of Low-Resource Instruction

Educators in resource-constrained environments confront a unique dynamic known as the **Double Hurdle**. In a standard classroom, learners face only one primary challenge: mastering the academic curriculum. In low-resource settings, both instructors and students must clear two distinct hurdles simultaneously:

| 1. Pedagogical & cognitive | 2. Infrastructural & material |
| :--- | :--- |
| • Abstract command-line syntax | • Rolling blackouts & power cuts |
| • "Expert-novice blind spot" | • Severe bandwidth & download caps |
| • Acute terminal anxiety & shame | • Heterogeneous, low-spec laptops |
| • Cognitive load overload | • Windows CRLF / permission bugs |
| • Heavy clinical/wet-lab burdens | • Absence of institutional HPC/IT |

: Table 1: The double hurdle

### 1. The Pedagogical and Cognitive Hurdle
Adult learners in your workshops are typically accomplished professionals: senior microbiologists, physicians, parasitologists, or postgraduates. In their laboratories or clinics, they command respect. When seated in front of a raw Unix terminal, a single cryptic error message (`command not found`, `permission denied`, or `SyntaxError`) can induce acute **terminal anxiety** and imposter syndrome. If instructors rush through commands or take over keyboards, adult learners disengage and conclude that bioinformatics is an elitist discipline reserved for computer scientists.

### 2. The Infrastructural and Material Hurdle
Simultaneously, the technical foundation beneath the classroom is inherently precarious. Bandwidth is rarely sufficient for 25 simultaneous `conda install` or `apt-get` downloads. Electricity may cut out without warning. Student laptops vary wildly—from decade-old dual-core Windows machines with 4 GB of RAM to locked-down institutional laptops that prohibit software installation.

As an educator in these settings, your job is not merely to transmit technical knowledge; you are an **architect of cognitive safety and operational resilience**. Every lesson you deliver must be engineered to anticipate failure, degrade gracefully, and succeed entirely offline.


## The Three-Part Curriculum Roadmap

This course is organised into three integrated parts, moving systematically from pedagogical foundations to technical toolsets, and culminating in a full curriculum design sprint:

| Part 1: How to Teach | Part 2: What to Teach | Part 3: Sustain |
| :--- | :--- | :--- |
| • What is Bioinformatics | • Open Resources (FAIR) | • Capstone Training Design Sprint |
| • Adult Learning (Androgogy) | • Core Computing Concs | • Pitching Your Workshop Plan |
| • Active Strategies | • Practical UNIX & Bash | • Communities of Practice |
| • Effective Delivery | • Containers (Apptainer) | • Combating Lone Bioinformatician Syndrome |
| • Training Design (Bwd) | • Software Installation | |
| • Lesson Planning Arc | • Cloud vs Locality | |
| • Formative Assessment | • HPC SLURM Workflows | |
| • Authoring with Quarto | • Micro-datasets | |
| | • Data Interpretation | |
| | • Responsible AI Mentors | |

: Table 2: Course curriculum roadmap for trainer development

### Part 1: How to Teach Bioinformatics (Chapters 1–8)
We begin with the human element:

- **Adult Learning Theory (Andragogy):** Understanding Knowles' principles, managing cognitive load, and dismantling the "Expert-Novice Paradox".
- **Active Teaching Methodologies:** Mastering participatory live coding, faded examples, and driver-navigator pair programming.
- **Classroom Orchestration:** Cultivating psychological safety, managing helpers with the "hands-off-keyboard" rule, and timing with the Rule of Thirds.
- **Curriculum Architecture:** Applying Wiggins & McTighe's Backward Design framework with observable Bloom's taxonomy action verbs.
- **Lesson Planning & Delivery Logistics:** Structuring 6-stage lesson arcs, applying the Double-Time Rule, and building contingency matrices.
- **Diagnostic Assessments:** Creating multiple-choice questions with diagnostic distractors and zero-bandwidth feedback mechanisms.
- **Authoring Open Courseware:** Packaging FAIR-compliant, portable learning materials with Quarto, Markdown callouts, and offline static site bundles.

### Part 2: What to Teach: The Low-Resource Toolset (Chapters 9–17)
Next, we explore how to adapt computational bioinformatics content for constrained environments:

- **Open Educational Resources:** Repurposing high-quality curricula from The Carpentries, Galaxy Training Network (GTN), and H3ABioNet.
- **Computational Fundamentals:** demystifying hardware (RAM vs CPU vs disk), memory exhaustion (`Killed 137`), plain text vs binary formats, and Windows CRLF issues.
- **Defensive UNIX & Scripting:** Teaching file inspection without Microsoft Excel corruption, tabular wrangling with `awk` and `cut`, and bulletproof scripting with `set -euo pipefail`.
- **Containerisation:** Utilizing Docker and rootless Apptainer/Singularity (`.sif`) to package dependencies for offline USB distribution.
- **Software Installation:** Avoiding Conda dependency solve lockouts using Micromamba and portable `conda-pack` offline bundles.
- **Cloud & HPC Economics:** Navigating the "Data Locality Rule", preventing cloud bill shock, and teaching HPC cluster etiquette through SLURM queue mechanics.
- **Micro-datasets:** Downsampling gigabyte-scale sequencing libraries into 2-megabyte classroom datasets that run in under 60 seconds on modest laptops.
- **Data Interpretation:** Shifting focus from mere pipeline execution to biological quality control, batch effect detection, and statistical significance.
- **Responsible Use of AI:** Guiding learners to treat Large Language Models as 24/7 virtual tutors while rigorously guarding against hallucinations, deprecated syntax, and data leakage.

### Part 3: Design and Sustain your Training (Chapters 18–19)
Finally, you will synthesize everything you have learned into actionable practice:

- **The Capstone Design Sprint:** You will design a complete, customized bioinformatics workshop plan for your home institution and pitch it to your peers and instructors for feedback.
- **Communities of Practice:** Strategies to overcome post-workshop attrition, dismantle the "lone bioinformatician syndrome", and launch sustainable local study groups and Hacky Hours.


## How to Engage With This Course: The Dual Mindset

To extract the maximum value from this course, we ask you to adopt the **Dual Mindset** at all times:

::: {.callout-important}
### The Dual Mindset: Participant and Instructor

During every session, you will occupy two distinct roles simultaneously:

1. **The Learner/Participant:** You participate in the exercise, run the command, solve the problem, or analyze the data as if you were a student in a workshop. Notice your emotional reactions: Where did you hesitate? What was confusing?
2. **The Reflective Instructor:** You analyze the exercise from the trainer's balcony: *Why did the instructor phrase the prompt this way? What diagnostic misconception was embedded in distractor C? Why did the instructor deliberately make that typing mistake on screen? How would this fail if the classroom lost Wi-Fi?*
:::

### Classroom Mechanics and Communication Protocols

Throughout our sessions, we will employ low-bandwidth, non-verbal feedback protocols that you can adopt directly in your future teaching:

- **The Sticky Note Protocol:** Each participant receives one green and one pink/orange sticky note. 
  - *Green note on laptop lid:* "I have completed the exercise and am ready to proceed."
  - *Pink note on laptop lid:* "I am stuck or encountered an error; I need a helper."
  This removes the social stigma of raising hands and gives the lead instructor an instantaneous visual heatmap of room progress.
- **Chest Voting (Zero-Bandwidth Polling):** During formative assessments, participants hold 1 to 4 fingers against their sternum to vote for options A, B, C, or D. Because votes are held close to the body, learners cannot copy their peers, eliminating conformity bias without requiring polling apps or internet access.
- **The Hands-Off-Keyboard Rule:** When helpers assist you during exercises, they are strictly prohibited from touching your keyboard or mouse. They must guide you verbally while your hands type the solution. This preserves learner agency and muscle memory.
- **The 15-Minute Rule:** When stuck on an error, spend at least 10 minutes reading the error message carefully and formulating a diagnosis, but do not struggle alone for more than 15 minutes before asking for help.


## Interactive Exercise: Assessing Your Teaching Ecosystem

::: {.callout-exercise}
### Exercise 1.1: Establishing Your Baseline Teaching Profile

Before diving into pedagogical theory, let us map the real-world conditions under which you currently teach or plan to teach. Take 8 minutes to answer the following four questions in your personal course notes:

1. **Target Cohort:** Who are your future learners (e.g. wet-lab MSc students, clinical registrars, senior university faculty)? What is their computational starting baseline?
2. **Hardware Reality:** What devices will your learners bring (personal Windows laptops, shared desktop computer labs, institutional MacBooks)? Do they possess local administrative rights (`sudo`/admin)?
3. **Connectivity & Power:** How reliable is the internet bandwidth and electrical grid at your target training venue? Have you planned an entirely offline contingency?
4. **Primary Pedagogical Frustration:** What is the single biggest bottleneck you have observed in bioinformatics training at your home institution (e.g., software installation collapse, cognitive overload, post-workshop abandonment)?

::: {.callout-answer collapse="true"}
#### Facilitator Reflection & Debrief

Notice that almost every trainer in low-resource settings identifies similar bottlenecks:

- **Hardware Heterogeneity:** Most students arrive with Windows machines carrying varied antivirus software and minimal RAM, making unstandardised installations painful.
- **Administrative Lockouts:** Trainees using hospital or institutional laptops often cannot install Docker or Miniconda without institutional IT intervention.
- **The "Installation Abyss":** In many traditional workshops, the entire first day is lost to troubleshooting package dependencies, leaving students exhausted before any biological concepts are introduced.
- **Post-Workshop Isolation:** Students leave inspired, but within two weeks hit an unexplained error on their own data and give up because they lack local peer support.

Keep your answers close at hand. Throughout this course, you will refine these notes into your master Capstone Blueprint in Chapter 20.
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- World-class bioinformatics training does not require luxury infrastructure; it requires pedagogical intentionality and defensive technical design.
- Trainers in resource-constrained environments face the **Double Hurdle**: addressing adult cognitive load and terminal anxiety while simultaneously mitigating infrastructural precarity.
- Effective instruction treats errors not as disruptions, but as authentic learning opportunities.
- Adopt the **Dual Mindset**: participate as a student while continuously evaluating the pedagogical design as an instructor.
- The course progresses systematically from adult learning principles (Part 1) to defensive computational tooling (Part 2), culminating in an actionable workshop blueprint and community sustainability roadmap (Part 3).
:::
