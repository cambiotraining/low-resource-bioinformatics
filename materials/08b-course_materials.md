---
title: Authoring and Publishing Course Materials
---

::: {.callout-tip}
#### Learning Objectives

- Contrast plain-text open authoring stacks (Markdown, Quarto, Git) with proprietary desktop formats (Word, PowerPoint) for technical course development.
- Implement cognitive visual hierarchy in course pages using specialized Quarto callout blocks (objectives, notes, warnings, and interactive exercises).
- Deploy and host interactive course websites for free using GitHub Pages and automated continuous integration.
- Engineer offline-first material bundles (self-contained HTML sites, standalone PDFs) that function without internet in resource-limited training venues.
- Apply academic attribution standards (`CITATION.cff`, Zenodo DOIs, Creative Commons licenses) to ensure educational materials are citable scholarly outputs.
:::

## Introduction: Beyond Static Documents

For decades, academic course materials consisted of proprietary desktop files: Microsoft Word documents, PowerPoint slide decks, and exported PDFs. While familiar, these formats create severe maintenance and accessibility friction in computational training:
- **Version Control Failure:** Collaboration results in messy email attachments like `Module1_v2_final_edited_AM.docx`.
- **Format Inflexibility:** Updating a command requires manually copying and pasting changes across slide decks, student handouts, and instructor cheatsheets.
- **Barrier to Contribution:** Proprietary formats prevent open-source community contributions, translations, and seamless adaptation.

```
┌────────────────────────────────────────────────────────────────────────┐
│                   PROPRIETARY FORMATS vs OPEN AUTHORING                │
├───────────────────────────────────┬────────────────────────────────────┤
│     PROPRIETARY (Word / PPT)      │       OPEN AUTHORING (Quarto / Git)│
├───────────────────────────────────┼────────────────────────────────────┤
│ • Binary, closed formats          │ • Human-readable plain text (.md)  │
│ • "Track changes" confusion       │ • Precise Git version control      │
│ • Format locked (Word $\neq$ Web) │ • Single source $\rightarrow$ Web, │
│ • Expensive software licenses     │   PDF, and Slides simultaneously   │
│ • Hard to search or link          │ • Fully searchable, accessible web │
│ • Hidden behind email attachments │ • Free global hosting on GitHub    │
└───────────────────────────────────┴────────────────────────────────────┘
```

Modern bioinformatics training leverages **open-source authoring frameworks**. By writing materials in plain text using **Markdown** and compiling them with **Quarto**, instructors create reproducible, multi-format curricula that are free to host, easy to maintain, and resilient in low-resource environments.


## The Open Authoring Ecosystem: Quarto & Markdown

**Quarto** is an open-source scientific and technical publishing system that transforms plain-text Markdown into rich websites, books, presentations, and documents.

```
                             ┌───────────────────┐
                             │ Source Documents  │
                             │ (Markdown: .md)   │
                             └─────────┬─────────┘
                                       │
                                       ▼
                             ┌───────────────────┐
                             │   Quarto Engine   │
                             │ (Embedded Pandoc) │
                             └─────────┬─────────┘
                                       │
        ┌──────────────────────────────┼──────────────────────────────┐
        ▼                              ▼                              ▼
┌──────────────────┐          ┌──────────────────┐          ┌──────────────────┐
│ Interactive Web  │          │ Printable PDF /  │          │ PowerPoint / HTML│
│ (Static HTML)    │          │ Offline Manual   │          │ Slide Decks      │
└──────────────────┘          └──────────────────┘          └──────────────────┘
```

### Why Quarto Excels for Technical Training
1. **Single-Source Publishing:** You write your lesson content once. Quarto can render that single source into an interactive website, a downloadable PDF manual, or a PowerPoint slide deck (`format: pptx`).
2. **Executable Code Blocks:** If teaching Python, R, or Bash, Quarto can execute code blocks during rendering, ensuring that example outputs, plots, and tables are always synchronized with the code.
3. **Zero Licensing Costs:** Quarto is completely free and cross-platform (Linux, macOS, Windows).


## Visual Scaffolding with Callout Blocks

Novice learners struggle to parse walls of unformatted text. Effective course design uses **callout boxes** to establish clear visual hierarchy and guide cognitive focus.

In Quarto, callouts are created using the `::: {.callout-<type>}` syntax:

```markdown
::: {.callout-tip}
#### Learning Objectives
- Actionable outcomes written with Bloom's Taxonomy verbs.
:::

::: {.callout-note}
## Conceptual Context
Background explanation connecting computation to biology.
:::

::: {.callout-warning}
## Common Beginner Pitfall
Alerting learners to dangerous syntax traps or file errors.
:::

::: {.callout-exercise}
## Challenge Title
Hands-on task for learners to solve.

::: {.callout-answer}
Hidden model solution revealed on click.
:::
:::
```

### Standard Pedagogical Callout Functions:
- **`callout-tip` (Green):** Reserved for framing Learning Objectives at the start of each page and Key Points in the concluding summary.
- **`callout-note` (Blue):** In-depth biological analogies, historical context, or terminology disambiguation.
- **`callout-warning` / `callout-caution` (Orange/Red):** Critical warnings (e.g. irreversible `rm` commands, line-ending mismatches, or laptop battery warnings).
- **`callout-exercise`:** Numbered active learning exercises with collapsible answers, allowing learners to attempt challenges before inspecting solutions.


## Zero-Cost Web Hosting with GitHub Pages

Universities in low-resource settings often lack dedicated web hosting budgets or suffer from restrictive IT department firewalls.

**GitHub Pages** provides completely free, high-speed, secure web hosting for static websites directly from a GitHub code repository:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   CONTINUOUS DEPLOYMENT WORKFLOW                       │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│   1. Instructor edits markdown locally:                                │
│      git commit -m "Update variant calling module"                     │
│      git push origin main                                              │
│                                │                                       │
│                                ▼                                       │
│   2. GitHub Actions automated runner triggers:                         │
│      • Installs Quarto                                                 │
│      • Runs: quarto render                                             │
│      • Compiles static HTML into gh-pages branch                       │
│                                │                                       │
│                                ▼                                       │
│   3. Website published instantly worldwide:                            │
│      https://username.github.io/my-bioinformatics-course/              │
│      (Fast CDN, SSL encryption, zero hosting fees, 100% uptime!)       │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```


## Designing for Low-Bandwidth and Offline Venues

A common failure mode of online course materials is relying on an active internet connection during class. If the classroom router fails, learners cannot read the tutorial steps.

Open authoring allows trainers to build **offline-first curricula**:

### 1. Self-Contained Static HTML Bundles (`_site/`)
When Quarto renders a website, all HTML files, CSS stylesheets, icons, and JavaScript navigation scripts are compiled into a standalone folder called `_site/`:
- **The USB "Sneakernet" Workflow:** The instructor zips the `_site/` directory into `course_website.zip` (~10–20 MB) and copies it onto USB flash drives.
- Students unzip the archive onto their local laptops and double-click `index.html`.
- **Result:** The entire course website opens in any browser with functioning sidebar navigation, search indexing, and styling—with **zero internet connection required**!

### 2. Image Optimization for Constrained Networks
High-resolution smartphone photos and uncompressed screenshots bloat course repositories. A 10 MB PNG file will choke a slow classroom connection:
- Compress all diagrams and screenshots to WebP or optimized PNG before committing:
  ```bash
  # Optimize PNG files to under 100 KB
  optipng -o5 materials/images/*.png
  ```


## Academic Credit & Scholarly Archiving

Teaching materials represent substantial scholarly work, yet instructors often receive minimal academic recognition for developing them. Adopting open scientific standards makes your curriculum **citable, discoverable, and credit-bearing**:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   MAKING COURSE MATERIALS CITABLE                      │
├───────────────────────────────────┬────────────────────────────────────┤
│ Mechanism                         │ Practical Benefit                  │
├───────────────────────────────────┼────────────────────────────────────┤
│ 1. CITATION.cff File              │ GitHub automatically displays an   │
│                                   │ "APA / BibTeX Citation" button on  │
│                                   │ the repository page.               │
├───────────────────────────────────┼────────────────────────────────────┤
│ 2. Zenodo DOI Integration         │ Free, permanent digital object     │
│                                   │ identifier (DOI) indexed in Google │
│                                   │ Scholar and Web of Science.        │
├───────────────────────────────────┼────────────────────────────────────┤
│ 3. Creative Commons License       │ Explicit CC BY 4.0 license grants  │
│    (LICENSE.md)                   │ reuse rights while legally         │
│                                   │ mandating attribution to you.      │
└───────────────────────────────────┴────────────────────────────────────┘
```

### Setting Up a `CITATION.cff` File
Place a `CITATION.cff` file in your repository root:
```yaml
cff-version: 1.2.0
message: "If you use or adapt these materials, please cite them as below."
title: "Practical Genomics in Resource-Constrained Settings"
authors:
  - family-names: Mensah
    given-names: Kwame
    affiliation: "University of Science and Technology"
    orcid: "https://orcid.org/0000-0002-1234-5678"
version: 1.0.0
date-released: 2026-03-15
license: CC-BY-4.0
```


## Interactive Exercises for Future Trainers

These exercises will guide you in structuring an open lesson and configuring automated web publishing.

::: {.callout-exercise}
## Restructuring a Wall of Text into Scaffolded Markdown

You receive a draft lesson from a guest lecturer submitted as a plain Word document:
> *"Students should know how to run BWA. BWA is a Burrows-Wheeler aligner. First you must index the genome with bwa index ref.fa. Be careful because indexing human takes 3 hours and 5 GB of RAM so use our small phage genome instead. After indexing, run bwa mem ref.fa r1.fq r2.fq > out.sam. Now answer this question: what happens if you forget to index first?"*

Rewrite this paragraph into structured Quarto Markdown:
1. Include a `callout-tip` with a measurable learning objective.
2. Provide a clear code block with explanatory text.
3. Include a `callout-warning` alerting learners to the memory/runtime trap.
4. Wrap the question and solution inside a `callout-exercise` with a hidden `callout-answer`.

::: {.callout-answer}
### Structured Quarto Markdown Version

```markdown
::: {.callout-tip}
#### Learning Objectives
- Index a reference genome and align paired-end sequencing reads using BWA-MEM.
:::

## Genome Indexing and Alignment

Before sequencing reads can be mapped, the reference genome must be formatted into a searchable lookup index based on the Burrows-Wheeler Transform.

```bash
# 1. Index the reference genome (phage_genome.fasta)
bwa index phage_genome.fasta

# 2. Align paired-end reads to the indexed reference
bwa mem phage_genome.fasta reads_R1.fq.gz reads_R2.fq.gz > results/aligned.sam
```

::: {.callout-warning}
## Indexing Resource Requirements
Indexing a full 3 GB human genome takes over 3 hours and requires 5 GB of RAM. In our classroom exercises, we exclusively index a small 50 kb bacteriophage genome, which completes in under 5 seconds!
:::

::: {.callout-exercise}
## Identifying Indexing Prerequisites

What error will BWA-MEM return if you attempt to run `bwa mem ref.fa R1.fq R2.fq` without executing `bwa index ref.fa` first?

::: {.callout-answer}
BWA-MEM will abort immediately with:
`[E::bwa_idx_load_from_disk] fail to locate the index files`
Because BWA relies on five binary index files (`.amb`, `.ann`, `.bwt`, `.pac`, `.sa`), mapping cannot begin without the prior indexing step.
:::
:::
```
:::
:::

::: {.callout-exercise}
## Auditing Offline Readiness for Course Webpages

You have authored an attractive online course website using Quarto. Before traveling to a rural field station with zero internet connectivity to deliver the workshop, you want to ensure your materials will function 100% offline.

List **four common online dependencies** that will break when students open a web tutorial offline, and explain how to eliminate each dependency during development.

::: {.callout-answer}
### Offline Readiness Audit

1. **Embedded YouTube or Vimeo Videos:**
   - *Problem:* Embedded streaming iframes fail with black screens offline.
   - *Fix:* Replace streaming embeds with local static diagrams, or distribute `.mp4` video files directly on the USB drive.

2. **External CDN JavaScript / CSS Links:**
   - *Problem:* Linking to external fonts (Google Fonts) or icons via remote CDNs causes unstyled text or browser hanging.
   - *Fix:* Use Quarto's built-in themes and local font extensions, which bundle all styling and icon fonts directly inside the `_site/` directory.

3. **External Hyperlinks for Datasets:**
   - *Problem:* Tutorials instructing students to *"click here to download the reference genome from NCBI"* will fail.
   - *Fix:* Place all required reference genomes and micro-datasets inside a local `course_files/data/` folder included in the offline USB distribution.

4. **External Web Documentation Links:**
   - *Problem:* Links to tool manuals (e.g. `samtools.github.io`) will not resolve.
   - *Fix:* Provide pre-compiled offline cheatsheets or mirror the documentation locally using `wget --mirror`.
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- **Plain Text Powers Sustainability:** Writing course materials in Markdown and Quarto eliminates proprietary software dependencies, enables robust Git version control, and generates web, PDF, and slide formats from a single source.
- **Scaffold Cognition with Callouts:** Structure lessons using visually distinct callout blocks (`callout-tip` for objectives/summary, `callout-warning` for pitfalls, and `callout-exercise` for active practice).
- **Free Hosting via GitHub Pages:** Leverage automated GitHub Actions to build and host professional course websites with zero server or licensing costs.
- **Build Offline-First Curricula:** Distribute compiled `_site/` static HTML folders via USB drives so learners have full interactive website functionality without internet access.
- **Ensure Academic Credit:** Add a `CITATION.cff` file and link your repository to Zenodo to mint persistent DOIs, turning educational development into a citable scholarly contribution.
:::
