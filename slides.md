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
- **Capstone Outcome:** A complete, peer-reviewed training plan ready for delivery at your home institution.

## The Low-Resource Reality
- Infrastructure constraints are systemic, not accidental:
  - Unstable power grids and frequent blackouts.
  - Slow, expensive, or intermittent internet bandwidth.
  - Modest learner hardware (e.g., 4–8 GB RAM consumer laptops).
  - Lack of dedicated institutional High Performance Computing (HPC).
  - Absence of formal computational curricula in life-science degrees.
- **Key Insight:** Standard Western training models must be adapted—not simply transplanted—to succeed.

## Course Structure: Three Core Pillars
1. **Part 1: How to Teach Bioinformatics**
   - Andragogy, live coding, pair programming, effective environments, backward design, lesson planning, and assessment.
2. **Part 2: What to Teach**
   - Open educational resources, computational concepts, UNIX, containers, installation, cloud, HPC, micro-datasets, and data interpretation.
3. **Part 3: Design Your Training**
   - Capstone design sprint, peer review, and participant pitch presentations.


# Part 1: How to Teach Bioinformatics

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

## The "Double Hurdle" in Training
- Adult life scientists face two steep learning curves simultaneously:
  1. **New Conceptual Complexity:** Abstract algorithms (de Bruijn graphs, Bayesian phylogenetics, statistical models).
  2. **New Technical Modality:** Text-only terminals, file permissions, coordinate paths, and cryptic error messages.
- Presenting both simultaneously triggers cognitive overload.
- **Pedagogical Strategy:** Separate the hurdles—build spatial computational models before introducing complex biological algorithms.


# Module 2: Adult Learning Principles (Andragogy)

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

## Knowles' Six Assumptions in Bioinformatics
1. **Need to Know:** Explain *why* a tool matters before demonstrating syntax.
2. **Self-Concept:** Treat learners as autonomous peers, not passive students.
3. **Prior Experience:** Anchor computational steps to physical wet-lab assays (e.g., quality scores $\rightarrow$ gel band clarity).
4. **Readiness to Learn:** Focus on data and tools directly relevant to their research.
5. **Orientation to Learning:** Organize around scientific questions, not tool manuals.
6. **Motivation:** Cultivate problem-solving confidence and scientific autonomy.

## The Expert-Novice Paradox & Psychological Safety
- Trainees are accomplished professionals (postdocs, PIs, senior clinicians).
- Facing a terminal error (`command not found`) makes them feel reduced to novices.
- **Common Reactions:** Imposter syndrome, terminal anxiety, and silent withdrawal.
- **Instructor Intervention:**
  - Create psychological safety on Day 1.
  - Explicitly normalize syntax errors as the natural language of coding.
  - Reaffirm domain expertise: *"Without your biology, bioinformatics has nothing to compute."*

## From Teacher to Learning Facilitator
- **Traditional Teacher:** "Sage on the Stage" transmitting prescribed content.
- **Learning Facilitator:** "Guide on the Side" managing the learning environment.
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

## Formative Telemetry: Sticky Notes & Minute Papers
- Never ask: *"Does everyone understand?"* (Shy students will not reply).
- **Two-Color Sticky Notes (Real-time telemetry):**
  - **Green up:** "I completed the exercise successfully."
  - **Red up:** "I am stuck or have an error; I need a helper."
- **One-Minute Papers (End-of-day synthesis):**
  - 1. What was the most important thing you learned today?
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

## The 6-Stage Lesson Arc
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

## Instructor Delivery Notes & Contingency Planning
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
  - **Authentic Capstone Deliverables:**
  - Mini-projects demonstrating real-world competence (e.g. producing an outbreak report or annotated variant table).

# Module 8: Authoring Course Materials

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

## Making Educational Materials Citable
- Treat curriculum development as a recognized scholarly research output:
  - **`CITATION.cff`:** Place in repository root so GitHub generates automatic APA/BibTeX citation buttons.
  - **Zenodo DOI Integration:** Mint persistent Digital Object Identifiers (DOIs) indexed in Google Scholar.
  - **Open Licensing:** Attach CC BY 4.0 in `LICENSE.md` to legally protect attribution while enabling global reuse.


# Part 2: What to Teach

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


# Module 10: Core Computational Concepts

## Hardware Mental Models: The Kitchen Analogy
- **Secondary Storage (SSD / HDD) = The Pantry:**
  - Large capacity (500 GB – 2 TB); non-volatile; relatively slow access.
- **RAM (Working Memory) = The Cutting Board:**
  - Fast, immediate workspace; limited capacity (4–16 GB); volatile (erased on power loss).
  - Tools must load data onto the cutting board to work on it!
- **CPU (Processor) = The Chef:**
  - Executes instructions; multiple cores = multiple chefs working in parallel.
  - Over-subscribing threads (`-t 16` on a 4-core laptop) slows processing down!

## Realities in Low-Resource Computing
- **The Out-Of-Memory (OOM) Crash:**
  - Loading a 10 GB genome index onto an 8 GB cutting board causes the OS kernel to kill the process (`Killed` / Exit code 137).
  - Teach learners to recognize memory exhaustion vs. software bugs.
- **Disk Thrashing (Swapping):**
  - Overflowing RAM forces the OS to use slow hard drives as memory, freezing the computer.
- **Filesystem Hierarchy & Coordinates:**
  - Command line requires explicit coordinate addressing (absolute vs. relative paths).
  - Tab-completion is essential: guarantees file existence and eliminates typos.

## Data Representation & Operating System Friction
- **Plain Text vs. Binary:**
  - Plain text (FASTA, FASTQ, SAM, VCF): Human-readable, streamable with CLI tools.
  - Binary (BAM, BCF, index files): Compact, fast random access, unreadable in text editors.
- **The Windows CRLF Line Ending Trap:**
  - Windows text editors add hidden Carriage Returns (`\r\n`), causing `/bin/bash^M: bad interpreter` errors on Linux.
  - Inspect with `file script.sh` and fix with `dos2unix script.sh`.
- **Streams & Piping:**
  - Connect STDOUT to STDIN with `|` to process data in memory without writing massive intermediate files to slow laptop disks.


# Module 11: Practical UNIX

## The Bioinformatician's Swiss Army Knife
- **Why UNIX Excels on Modest Hardware:**
  - Extremely lightweight OS overhead (~15 MB RAM vs. heavy graphical interfaces).
  - Processes multi-gigabyte files line-by-line without loading entire files into memory.
  - Free, open-source, and universal across servers, clouds, and clusters.
- **Core Navigation & Hygiene:**
  - `pwd`, `ls -lh`, `cd ..`, `mkdir -p`, `cp -r`, `mv`.
  - Defensive computing: `rm` has no recycle bin—teach temporary trash directories.
  - Avoid spaces and special characters in file naming.

## Inspecting & Wrangling Genomic Data
- **Never open large biological files in Microsoft Excel:**
  - Excel row truncation (1,048,576 rows max) silently discards reads!
  - Date auto-conversion corrupts gene names (*SEPT4* $\rightarrow$ *04-Sep*).
- **Inspection Tools:** `head`, `tail`, `less -S` (chops long lines), `wc -l`.
- **Wrangling Matrix:**
  - `grep`: Search headers and filter metadata (`grep -v "^#"`).
  - `cut`: Extract tab-delimited columns from BED/VCF files.
  - `sort` & `uniq -c`: Generate frequency counts and summarize categories.
  - `awk`: Conditional numerical filtering (e.g. `awk '$6 > 30' file.vcf`).

## Automation & Session Resilience
- **Defensive Scripting Header:**
  - Always teach `set -euo pipefail` to catch errors early and prevent silent script failure.
  - Automate multi-sample processing using `for` loops and `basename`.
- **Surviving Power Cuts & Dropped Connections:**
  - When working over SSH on remote machines, Wi-Fi drops kill the terminal session!
  - Teach **`tmux`** (terminal multiplexer): detach (`Ctrl-b d`) and reattach (`tmux attach`).
  - Background execution with `nohup command > log.txt 2>&1 &`.


# Module 12: Containerisation

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


# Module 13: Software Installation

## How the OS Discovers Programs
- **The `$PATH` Variable:** Colon-separated list of directories searched when a command is typed.
  - If a binary is in `~/Downloads`, typing its name produces `command not found`.
  - Fix: Move to `~/.local/bin` or add folder to `$PATH` in `~/.bashrc`.
- **Permissions:** Downloaded files require execute permissions (`chmod +x binary`).
- **The `./` Notation:** Explicitly instructs the shell to execute a binary in the current directory.

## Modern Package Management: Mamba & Micromamba
- **Classic Conda Limitation:** Python-based SAT solver consumes 2–4 GB RAM, causing OOM crashes on modest laptops.
- **Mamba & Micromamba Solution:** Fast C++ solver (`libsolv`) resolves environments in seconds with minimal memory.
- **The "Never Base" Rule:** Never install tools into the `base` environment; always create isolated environments per project.
- **Offline Environment Sharing with `conda-pack`:**
  - Bundle full environments into a `.tar.gz` archive on a connected machine.
  - Unpack on student laptops via USB—zero network traffic required!

## Pre-Course Verification & Clinics
- Never waste Day 1 morning on software installation.
- Host virtual drop-in "Installation Clinics" 2–3 days prior to the course.
- Provide an automated shell pre-flight verification script (`preflight_check.sh`) to confirm all tools are in `$PATH` before arrival.


# Module 14: Cloud-based Bioinformatics

## Cloud Models for Low-Resource Settings
- Cloud transforms compute from expensive physical infrastructure into an elastic utility:
  - **SaaS (Galaxy):** Free, point-and-click GUI; pre-allocated quotas; ideal for wet-lab novices.
  - **PaaS (Google Colab / Terra):** Interactive Jupyter notebooks; free GPU/TPU access.
  - **IaaS (AWS / GCP / Azure):** Raw virtual machines; full root control for custom pipelines.
- **The Core Architectural Principle: Data Locality:**
  - *"Bring the compute to the data, not the data to the compute."*
  - Run compute in the cloud region where public data (SRA, ENA) resides; download only lightweight summary tables.

## Managing Low-Resource Cloud Barriers
- **Bandwidth Asymmetry:** Uploading 50 GB over a 2 Mbps connection takes 55 hours. Use data locality.
- **Currency & Credit Card Restrictions:** Public universities often lack international cards. Use academic grants (AWS Cloud Credits for Research) or free platforms (Galaxy).
- **Preventing "Bill Shock":**
  - Use Spot / Preemptible instances for 70–90% cost savings.
  - Configure automated budget alarms and CPU-idle auto-shutdown scripts.
- **Classroom Architectures:** Use the Galaxy Training Network (GTN) or GitHub Codespaces (60 free core-hours/month) to avoid requiring student credit cards.


# Module 15: Using an HPC or Server for Training

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


# Module 16: Utilising Micro-datasets

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


# Module 17: Data Interpretation

## Beyond the Green Checkmark
- **The Pipeline Completion Fallacy:** A pipeline printing `Exit code 0` and generating a 20,000-row VCF is not the end of science—it is the beginning.
- In low-resource settings with limited wet-lab validation budgets, computational interpretation must be exceptionally rigorous.
- **Multi-Stage Quality Control:**
  - Raw reads: Phred scores ($Q20$ vs $Q30$), adapter contamination.
  - Alignments: Depth vs. breadth of coverage (need 20–30$\times$ depth for clinical variant calls).
  - Assemblies: N50 contig length combined with BUSCO biological gene completeness.
  - Variants: Ti/Tv ratios and depth filters.

## Guarding Against Technical Artifacts
- **The Unrecoverable Batch Effect:** Confounded study designs (e.g. cases extracted on Monday, controls on Friday) cannot be fixed by bioinformatics!
- **Multiple Testing Correction:**
  - Testing 20,000 genes at $p < 0.05$ yields 1,000 false positive discoveries by random chance.
  - Use Benjamini-Hochberg False Discovery Rate (FDR $< 0.05$).
  - Evaluate Volcano plots: both statistical significance ($-\log_{10} p$) and biological effect size ($\log_2 \text{FC}$).
- **Human-in-the-Loop Visual Validation:**
  - Inspect candidate mutations in IGV (check mapping quality, read depth, and strand bias).
  - Use exploratory PCA to spot sample swaps before differential modeling.



# Module 18: Responsible Use of AI in Bioinformatics

## The "Virtual Mentor" in Low-Resource Settings
- **The Lone Bioinformatician Challenge:**
  - In isolated institutions, researchers lack local mentors and senior code reviewers.
  - LLMs act as a 24/7 personal tutor: explaining cryptic error logs, writing boilerplate scripts, and demystifying flags.
- **The High-Risk Pitfalls:**
  - **Flag Hallucination:** Models invent non-existent flags (e.g. `--min-coverage` in BCFtools) or mix competing tools.
  - **Deprecated Syntax:** Recommending obsolete software (TopHat2, Python 2) from historical web training data.
  - **The Copy-Paste Blindspot:** Short-circuiting cognitive struggle leaves students unable to troubleshoot on real data.

## Ethics, Sovereignty & The "Trust but Verify" Protocol
- **Strict Ethical Red Lines for AI Prompts:**
  - Never paste unconsented patient health information (PHI) or identifiable clinical metadata.
  - Never upload raw human genomic sequences to public commercial cloud chatbots.
  - Never expose unreleased pathogen outbreak assemblies before official clearance.
- **The "Trust but Verify" Protocol:**
  - 1. Check the binary manual (`tool --help | grep flag`). Does the option exist?
  - 2. Dry run on a micro-dataset first.
  - 3. Audit output dimensions (`wc -l`, `head`).
  - 4. Biological sanity check.
- **Workshop AI Policy:** Encourage for explaining errors; restrict during foundational mental-model construction.


# Part 3: Design and Sustain your Training

# Module 19: Capstone Design Project

## The Capstone Design Challenge
- Your task is to transition from student of pedagogy to **training architect**.
- Deliverable: A fully developed, resource-resilient workshop proposal ready for implementation at your home institution.
- **The 7 Core Components:**
  1. Context & Venue Profile (infrastructure realities).
  2. Target Learner Persona (background, baseline, pain points).
  3. Measurable Learning Outcomes (Bloom's action verbs).
  4. Curriculum & Tool Selection (justified for local relevance).
  5. Instructional Delivery Model (live coding, pair programming).
  6. Technical Logistics & Contingency Plan B (micro-data, offline).
  7. Assessment & Impact Strategy (formative checks, capstone task).

## The Presentation Pitch & Tuning Protocol
- **The Pitch Format (10 minutes):**
  - Slide 1: Local Need, Institution & Venue Context.
  - Slide 2: The Learner Persona.
  - Slide 3: Measurable Learning Outcomes.
  - Slide 4: Curriculum Architecture & Pacing (Rule of Thirds).
  - Slide 5: Technical Plan, Micro-datasets & Plan B Matrix.
  - Slide 6: Authentic Assessment Deliverable & Impact Plan.
- **The Tuning Protocol (Peer Evaluation):**
  - *Warm Feedback:* Affirmations of strong design choices and creative adaptations.
  - *Cool Feedback:* Inquiries regarding pacing, cognitive load, and contingency fallbacks.


# Module 20: Building Communities of Practice

## The "Day Four" Crisis & The Lone Bioinformatician
- **The Post-Workshop Reality:**
  - Trainees return home with high enthusiasm, but face departmental isolation.
  - Without ongoing mentorship, code review, or peer support, skill decay reaches 100%.
- **The Community of Practice (CoP) Solution (Lave & Wenger):**
  - Learning is fundamentally social.
  - Sustained capacity requires peer networks that support active problem-solving long after the workshop ends.

## Grassroots Community Formats
- Start small and informal—no institutional budget required:
  - **Hacky Hours / Coding Clinics:** 1 hour weekly; bring your laptop, broken code, and coffee; troubleshoot together.
  - **Carpentries Study Groups:** Bi-weekly shared progression through open online tutorials.
  - **Methods Journal Clubs:** Dissecting the computational methods section of recent papers.
  - **Bug-Busting Hackathons:** Half-day team sprints on shared departmental data.

## Linking Grassroots to Continental Networks
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
