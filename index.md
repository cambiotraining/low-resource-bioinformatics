---
date: today
pagetitle: "Overview"
---

# Teaching Bioinformatics in Low-resource Settings {.unnumbered}

## Overview

*Teaching Bioinformatics in Low-resource Settings* is an intensive train-the-trainer programme tailored for educators, researchers, clinicians, and core facility managers in resource-constrained environments—including Low- and Middle-Income Countries (LMICs). While traditional bioinformatics pedagogy presumes high-speed, unmetered internet, institutional High-Performance Computing (HPC) clusters, and uniform, modern student hardware, trainers in low-resource environments must navigate severe bandwidth limitations, frequent power interruptions, outdated and heterogeneous laptops, and adult learners facing acute terminal anxiety. 


This course bridges the pedagogical and operational divide by integrating evidence-based adult learning theory with practical computational design. Participants learn how to construct offline-resilient, containerised curricula using micro-datasets, implement active learning strategies (such as participatory live coding and driver-navigator pairing), design authentic assessments, author publication-grade open courseware with Quarto, guide learners on the responsible use of generative AI, and nurture sustainable local communities of practice.

::: {.callout-tip}
### Learning Objectives

After completing this course, participants will be able to:

- **Apply Adult Learning Principles**: Contrast andragogical principles with pedagogical assumptions, identify cognitive load thresholds, and mitigate terminal anxiety in adult wet-lab learners.
- **Implement Active Teaching Strategies**: Facilitate participatory live coding with deliberate mistake handling, faded examples, and driver-navigator pair programming to maximise learner retention.
- **Engineer Defensive Computing Environments**: Architect robust training setups resilient to power outages and internet dropouts using micro-datasets, static binaries, pre-cached container images (Apptainer/Docker), and offline `conda-pack` archives.
- **Design Cohesive Curricula**: Formulate backward-designed instructional units using observable Bloom's taxonomy action verbs, diagnostic multiple-choice questions with targeted distractors, and authentic capstone assessments.
- **Author and Publish Open Courseware**: Create modular, version-controlled, and FAIR-compliant training materials using Quarto, Markdown callouts, GitHub Pages, and offline static site bundles.
- **Integrate Responsible AI**: Guide students to critically leverage generative AI as a 24/7 virtual tutor while enforcing verification protocols against hallucinations, deprecated syntax, and genomic privacy violations.
- **Establish Communities of Practice**: Overcome post-workshop regression and the "lone bioinformatician syndrome" by launching local peer-learning cohorts, hacky hours, and institutional study groups.
- **Deliver a Training Blueprint**: Pitch a complete, peer-reviewed, and context-adapted bioinformatics training proposal equipped with contingency matrices and delivery logistics.
:::


### Target Audience

This course is engineered for:

- **Current and Aspiring Bioinformatics Educators**: University lecturers, research software engineers, and teaching assistants preparing to deliver computational genomics or data analysis courses in low-resource or LMIC institutions.
- **Wet-Lab Scientists and Clinicians**: Molecular biologists, clinical microbiologists, and laboratory heads transitioning into data analysis who wish to mentor colleagues and trainees.
- **Core Facility and Institutional Leads**: Facility directors, systems administrators, and capacity-building coordinators tasked with rolling out scalable, sustainable bioinformatics training in regional research institutes.


### Prerequisites

To gain the most from this train-the-trainer curriculum, participants should have:

- **Foundational Knowledge**: Basic familiarity with molecular biology concepts (DNA, RNA, proteins, sequencing workflows) and standard bioinformatic data formats (e.g. FASTA, FASTQ, SAM/BAM, VCF).
- **Basic Command-Line Exposure**: Familiarity with navigating directories (`cd`, `ls`, `pwd`) and viewing text files in a Unix-like shell is advantageous, though no advanced shell scripting or programming experience is required.
- **Educational Motivation**: An active commitment to teaching, institutional capacity development, and open-source scientific knowledge dissemination.

## Citation & Authors

Please cite these materials if:

- You adapted or used any of them in your own teaching.
- These materials were useful for your research work or institutional training programmes.

{{< citation CITATION.cff >}}


## Acknowledgements

These training materials draw deep inspiration from global initiatives dedicated to inclusive, open, and reproducible computational training:

- **[The Carpentries](https://carpentries.org/)** (Software Carpentry, Data Carpentry) for foundational pedagogy in live coding, participatory learning, and instructor training.
- **[The Galaxy Training Network (GTN)](https://training.galaxyproject.org/)** for community-driven, FAIR-compliant open educational resources and micro-tutorials.
- **[H3ABioNet](https://www.h3abionet.org/)** and **[CABANA](https://www.cabana.online/)** for pioneering distributed, low-bandwidth, and pan-African/pan-Latin American bioinformatics capacity building.
- **[Cambridge Research Informatics Training (CRIT)](https://bioinfotraining.bio.cam.ac.uk/)** for the course design framework, pedagogical peer-review, and institutional support.
