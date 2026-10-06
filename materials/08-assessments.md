---
title: Assessment Strategies
---

::: {.callout-tip}
#### Learning Objectives

- Distinguish between **formative assessment** (assessment *for* learning) and **summative assessment** (assessment *of* learning) in professional bioinformatics workshops.
- Construct diagnostic **Multiple-Choice Questions (MCQs)** with deliberate distractors that reveal specific mental model misconceptions.
- Design **Parson’s Problems** (jumbled code blocks) to evaluate workflow logic and command sequencing without syntax typing anxiety.
- Deploy zero-bandwidth formative classroom assessment techniques (finger voting, mini-whiteboards, sticky notes) in connectivity-constrained venues.
- Formulate authentic assessments that mirror real-world research tasks (e.g. multi-sample QC critique, AMR gene confirmation).
- Develop pre- and post-workshop surveys to measure learner self-efficacy gains and evaluate long-term training impact.
:::

## Introduction: Why Assessment is Not About Grading

In formal university education, assessment is often equated with examinations, letter grades, and high-stakes rankings. When teaching adult professionals—such as researchers, clinicians, and laboratory scientists—traditional testing is counterproductive. It induces anxiety, triggers imposter syndrome, and discourages exploratory experimentation.

In short-format bioinformatics training, assessment serves a fundamentally different purpose: **it is a diagnostic navigation tool**.

| FORMATIVE ASSESSMENT<br>(Assessment FOR Learning) | SUMMATIVE ASSESSMENT<br>(Assessment OF Learning) |
| :--- | :--- |
| • Conducted DURING the lesson | • Conducted at the END of a course |
| • Low-stakes / ungraded | • High-stakes (Grades, Ranking) |
| • Diagnoses mental model bugs | • Evaluates overall achievement |
| • Informs immediate instruction | • Evaluates the curriculum |
| • "The chef tasting the soup" | • "The customer eating the soup" |

: Table 1: Formative versus summative assessment

Formative assessment tells both the instructor and the learner: *Did that concept click? Do we share the same mental model? Can we move forward, or do we need to pause and clarify?*


## Diagnostic Multiple-Choice Questions (MCQs)

A standard multiple-choice question often tests trivial recall of facts. A **diagnostic MCQ**, in contrast, is designed to reveal **specific misconceptions or flawed mental models**.

### The Anatomy of a Diagnostic MCQ

An effective diagnostic MCQ consists of:

1. **A Clear Stem:** A focused question presenting a concrete problem or command.
2. **One Correct Answer:** Unambiguously accurate.
3. **Plausible Distractors (Wrong Answers):** Each incorrect option represents a *known, specific conceptual error* or common beginner trap.

::: {.callout-important}
## Sample diagnostic bioinformatics MCQ
**Question:** You want to count how many sequences are in a multi-FASTA  
file called `isolates.fasta`. Which command should you run?          
                                                                     
A) `wc -l isolates.fasta`                                            
B) `grep -c ">" isolates.fasta`                                      
C) `grep -c "^>" isolates.fasta`                                     
D) `head -n 4 isolates.fasta`
:::

### What Each Choice Diagnoses:
- **If they pick A (`wc -l`):** Confuses total lines in a file with total sequences (forgets that FASTA sequences wrap across multiple lines).
- **If they pick B (`grep -c ">"`):** Understands the header marker (`>`), but forgets that description headers or quality lines may contain `>` mid-line; misses the line-start anchor (`^`).
- **If they pick C (`grep -c "^>"`):** **CORRECT.** Accurately identifies the start of header lines.
- **If they pick D (`head -n 4`):** Confuses FASTQ 4-line records with FASTA format.

::: {.callout-note}
## Peer Instruction (The Mazur Technique)
When running an MCQ in class:
1. Have students vote individually in silence.
2. If 40–70% get it right, **do not give the answer away!**
3. Tell students: *"Turn to your neighbor. Find someone who picked a different letter, and convince them why your answer is correct (2 minutes)."*
4. Re-vote. The percentage of correct responses almost always jumps to 85–90% through peer explanation!
:::


## Parson’s Problems: Jumbled Code

One of the greatest pedagogical inventions in computing education is the **Parson’s Problem** (Parsons & Haden, 2006).

Novice bioinformaticians frequently struggle with simultaneous cognitive loads: remembering high-level pipeline logic while hunting for missing quotes, misplaced spaces, or exact flag syntax.

A Parson’s Problem eliminates syntax frustration by providing learners with the **exact lines of code scrambled in random order**. The learner’s task is simply to arrange the lines into the correct execution sequence.

::: {.callout-important}
## Parson’s Problem: variant calling workflow
**Task:** Put the following steps in the correct order to identify high-quality genomic variants from raw sequencing reads:

  [ ] `samtools index aligned_sorted.bam`                                
  [ ] `fastp -i raw_R1.fq.gz -I raw_R2.fq.gz -o clean_R1.fq.gz ...`      
  [ ] `bcftools call -mv -Oz -o raw_variants.vcf.gz`                     
  [ ] `bwa mem reference.fasta clean_R1.fq.gz clean_R2.fq.gz | ...`      
  [ ] `bcftools filter -e 'QUAL < 30 || DP < 10' raw_variants.vcf.gz`
:::

*Correct Order:*

1. `fastp` (Quality trimming raw reads)
2. `bwa mem` (Aligning clean reads to reference)
3. `samtools index` (Indexing the sorted BAM file)
4. `bcftools call` (Calling raw variants)
5. `bcftools filter` (Filtering low-quality calls)

Parson’s problems test whether students understand the **data flow and logical dependencies** of a pipeline without letting syntax typos derail their progress.


## Zero-Bandwidth Classroom Assessment Techniques

In low-resource venues, modern web polling applications (such as Mentimeter, Kahoot, or Slido) often fail because classroom Wi-Fi is overwhelmed or students lack cellular data bundles.

Use these zero-bandwidth, low-tech alternatives:

| Technique | How It Works in Practice |
| :--- | :--- |
| 1. Finger Voting | For MCQs (A, B, C, D): Students hold 1, 2, 3, or 4 fingers against their chest. On count of three, everyone displays their vote simultaneously. |
| 2. Sticky Note Bar Chart | Post a line on the whiteboard: [Hard] ── [Easy]. Students stick their colored sticky notes along the spectrum during coffee breaks. |
| 3. Mini-Whiteboards or Paper Slips | Learners write a one-word command or path on a sheet of paper and hold it up simultaneously. |
| 4. Think-Pair-Share | Give a 60-second prompt; pairs discuss for 2 minutes; call on two random pairs to share. |

: Table 2: Zero-bandwidth formative tools

::: {.callout-tip}
## The "Chest Vote" Rule
When conducting finger voting, have students hold their hand flat against their chest before displaying their fingers. This prevents slower students from looking around the room and copying the vote of the most confident student.
:::


## Authentic Assessment in Bioinformatics

Adult life scientists are motivated by authentic tasks that mirror their professional responsibilities. Replace artificial quizzes with **authentic computational deliverables**:

| Traditional quiz | Authentic task |
| :--- | :--- |
| • "What is the flag for output in fastp?"<br>• "Define N50 in one sentence." | • "Generate a MultiQC report for these 4 patient samples and identify which sample failed library prep." |
| • Memorization-focused | • Interpretation-focused |
| • Abstract and unmotivating | • Directly mirrors lab reality |

: Table 3: Traditional versus authentic assessment

### Examples of Authentic Tasks:
- **The Outbreak Report:** Give learners a VCF file of a clinical isolate; ask them to fill out a 3-field hospital report: (1) Pathogen species, (2) Detected AMR mutations, (3) Recommended treatment exclusion.
- **The Quality Audit:** Provide three MultiQC reports; ask pairs to act as a core facility manager and decide: *"Which of these three sequencing batches should we accept, and which should we reject for re-sequencing?"*


## Measuring Impact: Pre- and Post-Workshop Surveys

To evaluate training efficacy and report outcomes to institutional funders, administer a **Pre-Workshop Survey** and an immediate **Post-Workshop Survey**.

### Measuring Self-Efficacy (Likert Scale)
Rather than testing trivia, measure changes in **learner self-efficacy** (confidence in their ability to perform tasks independently):

> *"On a scale of 1 (Not at all confident) to 5 (Extremely confident), rate your ability to:"*

> 1. *Navigate directories and inspect files using the Linux command line.*
> 2. *Execute an automated quality-trimming pipeline on paired-end reads.*
> 3. *Troubleshoot a syntax error in the terminal independently.*
> 4. *Identify and filter technical artifacts in a variant call set.*

### Long-Term Impact Evaluation (3–6 Months Post-Course)
Follow up with participants months later to measure real-world translation:

- *Have you applied the tools taught in the workshop to your research?*
- *Have you analyzed new datasets that contributed to a thesis, paper, or clinical report?*
- *Have you taught or shared these computational skills with colleagues at your home institution?*


## Interactive Exercises for Future Trainers

These exercises will test your ability to design diagnostic distractors and build authentic assessments.

::: {.callout-exercise}
## Designing a Diagnostic MCQ with Misconception Distractors

You are teaching a lesson on file paths in Linux. You want to assess whether learners understand the difference between absolute paths, relative paths, and the parent directory (`..`).

Write a diagnostic MCQ:
1. Provide a clear question stem based on an explicit directory tree.
2. Provide the correct answer.
3. Write three plausible distractors, explicitly stating what mental model misconception each distractor diagnoses.

::: {.callout-hint}
Use a simple tree where the user's current working directory (`pwd`) is a subfolder like `/home/trainee/projects/`.
:::

::: {.callout-answer}
### Diagnostic MCQ Blueprint

**Stem:**
Given the following directory structure:
```
/home/trainee/
├── data/
│   └── raw.fq
└── projects/  <-- (Current Working Directory: pwd)
```
You are currently inside `/home/trainee/projects/`. Which command will successfully display the first 5 lines of `raw.fq`?

- **Option A:** `head -n 5 /data/raw.fq`
- **Option B:** `head -n 5 data/raw.fq`
- **Option C:** `head -n 5 ../data/raw.fq`  *(CORRECT)*
- **Option D:** `head -n 5 raw.fq`

**Diagnostic Analysis of Distractors:**

- **Option A:** Diagnoses the misconception that `/` (root) is the same as the user's home directory (`~`). The learner thinks `/data` is inside home, when in fact it is at the root level of the system.
- **Option B:** Diagnoses a failure of spatial orientation. The learner assumes `data/` is a child folder inside their current directory (`projects/`), forgetting they must first step up into `trainee/`.
- **Option D:** Diagnoses the "magic file" misconception common among GUI users—assuming the computer knows where `raw.fq` is regardless of directory coordinates.
:::
:::

::: {.callout-exercise}
## Constructing an Authentic Capstone Assessment

Design an **Authentic Assessment Activity** for the final afternoon of a 3-day bacterial genomics workshop in a low-resource setting.

Specify:

1. **The Scenario / Biological Persona.**
2. **The Provided Materials / Micro-dataset (size and format).**
3. **The Concrete Student Deliverable.**
4. **How this task assesses learning without relying on traditional written exams.**

::: {.callout-answer}
### Authentic Capstone Assessment Blueprint

1. **The Scenario:**
   *"You are the bioinformatics officer at the regional hospital. Two blood culture isolates of Salmonella enterica were obtained from patients in Ward 4. The hospital infection control committee wants to know: Are these two cases part of the same nosocomial transmission event, or independent community acquisitions?"*

2. **Provided Materials:**
   - Two paired-end micro-datasets (`patientA_R1/R2.fq.gz` and `patientB_R1/R2.fq.gz`, each 15 MB).
   - Reference genome FASTA file of *Salmonella enterica*.
   - A pre-compiled USB bundle containing `fastp`, `bwa`, `samtools`, and `bcftools`.

3. **Concrete Deliverable:**
   Pairs submit a **1-page Outbreak Briefing Slip** containing:
   - Summary table of raw reads, post-trimming Q30 percentage, and mapping rate for both isolates.
   - Total number of high-quality Single Nucleotide Polymorphisms (SNPs) differentiating Patient A from Patient B.
   - An IGV screenshot showing at least one distinguishing variant.
   - Final Recommendation: Is this a hospital outbreak (typically $\le 5$ SNPs difference) or independent infections ($> 50$ SNPs)?

4. **Pedagogical Rationale:**
   This task evaluates read QC, alignment, indexing, variant calling, variant filtering, visual inspection, and clinical interpretation simultaneously. It mirrors authentic professional practice, engages adult intrinsic motivation, and requires zero traditional grading.
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- **Assessment Drives Learning, Not Grading:** Use formative assessment during class as a real-time diagnostic navigation tool, not a high-stakes ranking system.
- **Diagnostic MCQs Reveal Mental Models:** Design distractors where each wrong answer identifies a specific, known computational misconception (e.g. root vs. home, line count vs. sequence count).
- **Use Peer Instruction:** Combine MCQs with Think-Pair-Share. When students debate differing answers with their neighbors, conceptual understanding increases dramatically.
- **Parson’s Problems Eliminate Syntax Blocks:** Jumbled code exercises assess workflow logic and tool sequencing without letting syntax errors or typos derail beginners.
- **Leverage Zero-Bandwidth Techniques:** Use finger voting, mini-whiteboards, and sticky-note bar charts when internet connectivity is unreliable.
- **Prioritize Authentic Tasks:** Assess adult learners using realistic scientific scenarios (outbreak investigations, QC audits) that yield actionable biological deliverables.
- **Measure Self-Efficacy:** Use pre- and post-workshop surveys to measure gains in learner confidence and track long-term research impact.
:::
