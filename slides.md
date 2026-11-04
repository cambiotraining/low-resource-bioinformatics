---
title: "Teaching Bioinformatics in Low-resource Settings"
subtitle: "Trainer Development Workshop"
author: "Cambridge Research Informatics Training (CRIT)"
date: "2026"
format:
  pptx:
    slide-level: 2
---

# Welcome & Overview

## Welcome to the Course
- **Goal:** Equip you to design, deliver, and evaluate impactful bioinformatics training in resource-constrained environments.
- **Audience:** Researchers, educators, clinicians, and core facility staff based in or working with low-resource institutions.
- **Approach:** Evidence-based adult learning pedagogy paired with practical, resource-resilient computational strategies.
- **Final Outcome:** A complete, peer-reviewed training plan ready for delivery at your home institution.

## The Low-Resource Reality
- Infrastructure constraints are systemic, not accidental:
  - Unstable power grids and frequent blackouts.
  - Slow, expensive, or intermittent internet bandwidth.
  - Modest learner hardware (e.g., 4–8 GB RAM consumer laptops).
  - Lack of dedicated institutional High Performance Computing (HPC).
  - Absence of formal computational curricula in life-science degrees.
- **Key Insight:** Standard Western training models must be adapted—not simply transplanted—to succeed.

## Course Structure: Three Core Pillars
1. **Part 1: Principles of Bioinformatics Training Design**
   - Andragogy, live coding, pair programming, effective delivery, backward design, lesson planning, assessment, and responsible AI.
2. **Part 2: Building Practical & Scaleable Bioinformatics Training**
   - Open educational resources, containers, software installation, cloud, server architecture, micro-datasets, Quarto authoring, and case studies.
3. **Part 3: Design and Sustain your Training**
   - Training design sprint, proposal pitch presentations, and communities of practice.


# Part 1: Principles of Bioinformatics Training Design

# Module 1: What is Bioinformatics?

## Defining Bioinformatics
- Interdisciplinary science combining:
  - **Biological Sciences:** Domain expertise, assays, and experimental design.
  - **Computer Science:** Algorithms, command-line interfaces, pipelines, and version control.
  - **Statistics & Mathematics:** Hypothesis testing, normalization, FDR, and modeling.
- **The Core Mission:** Extracting biological meaning from high-dimensional data through computation.
- Not merely "running software"—it is an investigative biological discipline.

## Why Bioinformatics Matters in Low-Resource Settings
- **Addressing Local Priorities:** Real-time surveillance of endemic pathogens (malaria, TB, cholera, viral threats) and agricultural improvement.
- **Dismantling "Helicopter Science":** Enabling local researchers to analyze, interpret, and publish their own data rather than exporting samples.
- **High Return on Investment:** High-impact discovery science without multi-million-dollar wet-lab consumable budgets.
- **The Modern Bottleneck:** Sequencers (e.g. Oxford Nanopore) are accessible; analytical expertise is the primary constraint.

## Overcoming the Conceptual & Technical Hurdle
- Life scientists face two steep learning curves simultaneously:
  1. **Conceptual Complexity:** Abstract algorithms (de Bruijn graphs, Bayesian phylogenetics, statistical models).
  2. **Technical Modality:** Text-only terminals, file permissions, coordinate paths, and cryptic error messages.
- Presenting both simultaneously triggers cognitive overload.
- **Pedagogical Strategy:** Separate the hurdles—build spatial computational models before introducing complex biological algorithms.


# Module 2: Learning Principles (Andragogy)

## Pedagogy vs. Andragogy
- **Pedagogy (Teaching Children):**
  - Teacher controls what, when, and how learning happens.
  - Subject-centred curriculum; external motivation (grades).
  - Assumes dependent learners with little prior experience.
- **Andragogy (Helping Adults Learn - Knowles, 1968):**
  - Self-directed, autonomous learners.
  - Rich reservoir of existing domain expertise.
  - Problem-centred orientation focused on immediate real-world tasks.
  - Driven by internal motivation (career advancement, solving research hurdles).

## Knowles' Core Assumptions in Bioinformatics
1. **Need to Know:** Explain *why* a tool matters before demonstrating syntax.
2. **Self-Concept:** Treat learners as autonomous peers, not passive students.
3. **Prior Experience:** Anchor computational steps to physical wet-lab assays (e.g., quality scores $\rightarrow$ gel band clarity).
4. **Readiness to Learn:** Focus on data and tools directly relevant to their research.
5. **Orientation to Learning:** Organize around scientific questions, not tool manuals.
6. **Motivation:** Cultivate problem-solving confidence and scientific autonomy.

## Imposter Syndrome & Psychological Safety
- Trainees are accomplished professionals (postdocs, PIs, senior clinicians).
- Facing a terminal error (`command not found`) makes them feel reduced to novices.
- **Common Reactions:** Imposter syndrome, terminal anxiety, and silent withdrawal.
- **Instructor Intervention:**
  - Create psychological safety on Day 1.
  - Explicitly normalize syntax errors as the natural language of coding.
  - Reaffirm domain expertise: *"Without your biology, bioinformatics has nothing to compute."*

## From Content Transmitter to Empathetic Facilitator
- **Authoritative Instructor:** Transmitting prescribed content from the podium.
- **Empathetic Facilitator:** Managing the learning environment and supporting inquiry.
- **Key Facilitator Responsibilities:**
  - Diagnosing learner baselines and negotiating priorities.
  - Building relationships and creating an empathetic, zero-judgment room.
  - Scaffolding authentic learning experiences.
  - Facilitating peer-to-peer inquiry.


# Module 3: Strategies for Training

## Participatory Live Coding
- The gold standard method for teaching computation (The Carpentries model):
  - Instructor types code live on the projector; learners type along simultaneously.
  - Never lecture through static code slides.
- **Live Coding Rules of Thumb:**
  - Enlarge screen font to 18pt–24pt (readable from the back row).
  - Narrate every keystroke, flag, and space before typing.
  - Slow down natural typing speed by at least 50%.
  - Celebrate typos: walk through error diagnosis collaboratively.

## Paired Programming: Driver & Navigator
- Adapted from software engineering to enhance classroom learning:
  - **The Driver:** Hands on the keyboard; types commands and focuses on mechanics.
  - **The Navigator:** Hands off the keys; reads instructions, catches typos, and focuses on logic.
  - **Roles Swap:** Every 20 minutes.
- **Benefits in Low-Resource Classrooms:**
  - Overcomes hardware shortages (2 learners per machine).
  - Catches 80% of typos before hands are raised.
  - Promotes peer discussion and social learning.

## Scaffolded Learning & Faded Examples
- Prevents "blank screen panic" by fading instructional scaffolding in stages:
  1. **Fully Worked Example:** Instructor demonstrates complete command and output.
  2. **Partially Faded Example:** Learners fill in specific missing flags or file paths.
  3. **Heavily Faded Example:** Structural skeleton provided; learners write key logic.
  4. **Independent Task:** Learners write commands from scratch.

## Cognitive Load & The 15-Minute Rule
- Human working memory holds only 4–7 novel chunks of information at once.
- Continuous lecturing leads to cognitive saturation within 15–20 minutes.
- **The 15-Minute Instructional Cycle:**
  - 7–10 minutes: Live coding and concept framing.
  - 3–5 minutes: Active micro-challenge or prediction question.
  - 2 minutes: Debrief and formative sticky-note check.


# Module 4: Elements of Effective Training

## Inclusive Classrooms & Code of Conduct
- Establish clear community expectations before opening the terminal:
  - Enforce a formal **Code of Conduct** prohibiting gatekeeping and condescending language.
  - Ban dismissive phrases: *"That's trivial,"* *"Just read the manual,"* or *"Obviously."*
  - Ensure gender and institutional equity during discussions and hands-on activities.
  - Support non-native English speakers with written glossaries and clear pacing.

## The Human Support Architecture: Roving Helpers
- Computational workshops cannot be taught solo with 20+ students.
- **The Golden Ratio:** 1 roving helper for every 6–8 learners.
- Helpers catch individual syntax bugs so the instructor maintains classroom flow.
- **The "Hands-Off-the-Keyboard" Rule:**
  - Helpers must **never** touch a student's keyboard or mouse.
  - Place hands behind the back; guide verbally.
  - The learner's fingers must type the correction to build genuine self-efficacy.

## Low-Resource Venue & Technical Logistics
- Conduct a rigorous pre-flight audit of the physical space:
  - **Electrical Power:** Bring 4–6 heavy-duty extension power strips (bioinformatics CPU usage drains laptop batteries in 60 minutes!).
  - **Projection:** High-contrast display settings; control window glare.
  - **Audio:** Use a microphone if classroom size exceeds 25 participants.
  - **Connectivity:** Maintain a dedicated instructor mobile hotspot; prepare full offline USB backups.

## Pacing: The Rule of Thirds
- Avoid curriculum bloat—cramming 5 days of content into 2 days guarantees zero retention.
- **The Rule of Thirds Allocation:**
  - **1/3 Instruction:** Participatory live coding and concept framing.
  - **1/3 Guided Practice:** Paired hands-on challenges and active debugging.
  - **1/3 Buffer & Review:** Q&A, diagnostic debrief, helper catch-up, and breaks.
- **The 20% Pruning Rule:** Plan to cut 20% of your planned material; go deeper on fundamentals.

## Gathering Real-Time Feedback
- Never ask: *"Does everyone understand?"* (Shy students will not reply).
- **Two-Color Sticky Notes (Real-time telemetry):**
  - **Green up:** "I completed the exercise successfully."
  - **Red/Pink up:** "I am stuck or have an error; I need a helper."
- **Daily Feedback on Sticky Notes:**
  - 1. What was the most important concept you learned today?
  - 2. What is still muddy or confusing?
  - Address the "muddiest points" first thing the following morning.


# Module 5: Designing Training (Backward Design)

## The Backward Design Framework
- Shift from **Forward Design** (content/tool-driven) to **Backward Design** (competency-driven):
  - **Stage 1: Desired Results:** What should learners know, understand, and be able to do?
  - **Stage 2: Acceptable Evidence:** How will we know they achieved it? (Design the assessment first!).
  - **Stage 3: Learning Experiences:** What instructional steps and datasets lead to that evidence?
- Every slide, command, and exercise must directly support an observable learning outcome.

## Constructing Learner Personas
- Create 1–2 detailed personas representing your audience:
  - **Role & Background:** (e.g. Senior Clinical Microbiologist, MSc Agronomy student).
  - **Computational Baseline:** (e.g. Excel expert, zero command-line experience).
  - **Motivations:** (e.g. analyze 30 bacterial isolates before a thesis deadline).
  - **Constraints:** (e.g. 4 GB RAM Windows laptop, no root access, 2 Mbps shared Wi-Fi).
- Use personas to make curriculum cut decisions objectively.

## Bloom's Taxonomy for Bioinformatics
- Align learning outcomes with explicit cognitive levels:
  - **Remember:** Identify, list, recall syntax.
  - **Understand:** Explain, differentiate, predict.
  - **Apply:** Execute commands, modify parameters, implement workflows.
  - **Analyze:** Diagnose errors, troubleshoot pipelines, filter artifacts.
  - **Evaluate:** Appraise quality reports, validate variants, critique assemblies.
  - **Create:** Construct workflows, automate scripts, design experiments.
- **Eliminate "Zombie Verbs":** Avoid *understand*, *learn*, or *appreciate*. Use observable actions.

## Concept Mapping: Uncovering Hidden Dependencies
- Bioinformatics learning is strictly hierarchical.
- Draw a directed graph connecting concepts to uncover prerequisite bottlenecks:
  - *File Paths* $\rightarrow$ Prerequisite for *Running CLI Tools*.
  - *Standard Streams & Piping* $\rightarrow$ Prerequisite for *Streaming Alignments*.
  - *VCF Format Columns* $\rightarrow$ Prerequisite for *Variant Filtering*.
- Teaching an advanced topic before its computational prerequisite causes classroom paralysis.


# Module 6: Lesson Planning

## The Lesson Planning Arc
- Structure each 60-to-90-minute session purposefully:
  1. **The Motivational Hook (5 mins):** Authentic outbreak or biological challenge.
  2. **Objectives & Framing (5 mins):** Clear statement of what will be built.
  3. **Participatory Demonstration (15–20 mins):** Live-coding core commands.
  4. **Formative Challenge (20–25 mins):** Paired hands-on practice.
  5. **Collective Debrief (10 mins):** Error analysis and output inspection.
  6. **Cognitive Closure (5 mins):** Key takeaways and preview of next module.

## The Double-Time Rule
- **The Instructor Fallacy:** *"This task takes me 3 minutes, so students need 5 minutes."*
- **The Classroom Reality:** Novice learners take **3x to 4x longer** than experts:
  - Locating windows and switching between browser and terminal.
  - Hunting for special keyboard characters (`~`, `|`, `\`, `_`).
  - Slower typing speed and syntax typos.
  - Hardware execution latencies on modest laptops.
- Always budget at least double to triple your personal execution time.

## Delivery Notes & Contingency Planning
- Prepare a podium cheatsheet containing:
  - Exact commands and expected terminal outputs.
  - Pacing time checkpoints and specific helper alert warnings.
- **The Contingency Matrix (Plans B and C):**
  - *Internet failure:* Distribute offline USB drive mirrors.
  - *Power blackout:* Run on laptop batteries; switch to whiteboard conceptual activities.
  - *Tool crash on Windows:* Pair student with a neighbor or provide pre-computed outputs.
  - *Long pipeline run:* Kill job; load pre-computed "here is one I prepared earlier" data.


# Module 7: Assessment Strategies

## Assessment as a Diagnostic Compass
- Formative assessment is **assessment for learning**, not evaluation of grading.
- Low-stakes, continuous diagnostics identify broken mental models in real time.
- Traditional grading induces anxiety in adult professionals; formative feedback builds competence.
- **The Chef Metaphor:**
  - When the chef tastes the soup during cooking: *Formative assessment*.
  - When the customer eats the soup: *Summative assessment*.

## Diagnostic Multiple-Choice Questions (MCQs)
- Design MCQs where every wrong answer (**distractor**) reveals a specific misconception:
  - *Stem:* "Which command displays the first 10 reads in a FASTQ file?"
  - *Correct Answer:* `head -n 40 sample.fastq` (10 reads $\times$ 4 lines).
  - *Distractor 1:* `head -n 10 sample.fastq` (Diagnoses: confuses lines with reads).
  - *Distractor 2:* `wc -l sample.fastq` (Diagnoses: confuses line count with display).
- **Peer Instruction (Eric Mazur Technique):**
  - Individual vote $\rightarrow$ Think-Pair-Share with a neighbor $\rightarrow$ Re-vote $\rightarrow$ Debrief.

## Parson's Problems: Jumbled Code
- Scrambled lines of code that learners arrange in correct execution order.
- **Pedagogical Advantages:**
  - Evaluates algorithmic logic and dependency sequencing.
  - Completely eliminates syntax typos, missing quotation marks, and spelling frustration.
  - Highly engaging micro-exercise for beginners.
- Example: Arranging steps from raw FASTQ trimming $\rightarrow$ BWA alignment $\rightarrow$ SAM sorting $\rightarrow$ BCFtools variant calling.

## Zero-Bandwidth Classroom Assessment
- Avoid relying on online polling tools (Mentimeter, Slido, Kahoot) that require internet:
  - **Chest-Level Finger Voting:** Students display 1, 2, 3, or 4 fingers against their chest simultaneously on count of three.
  - **Mini-Whiteboards / Paper Slips:** Write a command or path and hold it up.
  - **Authentic Final Deliverables:**
  - Mini-projects demonstrating real-world competence (e.g. producing an outbreak report or annotated variant table).


# Module 8: Responsible Use of AI in Bioinformatics

## Generative AI: The 24/7 Virtual Tutor
- Large Language Models (LLMs) offer immense potential in low-resource environments:
  - Virtual 24/7 tutor when experienced local mentors are unavailable.
  - Instant explanation of cryptic Unix and compiler error messages.
  - Drafting initial Bash, Python, and R boilerplate code.
  - Formatting complex regular expressions and data wrangling commands.

## Critical Risks & Prompt Don't-Dos
- **Common AI Hazards in Bioinformatics:**
  - **Flag Hallucination:** Models invent non-existent flags (e.g. `--min-coverage` in BCFtools) or mix competing tools.
  - **Deprecated Syntax:** Recommending obsolete software (TopHat2, Python 2) from historical web training data.
  - **The Copy-Paste Blindspot:** Short-circuiting cognitive struggle leaves students unable to troubleshoot on real data.
- **Three Strict Don't-Dos for AI Prompts:**
  1. Never paste unconsented Patient Health Information (PHI).
  2. Never paste unconsented raw human DNA sequences.
  3. Never expose sensitive pathogen outbreak data before public health clearance.

## The "Trust but Verify" Protocol & Course AI Policy
- **The 4-Step Verification Protocol:**
  1. *Manual Audit:* Verify command flags with `tool --help | grep flag`.
  2. *Dry Run:* Execute on a 1,000-read micro-dataset first.
  3. *Structural Audit:* Verify output dimensions (`wc -l`, `head`).
  4. *Biological Sanity Check:* Do results align with biological reality?
- **Classroom AI Policy:**
  - ✅ Permitted: Explaining error logs, understanding syntax, brainstorming tools.
  - ❌ Restricted: Generating code during initial mental-model construction; submitting unverified AI code.


# Part 2: Building Practical & Scaleable Bioinformatics Training

# Module 9: Open Educational Resources (OER)

## The "Don't Reinvent the Wheel" Imperative
- Authoring a bioinformatics curriculum from scratch takes hundreds of hours.
- Open Educational Resources (OER) provide peer-reviewed, classroom-tested materials.
- **Your Superpower as a Trainer:** Curating, contextualizing, and adapting existing resources for your local community.
- **The 5R Permissions (David Wiley):**
  - **Retain:** Make and own copies (offline USB storage).
  - **Reuse:** Use unaltered in workshops.
  - **Revise:** Adapt, translate, and modify datasets.
  - **Remix:** Combine modules from different sources.
  - **Redistribute:** Share adapted versions openly.

## Creative Commons & The FAIR Training Principles
- **Licensing Guidelines:**
  - Favor **CC BY** (Attribution) and **CC BY-SA** (ShareAlike).
  - Caution with **CC BY-NC** (complicates cost-recovery registration fees).
  - **Avoid CC BY-ND** (NoDerivatives prohibits dataset adaptation or translation!).
- **FAIR Principles for Training Materials:**
  - **Findable:** Tagged with structured metadata; deposited in TeSS / Zenodo with DOIs.
  - **Accessible:** Open access without paywalls; downloadable offline copies.
  - **Interoperable:** Plain-text Markdown/Quarto formats; standard biological ontologies.
  - **Reusable:** Explicit open licensing, defined prerequisites, and micro-datasets.

## Major Repositories & Contextualization
- **Key OER Sources:**
  - **The Carpentries:** Modular, evidence-based Unix, Git, Python, R, and Genomics lessons.
  - **Galaxy Training Network (GTN):** 400+ tutorials with integrated workflows and data.
  - **H3ABioNet:** Curricula tailored for distributed, bandwidth-constrained African classrooms.
- **The Contextualization Imperative:**
  - Strip out western infrastructure assumptions (live gigabyte downloads, HPC clusters).
  - Localize the biology: replace model organisms (mice, yeast) with regional crops (cassava, sorghum) or endemic pathogens (malaria, TB, cholera, AMR).


# Module 10: Containerisation

## Solving "Dependency Hell"
- Bioinformatics software has complex, brittle dependency chains.
- Traditional workshop installations across 25 mixed-OS laptops lose Day 1 to troubleshooting.
- **Containers:** Package software, dependencies, system libraries, and configuration into a standardized, isolated execution box.
- **Containers vs. Virtual Machines:**
  - VMs virtualize hardware and run a full guest OS kernel (heavy, slow, high RAM usage).
  - Containers share the host kernel (lightweight, sub-second launch, native speed).

## Docker vs. Singularity / Apptainer
- **Docker:**
  - Dominates industry and personal cloud development.
  - Requires background daemon and root/sudo access (prohibited on shared academic HPC).
  - Filesystems isolated by default (requires explicit `-v` volume mounting).
- **Singularity / Apptainer:**
  - The standard for scientific computing and academic HPC.
  - Runs entirely as unprivileged user (safe on shared clusters).
  - Mounts current directory and home directory automatically.
  - Packaged into a single standalone file (`.sif`)—easy to copy via USB.

## Container Strategies in Low-Resource Classrooms
- **The Bandwidth Collapse Trap:**
  - 25 students running `docker pull` on 1.5 GB images simultaneously takes 8+ hours on 10 Mbps Wi-Fi!
- **Offline Distribution Protocols:**
  - Instructor pre-downloads and packages containers before the workshop.
  - Docker: `docker save image -o image.tar` $\rightarrow$ Distribute via USB $\rightarrow$ `docker load`.
  - Apptainer: Copy the `.sif` file directly via USB flash drives.
- **BioContainers:** Open community repository providing pre-built images for all Bioconda tools.


# Module 11: Software Installation

## How the Operating System Discovers Programs
- **The `$PATH` Variable:** Colon-separated list of directories searched when a command is typed.
  - If a binary is in `~/Downloads`, typing its name produces `command not found`.
  - Fix: Move to `~/.local/bin` or add folder to `$PATH` in `~/.bashrc`.
- **Permissions:** Downloaded files require execute permissions (`chmod +x binary`).
- **The `./` Notation:** Explicitly instructs the shell to execute a binary in the current directory.

## Modern Package Management: Mamba & Micromamba
- **Classic Conda Limitation:** Python-based SAT solver consumes 2–4 GB RAM, causing OOM crashes on modest laptops.
- **Mamba & Micromamba Solution:** Fast C++ solver (`libsolv`) resolves environments in seconds with minimal memory.
- **Never Install into the Base Environment:** Always create isolated environments per project (`mamba create -n project_env`).
- **Offline Environment Sharing with `conda-pack`:**
  - Bundle full environments into a `.tar.gz` archive on a connected machine.
  - Unpack on student laptops via USB—zero network traffic required!

## Pre-Course Verification & Installation Clinics
- Never waste Day 1 morning on software installation.
- Host virtual drop-in "Installation Clinics" 2–3 days prior to the course.
- Provide an automated shell pre-flight verification script (`preflight_check.sh`) to confirm all tools are in `$PATH` before arrival.


# Module 12: Cloud-based Computing

## Cloud Models for Low-Resource Settings
- Cloud transforms compute from expensive physical infrastructure into an elastic utility:
  - **SaaS (Galaxy):** Free, point-and-click GUI; pre-allocated quotas; ideal for wet-lab novices.
  - **PaaS (Google Colab / Terra):** Interactive Jupyter notebooks; free GPU/TPU access.
  - **IaaS (AWS / GCP / Azure):** Raw virtual machines; full root control for custom pipelines.
- **The Core Principle: Data Locality:**
  - *"Bring the compute to the data, not the data to the compute."*
  - Run compute in the cloud region where public data (SRA, ENA) resides; download only lightweight summary tables.

## Managing Low-Resource Cloud Barriers
- **Bandwidth Asymmetry:** Uploading 50 GB over a 2 Mbps connection takes 55 hours. Use data locality.
- **Currency & Credit Card Restrictions:** Public universities often lack international cards. Use academic grants (AWS Cloud Credits for Research) or free platforms (Galaxy).
- **Preventing "Bill Shock":**
  - Use Spot / Preemptible instances for 70–90% cost savings.
  - Configure automated budget alarms and CPU-idle auto-shutdown scripts.
- **Classroom Architectures:** Use the Galaxy Training Network (GTN) or GitHub Codespaces (60 free core-hours/month) to avoid requiring student credit cards.


# Module 13: Using an HPC or Server for Training

## The Server as a Pedagogical Shield
- **Eliminating the "Installation Abyss":**
  - Equalizes heterogeneous, low-spec learner laptops (2–4 GB RAM, Windows 7/10/11, locked hospital laptops).
  - Provides a single, uniform Linux environment with pre-configured tools, paths, and reference genomes.
- **Topologies for Low-Resource Venues:**
  - **In-Room Local Server (Offline LAN):** Portable mini-PC/workstation + local Wi-Fi router. *Zero internet required!*
  - **Institutional / Regional HPC:** High compute capacity, but requires dedicated SLURM training reservations/QoS.
  - **Cloud Training VM:** Disposable 32-core IaaS instance; requires reliable internet and billing controls.

## Defending Against the "Thundering Herd"
- **The Classroom Crisis:** 25 students press [Enter] at the same second $\rightarrow$ CPU/RAM saturation $\rightarrow$ OOM crash.
- **Standalone Server Safeguards:**
  - Hard per-user limits using `cgroups` v2 and `/etc/security/limits.conf` (restrict `nproc`, `as`, `maxlogins`).
  - Enforce thread limits: wrapper scripts that intercept and cap flags (e.g. max `-t 2`).
- **HPC / SLURM Safeguards:**
  - Dedicated reservation (`--reservation=workshop2026`) and QoS (`MaxJobsPerUser=2`).
  - Automated watchdog to prevent students from executing heavy compute on the login node.
- **Storage Hygiene:** Pre-build reference indices in a shared read-only directory (`chmod 555 /shared/`); enforce disk quotas on `/home`.

## Low-Friction Access & Live Monitoring
- **Browser-Based Access Over HTTPS (Port 443):**
  - Use **JupyterHub**, **RStudio Server**, or **`ttyd`** web terminals instead of raw SSH.
  - *Benefits:* Zero client installation, traverses firewalls blocking Port 22, and persists sessions if Wi-Fi flickers.
  - If using raw SSH: auto-launch `tmux` in `.bashrc` so disconnects don't terminate running pipelines.
- **The Trainer's Operations Cockpit:**
  - Keep a secondary screen with `htop` / `glances` / `squeue` to track load average, swap churn, and I/O wait (`wa`).
- **Contingency Tier 2 & 3:**
  - Always carry "Cooking Show" pre-computed outputs and standalone micro-datasets on USB flash drives.


# Module 14: Utilising Micro-datasets

## The Classroom Runtime Trap
- Full-scale research datasets (40 GB FASTQs, multi-hour runtimes, 64 GB RAM requirements) destroy live training:
  - Students stare at frozen screens for hours; active learning stops.
  - Typos discovered hours later cause immense frustration.
  - Modest laptops crash or overheat.
- **Micro-datasets:** Realistically engineered datasets running in **seconds** on basic hardware while preserving biological format and integrity.

## Micro-Dataset Engineering Strategies
1. **Random Downsampling (`seqtk sample -s 100`):** Rapid read subsetting. Must use identical random seeds for paired-end synchronization!
2. **Locus-Specific Extraction:** Slicing reads mapping to a single gene of interest (e.g. *rpoB* in *M. tuberculosis* or *mecA* in *S. aureus*). Keeps file size under 2 MB while preserving 50$\times$ depth for authentic variant calling!
3. **Small Model Organisms:** Slicing human Chr21/22 or using viral/plasmid genomes (SARS-CoV-2 assembles in 45 seconds).
4. **Synthetic Simulation:** Generating ground-truth error profiles with simulators (Badread, InSilicoSeq).

## The "Cooking Show" Pedagogical Model
- **Step 1 (The Live Recipe):** Learners run micro-datasets live in class to understand syntax, input/output flags, and intermediate files.
- **Step 2 ("Here is one I baked earlier"):** Transition immediately to pre-computed output tables from full cohorts for downstream statistical interpretation and PCA/pathway modeling.
- **Managing Expectations:** Always remind students that full research datasets take longer and require dedicated servers.


# Module 15: Authoring Course Materials

## The Open Authoring Stack (Quarto & Markdown)
- **Why Move Away from Word & PowerPoint?**
  - Proprietary binary formats lack true Git version control.
  - Inflexible: updating a command requires manual edits across multiple slide decks and docs.
- **The Plain-Text Revolution (Quarto):**
  - Single-source authoring: write plain-text Markdown once.
  - Compiles automatically to interactive HTML websites, standalone PDFs, and PowerPoint slides (`.pptx`).
  - Completely free, cross-platform, and open-source.

## Visual Scaffolding & Callout Blocks
- Structure lessons using visually distinct callout blocks to manage cognitive load:
  - **`callout-tip` (Green):** Framing Learning Objectives and Key Points summaries.
  - **`callout-note` (Blue):** In-depth biological analogies and conceptual background.
  - **`callout-warning` (Orange):** Critical pitfalls, permanent deletion warnings, and memory traps.
  - **`callout-exercise`:** Numbered active learning challenges with collapsible solutions.

## Free Web Hosting & Offline-First Bundles
- **Zero-Cost Web Publishing with GitHub Pages:**
  - Automated continuous deployment via GitHub Actions on every `git push`.
  - Zero institutional server costs, zero sysadmin maintenance, global CDN speed.
- **Offline-First Delivery in Low-Resource Venues:**
  - Quarto compiles into a self-contained static folder (`_site/`).
  - Zip the website and distribute via USB drives ("sneakernet").
  - Students browse the full course site locally in any browser without internet!

## Academic Credit & Scholarly Archiving
- Treat curriculum development as a recognized scholarly research output:
  - **`CITATION.cff`:** Place in repository root so GitHub generates automatic APA/BibTeX citation buttons.
  - **Zenodo DOI Integration:** Mint persistent Digital Object Identifiers (DOIs) indexed in Google Scholar.
  - **Open Licensing:** Attach CC BY 4.0 in `LICENSE.md` to legally protect attribution while enabling global reuse.


# Module 16: Case Studies in Curriculum Evaluation

## Case Study 1: Intro to Unix Shell (Design & Analogies)
- **Evaluating `cambiotraining.github.io/unix-shell/`:**
  - Adapted from The Carpentries; clear sequential progression (`pwd` $\rightarrow$ `cd` $\rightarrow$ pipes $\rightarrow$ scripts).
  - Graded 3-tier difficulty exercises (Level 1–3 stars) facilitate active self-assessment and helper triage.
- **Evaluating Common Computing Analogies:**
  - *Inverted Tree:* Helpful for hierarchy; risk of confusing branch depth with execution order.
  - *"You Are Here" Directory:* Clarifies relative paths; confusing when redirecting output across directories.
  - *Pipes as Plumbing:* Good for memory streams; students often mistakenly think pipes save data to disk.
  - *Wildcards as Jokers:* Memorable for globbing; learners easily confuse with regex.

## Case Study 1: Omissions & Low-Resource Realities
- **Gaps Identified in the Introductory Shell Curriculum:**
  - *Non-Biological Abstract Data:* Files like `creatures` and `haiku.txt` cause cognitive friction for adult wet-lab researchers.
  - *Missing Defensive Scripting:* Omits `set -euo pipefail` and defensive path validation.
  - *No Session Resilience:* Lacks `tmux` / `screen`; dropped SSH sessions terminate running pipelines.
  - *Format Traps:* No warning against opening massive tables in Excel or running `head` on binary/gzipped files.
  - *Windows CRLF Issues:* Missing diagnosis for Windows carriage return (`\r\n`) interpreter errors.

## Case Study 2: Bacterial Genomics (Suitability & Adaptations)
- **Evaluating `cambiotraining.github.io/bacterial-genomics/`:**
  - *High Biological Relevance:* Targets priority pathogens (*M. tuberculosis*, *S. aureus*, *S. pneumoniae*) and AMR.
  - *Infrastructural Mismatch:* Heavy Nextflow pipelines, live SRA/ENA downloads, and 16–32 GB RAM requirements trigger failure on standard laptops and low-bandwidth connections.
- **Essential Adaptations for Low-Resource Classrooms:**
  - **Offline USB Distribution:** Replace live downloads with pre-staged USB datasets.
  - **Targeted Micro-Datasets:** 2 MB locus-specific slices (*rpoB*, *mecA*) align in seconds on 4 GB RAM.
  - **"Cooking Show" Pattern:** Syntax test on micro-data $\rightarrow$ distribute pre-computed assemblies/trees for downstream interpretation.
  - **Two-Tier Pedagogy:** Single-tool CLI mechanics (`fastp`, `bwa`) taught before Nextflow orchestration.
  - **In-Room Centralized Server:** Run compute on a local offline server accessed via web terminals.


# Part 3: Design and Sustain your Training

# Module 17: Design Your Training

## The Training Plan: 7 Core Components
- Your task is to transition from student to **training architect**:
  - Deliverable: A practical, peer-reviewed training plan ready for delivery at your home institution.
- **The 7 Core Components:**
  1. *Context & Institutional Profile:* Venue realities, power, bandwidth, and device access.
  2. *Target Learner Persona:* Background, baseline, motivations, and computational pain points.
  3. *Measurable Outcomes:* 3–5 observable Bloom's taxonomy action verbs.
  4. *Curriculum & Tool Selection:* Right-sized for constraints and local relevance.
  5. *Instructional Delivery Model:* Live coding, driver-navigator pairs, roving facilitators.
  6. *Technical & Logistics Plan:* Micro-datasets, user-space tools, offline Plan B matrix.
  7. *Assessment & Evaluation Strategy:* Formative telemetry (stickies/MCQs) + authentic final task.

## The Presentation Pitch & Tuning Protocol
- **The Pitch Format (10 minutes + 3–4 minutes Q&A):**
  - Slide 1: Local Need, Institution & Venue Context.
  - Slide 2: The Learner Persona.
  - Slide 3: Measurable Learning Outcomes.
  - Slide 4: Curriculum Architecture & Pacing (Rule of Thirds).
  - Slide 5: Technical Plan, Micro-datasets & Plan B Matrix.
  - Slide 6: Final Assessment Deliverable & Impact Plan.
- **The Tuning Protocol (Structured Peer Review):**
  - *Warm Feedback:* Affirmations of strong design choices and creative adaptations.
  - *Cool Feedback:* Constructive questions regarding pacing, cognitive load, and contingency fallbacks.


# Module 18: Building Communities of Practice

## The Post-Workshop Crisis & The Lone Bioinformatician
- **The Post-Workshop Reality:**
  - Trainees return home with high enthusiasm, but face departmental isolation.
  - Without ongoing mentorship, code review, or peer support, skill decay reaches 100%.
- **The Community of Practice (CoP) Solution (Lave & Wenger):**
  - Learning is fundamentally social and situated in practice.
  - Sustained capacity requires peer networks that support active problem-solving long after the workshop ends.

## Lightweight Grassroots Community Formats
- Start small and informal—no institutional budget required:
  - **Hacky Hours / Coding Clinics:** 1 hour weekly; bring your laptop, broken code, and coffee; troubleshoot together.
  - **Carpentries Study Groups:** Bi-weekly shared progression through open online tutorials.
  - **Methods Journal Clubs:** Dissecting the computational methods section of recent papers.
  - **Bug-Busting Hackathons:** Half-day team sprints on shared departmental data.

## Linking Grassroots to Regional Networks
- Break institutional isolation by connecting local clubs to wider federations:
  - **Pan-African Networks:** H3ABioNet nodes, African Society for Bioinformatics and Computational Biology (ASBCB), ISCB RSGs.
  - **Global Alliances:** The Carpentries Community, Galaxy Community (Galaxy Africa), EMBnet, APBioNET.
- **Succession Planning & Sustainability:**
  - Avoid the "Founder's Trap": distribute roles from Day 1 (scheduling, moderation, note-taking).
  - Secure permanent room bookings and departmental recognition.

## Summary & Continuing the Journey
- **Key Takeaways:**
  - Teaching bioinformatics in low-resource settings requires intentional pedagogy, empathy, and technical resourcefulness.
  - Backward design and active learning turn technical obstacles into educational triumphs.
  - Micro-datasets, offline workflows, and peer communities empower learners regardless of connectivity.
- **Your Next Steps:**
  - Refine your training plan based on peer feedback.
  - Connect with regional networks (H3ABioNet, The Carpentries, Galaxy GTN).
  - Share your micro-datasets and materials openly to strengthen the global commons.
