---
title: Course Introduction
---

::: {.callout-tip}
#### Learning Objectives

- Articulate the overall philosophy, scope, and target outcomes of this train-the-trainer programme.
- Identify the dual challenges confronting bioinformatics trainers in resource-constrained settings: educational roadblocks and infrastructural barriers.
- Navigate the three part curriculum roadmap spanning training principles, practical training, and sustainable community architecture.
- Establish a personal baseline teaching context profile to guide your final training design.
:::

## Welcome to Teaching Bioinformatics in Low-resource Settings

Welcome to *Teaching Bioinformatics in Low-resource Settings*. This course is not a standard bioinformatics workshop where you learn how to assemble a genome or call variants. Instead, it is an intensive **train-the-trainer programme** designed to transform subject-matter specialists (researchers, core facility analysts, clinicians, and university lecturers) into resilient, empathetic, and effective bioinformatics educators.

Worldwide, bioinformatics has transitioned from a niche academic sub-discipline into the backbone of modern life sciences, clinical diagnostics, and public health surveillance. However, the vast majority of bioinformatics educational resources and training methodologies originate in high-income research hubs. These curricula routinely take foundational infrastructure for granted:

- Unlimited, high-speed fibre-optic campus Wi-Fi.
- Access to institutional High-Performance Computing (HPC) clusters or pre-funded cloud accounts.
- Cohorts equipped with high-spec Apple Silicon or Linux workstations.
- An abundance of local systems administrators, teaching assistants, and experienced computational mentors.

When trainers attempt to transplant these high-resource curricula directly into low- and middle-income countries (LMICs) or under-resourced regional institutions, the training frequently breaks down. Instructors encounter unexpected infrastructure challenges: download commands fail halfway through due to insufficient bandwidth, outdated student laptops run out of RAM and power cuts terminate running pipelines.

This course aims to demonstrate that **world-class bioinformatics training does not require advanced infrastructure**. By combining modern, evidence-based learning theory with well thought out computational design, you will learn how to build training programmes that are pedagogically empowering, technically robust, and fully sustainable in any setting.


## The Double Hurdle of Low-Resource Instruction

Educators in resource-constrained environments confront a unique dynamic. In a standard classroom, learners face only one primary challenge: mastering the academic curriculum. In low-resource settings, both instructors and students must clear two distinct hurdles simultaneously:

| 1. Pedagogical & cognitive | 2. Infrastructural & material |
| :--- | :--- |
| • Abstract command-line syntax | • Rolling blackouts & power cuts |
| • Going from an expert to a novice | • Severe bandwidth & download caps |
| • Acute terminal anxiety | • Heterogeneous, low-specification laptops |
| • Cognitive load overload | • Windows CRLF / permission bugs |
| • Heavy clinical/wet-lab burdens | • Absence of institutional HPC/IT |

: Table 1: Additional challenges faced in low-resource settings

**1. The Pedagogical and Cognitive Hurdle**

Learners in your training may be professionals: senior microbiologists, physicians, parasitologists, or postgraduates. In their laboratories or clinics, they command respect. When seated in front of a Unix terminal, a single confusing error message (`command not found`, `permission denied`, or `SyntaxError`) can induce **terminal anxiety** leading to imposter syndrome. If instructors rush through commands or take over keyboards, learners may disengage and conclude that bioinformatics is a discipline reserved for computer scientists.

**2. The Infrastructural and Material Hurdle**

Simultaneously, the technical foundation beneath the classroom can be shakey. Bandwidth is rarely sufficient for 25 simultaneous `conda install` or `apt-get` downloads. Electricity may cut out without warning. Student laptops vary from decade-old dual-core Windows machines with 4 GB of RAM to locked institutional laptops that prohibit software installation.

As an educator in these settings, your job is not merely to transmit technical knowledge; every lesson you deliver must be engineered to anticipate failure and potentially succeed entirely offline.


## The Curriculum

This course is organised into three integrated parts, moving systematically from design to implementation, and culminating in a full curriculum design sprint:

| Part 1: Design | Part 2: Implementation | Part 3: Design Your Training |
| :--- | :--- | :--- |
| • What is Bioinformatics | • Open Resources (FAIR) | • Training Design Sprint |
| • Learning Strategies | • Containers | • Pitching Your Training Plan |
| • Strategies for Training | • Software Installation | • Communities of Practice |
| • Effective Delivery | • Cloud-based Computing | • Combating Lone Bioinformatician Syndrome |
| • Training Design | • Using an HPC for training | |
| • Lesson Planning | • Micro-datasets | |
| • Formative Assessment | • Authoring with Quarto | |
| • Responsible use of AI | | |

: Table 2: Course curriculum

### Part 1: Principles of Bioinformatics Training Design (Chapters 2–9)
We begin with the theoretical side of teaching (pedagogy) and material development:

- **Learning Theories:** Understanding Knowles' principles, managing cognitive load, and dismantling the "Expert-Novice Paradox".
- **Active Teaching Methodologies:** Mastering participatory live coding, faded examples, and driver-navigator pair programming.
- **Classroom Orchestration:** Cultivating psychological safety, managing helpers with the "hands-off-keyboard" rule, and timing with the Rule of Thirds.
- **Curriculum Architecture:** Applying Wiggins & McTighe's Backward Design framework with observable Bloom's taxonomy action verbs.
- **Lesson Planning & Delivery Logistics:** Structuring lesson arcs, applying the double-time rule, and building contingency matrices.
- **Diagnostic Assessments:** Creating multiple-choice questions with diagnostic distractors.
- **Responsible Use of AI:** Guiding learners to treat Large Language Models as 24/7 virtual tutors while rigorously guarding against hallucinations, deprecated syntax, and data leakage.

### Part 2: Building Practical and Scaleable Bioinformatics Training (Chapters 10–17)
Next, we explore how to adapt computational bioinformatics content for resource-constrained environments:

- **Open Educational Resources:** Repurposing high-quality curricula from The Carpentries, Galaxy Training Network (GTN) and H3ABioNet.
- **Containerisation:** Utilizing Docker and rootless Apptainer/Singularity (`.sif`) to package dependencies for offline USB distribution.
- **Software Installation:** Avoiding Conda dependency solve lockouts using Micromamba and portable `conda-pack` offline bundles.
- **Cloud & HPC Economics:** Navigating the "Data Locality Rule", preventing cloud bill shock, and teaching HPC cluster etiquette through SLURM queue mechanics.
- **Micro-datasets:** Downsampling gigabyte-scale sequencing libraries into 2-megabyte classroom datasets that run in under 60 seconds on modest laptops.
- **Authoring Open Courseware:** Packaging FAIR-compliant, portable learning materials with Quarto, Markdown callouts, and offline static site bundles.
- **Case Studies:** Discussing how to adapt existing training materials to your context.

### Part 3: Design your Training (Chapters 18–19)
Finally, you will synthesize everything you have learned into building a plan for delivering training in your institution:

- **The Training Design Sprint:** You will design a complete, customized bioinformatics training plan for your home institution and pitch it to your peers and instructors for feedback.
- **Communities of Practice:** Strategies to overcome post-workshop attrition, dismantle the "lone bioinformatician syndrome", and launch sustainable local study groups and Hacky Hours.

## Interactive Exercise: Assessing Your Teaching Ecosystem

::: {.callout-exercise}
### Establishing Your Baseline Teaching Profile

Before diving into pedagogical theory, let us map the real-world conditions under which you currently teach or plan to teach. Take 10 minutes to answer the following four questions:

1. **Target Cohort:** Who are your future learners (e.g. wet-lab MSc students, clinicians, university faculty)? What is their computational starting baseline?
2. **Hardware Reality:** What devices will your learners bring (personal Windows laptops, shared desktop computer labs, institutional MacBooks)? Do they possess local administrative rights (`sudo`/admin)?
3. **Connectivity & Power:** How reliable is the internet bandwidth and electrical grid at your target training venue? Can your course be run entirely offline?
4. **Primary Pedagogical Obstacle:** What is the single biggest bottleneck you have observed in bioinformatics training at your home institution (e.g. software installation collapse, cognitive overload, post-workshop abandonment)?

::: {.callout-answer}
#### Your Baseline Teaching Profile

Notice that almost every trainer in low-resource settings identifies similar bottlenecks:

- **Hardware Heterogeneity:** Most students arrive with Windows machines carrying different antivirus software and minimal RAM, making unstandardised installations painful.
- **Administrative Lockouts:** Trainees using hospital or institutional laptops often cannot install Docker or Miniconda without institutional IT intervention.
- **Losing Time to Installation":** In many traditional workshops, the entire first day is lost to troubleshooting package dependencies, leaving students exhausted before any biological concepts are introduced.
- **Post-Workshop Isolation:** Students leave inspired, but within two weeks hit an unexplained error on their own data and give up because they lack local peer support.

Keep your answers close at hand. Throughout this course, you will refine these notes into your master training plan in Chapter 18.
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- World-class bioinformatics training does not require advanced infrastructure; it requires the correct teaching mindset and a robust plan for running the workshop successfully.
- Trainers in resource-constrained environments face the **Double Hurdle**: addressing cognitive load and anxiety about new computational techniques while simultaneously mitigating infrastructural instability.
- Effective instruction treats errors not as disruptions, but as authentic learning opportunities.
- The course progresses systematically from training design (Part 1) to practical guidance on how to deliver bioinformatics training (Part 2), culminating in an actionable training plan (Part 3).
:::
