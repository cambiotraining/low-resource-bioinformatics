---
title: Case Studies
---

::: {.callout-tip}
#### Learning Objectives

- Critically evaluate published bioinformatics course materials for pedagogical structure, assumptions, and omissions.
- Determine whether an advanced workflow-based genomics curriculum is feasible for delivery in a resource-constrained institutional setting.
- Formulate technical and instructional adaptations (e.g. micro-datasets, offline caching, cooking show pattern) to make advanced curricula deliverable under low-resource constraints.
:::

## Introduction

Evaluating existing curricula is a core skill for training developers. Rather than creating courses from scratch, trainers often adapt established open-access materials. This chapter evaluates two published courses from the Cambridge Centre for Research Informatics Training (CRIT):

1. **[Introduction to the Unix Command Line](https://cambiotraining.github.io/unix-shell/):** A foundational introductory course adapted from The Carpentries.
2. **[Working with Bacterial Genomes](https://cambiotraining.github.io/bacterial-genomics/):** An advanced, multi-day sequencing analysis course.

## Case Study 1: Introduction to the Unix Command Line

The course [Introduction to the Unix Command Line](https://cambiotraining.github.io/unix-shell/) is an entry-level workshop designed for wet-lab biologists and researchers with no prior command-line experience.

::: {.callout-exercise}
## Evaluating the Introduction to Unix Course

For this exercise, we want you to work in groups to critically evaluate the Unix course. In particular, consider the following:

1. **Design choices:** How is the course laid out? How are the exercises structured? How is the data provided?
2. **Analogies used:** How are analogies used to explain the concepts? Do these make sense? Are they useful?
3. **Areas for improvement:** How well would this course work in a low-resource setting? Are there sections that could be rewritten to improve the learner experience?
:::

## Case Study 2: Working with Bacterial Genomes

The course [Working with Bacterial Genomes](https://cambiotraining.github.io/bacterial-genomics/) covers quality control, reference mapping, *de novo* assembly, annotation, phylogenetics, pan-genome analysis, and AMR detection across 35 detailed modules.

::: {.callout-exercise}
## Adapting the Working with Bacterial Genomes Course

Again, working in groups to critically assess the feasability of running the Bacterial Genomes course in a low resource setting. In particular, consider the following:

1. **Institutional suitability:** Could you run the course as it is in your institution? Do you have the computational infrastructure to support the course? Are the pathogens included directly relevant to your institution's work?
2. **Critical failure points:** What are the likely bottlenecks? Is the course suitable for beginners? Would 20 students running Nextflow pipelines at the same time crash your server?
3. **Adaptations for low-resource settings:** How would you avoid the critical failure points? How would you deploy the datasets when internet bandwidth is limited? Does the software being used by the Nextflow pipelines need to be explained separately when teaching the materials to beginners?
:::

## Summary

::: {.callout-tip}
#### Key Points

- **Curriculum Evaluation is Essential:** Published course materials reflect the infrastructure and assumptions of the institutions where they were developed.
- **Introductory Shell Lessons:** The CRIT Unix course provides clear scaffolding and graded exercises, but needs biological datasets, defensive scripting practices, and connection resilience tools (`tmux`) for low-resource settings.
- **Advanced Workflows:** The Bacterial Genomics course offers high clinical and biological relevance for LMICs, but its computational footprint (Nextflow, containers, live downloads) is impractical for standard learner laptops.
- **Adaptation Strategy:** Advanced genomics courses can be adapted by replacing live downloads with USB distribution, engineering 2 MB micro-datasets for live execution, providing pre-computed outputs for heavy steps, and running centralized in-room servers.
:::
