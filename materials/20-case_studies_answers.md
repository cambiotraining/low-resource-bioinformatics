---
title: Case Studies
---

::: {.callout-tip}
#### Learning Objectives

- Critically evaluate published bioinformatics course materials for pedagogical structure, assumptions, and omissions.
- Assess the effectiveness and limitations of common computing analogies used in beginner shell lessons.
- Determine whether an advanced workflow-based genomics curriculum is feasible for delivery in a resource-constrained institutional setting.
- Formulate technical and instructional adaptations (e.g. micro-datasets, offline caching, cooking show pattern) to make advanced curricula deliverable under low-resource constraints.
:::

## Introduction

Evaluating existing curricula is a core skill for training developers. Rather than creating courses from scratch, trainers often adapt established open-access materials. This chapter evaluates two published courses from the Cambridge Centre for Research Informatics Training (CRIT):

1. **[Introduction to the Unix Command Line](https://cambiotraining.github.io/unix-shell/):** A foundational introductory course adapted from The Carpentries.
2. **[Working with Bacterial Genomes](https://cambiotraining.github.io/bacterial-genomics/):** An advanced, multi-day sequencing analysis course.

## Case Study 1: Introduction to the Unix Command Line

The course [Introduction to the Unix Command Line](https://cambiotraining.github.io/unix-shell/) is an entry-level workshop designed for wet-lab biologists and researchers with no prior command-line experience.

### Design Choices

- **Sequential, Scaffolding Structure:** The syllabus follows a traditional linear progression: filesystem navigation (`pwd`, `cd`, `ls`), file operations (`cp`, `mv`, `rm`), text processing (`cat`, `head`, `grep`), standard streams and pipes (`|`, `>`), shell scripts, loops, and remote server access.
- **Three-Tier Exercise Structure:** Exercises are explicitly labelled by difficulty (Level 1: basic recall; Level 2: concept integration; Level 3: open-ended application). This provides immediate self-assessment for learners and allows helpers to triage struggling students.
- **Minimal Dependencies:** Relies on a single downloadable archive (`data-shell.zip`) containing small text files and directory hierarchies.
- **Platform Inclusivity in Documentation:** Appendices detail environment setups for Windows (MobaXterm, Git Bash, WSL) and macOS/Linux terminals.

### Analogies Used and Their Utility

The course uses several foundational analogies to bridge the gap between graphical user interfaces and text-based terminals:

| Analogy | Concept Illustrated | Strengths | Limitations & Misconceptions |
| :--- | :--- | :--- | :--- |
| **Filesystem as an Inverted Tree** | Directory hierarchy (`/`, root, parent, child). | Clarifies directional paths (up to parent `..`, down to child). | Learners often confuse branch order with chronological creation or execution order. |
| **Current Working Directory as "You Are Here"** | Context-dependent relative paths versus absolute paths. | Helps novices understand that commands operate relative to their present location. | Fails when learners pass absolute paths or redirect output to distant directories; they expect to "see" the file move. |
| **Pipes (`\|`) as Physical Plumbing** | Streaming stdout of one program into stdin of another. | Effectively explains that data flows without saving temporary files to disk. | Learners assume the pipe stores data permanently on disk, or confuse pipes with file redirection (`>`). |
| **Wildcards (`*`) as a Joker Card** | Filename pattern matching and globbing. | Easy to remember; encourages batch operations. | Learners frequently confuse glob patterns with regular expressions or pass `*` into commands that take single file arguments. |

: Table 1: Analysis of computing analogies used in introductory shell training

### Gaps and Areas for Improvement

While pedagogically sound for well-equipped classrooms, the curriculum has noticeable omissions when viewed through a low-resource lens:

1. **Generic, Non-Biological Data Files:**
   The dataset (`data-shell.zip`) uses artificial files (`haiku.txt`, `creatures`, `molecules`). Adult biological researchers in LMICs often experience cognitive friction when practicing on abstract text files instead of biological data formats (FASTQ, FASTA, GFF, tabular metadata).
2. **Absence of Defensive Bash Habits:**
   The lesson introduces shell scripting without defensive headers (`set -euo pipefail`). It does not teach students how to verify variable assignments before running `rm`, leaving beginners prone to accidental data loss.
3. **No Session Resilience for Unstable Connections:**
   The remote access module covers raw `ssh`, but ignores terminal multiplexers (`tmux` or `screen`). In regions with frequent Wi-Fi drops, an SSH disconnect terminates running jobs. Introducing `tmux` should be a core requirement, not an advanced afterthought.
4. **Binary vs. Plain Text Distinction:**
   The text-inspection section covers `head`, `tail`, and `less` on plain text, but fails to warn students against running these commands on gzipped data (`.fastq.gz`, `.bam`) or opening large tabular files in spreadsheet software.
5. **Windows-Specific Line Ending Traps:**
   While the appendix explains terminal installation, it omits the common error caused by Windows carriage returns (`\r\n` vs `\n`), which causes scripts edited on Windows to fail on Linux with `\r: command not found`.

## Case Study 2: Working with Bacterial Genomes

The course [Working with Bacterial Genomes](https://cambiotraining.github.io/bacterial-genomics/) covers quality control, reference mapping, *de novo* assembly, annotation, phylogenetics, pan-genome analysis, and AMR detection across 35 detailed modules.

### Institutional Suitability Assessment

| Dimension | Course Requirement | Low-Resource Institution Reality | Feasibility Rating |
| :--- | :--- | :--- | :--- |
| **Network Bandwidth** | Live downloads of multi-gigabyte SRA/ENA runs; downloading Docker/Singularity images on demand. | 2–5 Mbps shared connection, metered data, frequent timeouts. | **Unsuitable** (High risk of classroom failure) |
| **Compute Hardware** | *De novo* assembly, PopPUNK, Panaroo requiring 16–32 GB RAM and multi-core CPUs. | Heterogeneous student laptops (4–8 GB RAM, dual-core); limited or absent local HPC. | **Unsuitable** without remote infrastructure |
| **Workflow Tooling** | Heavy reliance on Nextflow, Docker, Apptainer, and multi-tool pipelines (`bactmap`, `assembleBAC`). | IT permission restrictions on client laptops; limited experience troubleshooting container daemons. | **Challenging** |
| **Pathogen Relevance** | Focus on *M. tuberculosis*, *S. aureus*, and *S. pneumoniae*. | Directly aligns with public health priorities, clinical surveillance, and AMR tracking in LMICs. | **Highly Suitable** (Strong local relevance) |

: Table 2: Feasibility assessment of bacterial genomics curriculum for low-resource settings

### Critical Friction Points

1. **Download Bottlenecks:** Chapter 8 instructs learners to download raw sequence data. Running this live with 20–30 students simultaneously saturates classroom bandwidth within minutes.
2. **Nextflow Abstraction vs. Foundational Literacy:** Teaching Nextflow pipelines (`nf-core/bactmap`, `assembleBAC`) hides tool syntax, intermediate file structures, and error codes behind pipeline logs. If students return to an institution without Nextflow or container runtimes, they cannot run standalone tools.
3. **Hardware-Intensive Steps:** Running genome assembly (`SPAdes` / `Unicycler`) or population clustering (`PopPUNK`) during class causes low-spec laptops to freeze, crash from out-of-memory (OOM) errors, or overheat.

---

## Actionable Adaptations for Low-Resource Delivery

To deliver the *Working with Bacterial Genomes* course successfully in a resource-limited environment, make the following curriculum adaptations:

```
┌────────────────────────────────────────────────────────────────────────┐
│               ADAPTATION STRATEGY: BACTERIAL GENOMICS                  │
├──────────────────────────────────┬─────────────────────────────────────┤
│ ORIGINAL HIGH-RESOURCE DESIGN    │ LOW-RESOURCE ADAPTATION             │
├──────────────────────────────────┼─────────────────────────────────────┤
│ Live download from SRA/ENA       │ Pre-staged local data via USB drive │
│ Full 2-5 GB sequencing runs      │ 2 MB micro-datasets (targeted loci) │
│ Multi-hour assembly during class │ "Cooking Show" pre-computed outputs │
│ Local Docker on student laptops  │ In-room offline server or web GUI   │
│ Monolithic Nextflow pipelines    │ Two-tier instruction (CLI + engine) │
└──────────────────────────────────┴─────────────────────────────────────┘
```

### 1. Replace Live Downloads with Local Data Sneakernet
Remove all live download commands from the classroom schedule. Distribute datasets on USB flash drives before the workshop begins, or serve them over an offline local Wi-Fi router via a local HTTP server.

### 2. Implement Micro-Datasets for Active Steps
Replace gigabyte-sized read files with targeted micro-datasets:
- Extract reads mapping exclusively to specific diagnostic loci (e.g., the *rpoB* gene for *M. tuberculosis* rifampicin resistance, or the *mecA* cassette for *S. aureus*).
- File size drops from 2 GB to under 5 MB.
- Alignments complete in 15–30 seconds on 4 GB RAM laptops, enabling instant feedback and debugging.

### 3. Apply the "Cooking Show" Pattern for Heavy Compute
Avoid running full assemblies, pan-genomes (Panaroo), or large phylogenetic trees live:
- Demonstrate syntax and run initial commands on micro-datasets.
- Once students understand the command and parameters, provide pre-computed output folders containing full assemblies, VCFs, and tree files.
- Transition immediately to downstream interpretation (e.g. visualizing trees in Microreact/Acrobat, inspecting alignments in IGV, or tabulating AMR variants in TB-Profiler).

### 4. Provide a Two-Tier Pipeline Teaching Model
Rather than presenting Nextflow as a black box:
1. **Tier 1 (Mechanics):** Teach one end-to-end command line step manually (e.g. running `fastp` and `bwa mem` directly on a micro-dataset). This builds mental models of input/output streams and parameters.
2. **Tier 2 (Scale):** Introduce Nextflow as an orchestrator that automates those exact steps at scale across multiple samples.

### 5. Deploy a Centralized In-Room Server
Instead of requiring each participant to configure Docker or Conda on locked-down or low-spec personal laptops:
- Run an in-room mini-server (or high-spec laptop) connected to an offline network switch.
- Provide access via web-based terminals (JupyterHub or `ttyd`) over local HTTP/HTTPS.
- Trainees need only a web browser, eliminating local operating system incompatibilities and administrative permission blocks.

---

## Summary

::: {.callout-tip}
#### Key Points

- **Curriculum Evaluation is Essential:** Published course materials reflect the infrastructure and assumptions of the institutions where they were developed.
- **Introductory Shell Lessons:** The CRIT Unix course provides clear scaffolding and graded exercises, but needs biological datasets, defensive scripting practices, and connection resilience tools (`tmux`) for low-resource settings.
- **Advanced Workflows:** The Bacterial Genomics course offers high clinical and biological relevance for LMICs, but its computational footprint (Nextflow, containers, live downloads) is impractical for standard learner laptops.
- **Adaptation Strategy:** Advanced genomics courses can be adapted by replacing live downloads with USB distribution, engineering 2 MB micro-datasets for live execution, providing pre-computed outputs for heavy steps, and running centralized in-room servers.
:::
