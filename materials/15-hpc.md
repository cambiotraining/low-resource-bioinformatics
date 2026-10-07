---
title: High Performance Computing
---

::: {.callout-tip}
#### Learning Objectives

- Explain the physical and logical architecture of a High-Performance Computing (HPC) cluster, distinguishing between the login node and compute nodes.
- Identify the golden rule of cluster etiquette: never execute computationally demanding tasks directly on the login node.
- Write, submit, monitor, and cancel batch processing jobs using the SLURM workload manager.
- Launch interactive sessions on compute nodes (`srun` / `salloc`) for testing, prototyping, and debugging without impacting other cluster users.
- Profile past job resource utilization using `sacct` to accurately right-size memory, CPU, and walltime allocations for future runs.
- Navigate regional and national shared HPC infrastructure available to researchers in low- and middle-income countries (LMICs).
- Apply effective pedagogical analogies (such as the airport terminal model) to teach HPC concepts to novice learners without triggering cognitive overload.
:::

## Introduction: Why HPC Matters in Bioinformatics

A single sequencing experiment today can generate billions of nucleotide bases. While quality trimming or searching a micro-dataset can be demonstrated on a consumer laptop, genome-wide variant calling across hundreds of patient samples, *de novo* metagenomic assembly, or training deep-learning models for protein structure prediction demands computational resources that far exceed the capabilities of any desktop computer:

- Tens to hundreds of gigabytes (or even terabytes) of working memory (RAM).
- Dozens to hundreds of parallel CPU cores.
- Fast, redundant multi-terabyte storage arrays.

| Personal laptop | HPC cluster |
| :--- | :--- |
| • 4–16 GB RAM | • 128 GB – 2 TB RAM per node |
| • 2–8 CPU cores | • Hundreds to thousands of cores |
| • 256 GB – 1 TB local SSD | • Petabyte-scale shared storage |
| • Single user | • Hundreds of concurrent users |
| • Runs interactive commands directly on the machine | • Governed by an automated batch workload scheduler (e.g. SLURM) |

: Table 1: Laptop versus high performance computing

In low-resource environments, researchers rarely own personal high-spec workstations. Instead, **access to shared institutional, regional, or national HPC clusters represents their primary gateway to large-scale computational science**. As trainers, preparing our learners to navigate these shared environments responsibly is essential for their scientific autonomy.


## Anatomy of an HPC Cluster

To use a cluster effectively, learners need a clear mental model of how an HPC environment is physically and logically partitioned.

```
                                  [ EXTERNAL USERS ]
                                  (Laptops over SSH)
                                          │
                                          ▼
                                ┌───────────────────┐
                                │    LOGIN NODE     │
                                │ (The Front Desk)  │
                                │ • Edit scripts    │
                                │ • Submit jobs     │
                                │ • Check queues    │
                                └─────────┬─────────┘
                                          │
                                          ▼
                                ┌───────────────────┐
                                │   SLURM SCHEDULER │
                                │  "Traffic Control"│
                                └─────────┬─────────┘
                                          │
              ┌───────────────────────────┼───────────────────────────┐
              ▼                           ▼                           ▼
     ┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
     │  COMPUTE NODE 1 │         │  COMPUTE NODE 2 │         │  COMPUTE NODE N │
     │  (e.g. 64 Cores,│         │  (e.g. 64 Cores,│         │  (e.g. 64 Cores,│
     │   256 GB RAM)   │         │   256 GB RAM)   │         │   256 GB RAM)   │
     └────────┬────────┘         └────────┬────────┘         └────────┬────────┘
              │                           │                           │
              └───────────────────────────┴───────────────────────────┘
                                          │
                                          ▼
                                ┌───────────────────┐
                                │  SHARED STORAGE   │
                                │   (NFS / Lustre)  │
                                └───────────────────┘
```

### The Airport Terminal Analogy

An intuitive way to explain cluster architecture to biological learners is the **international airport analogy**:

1. **The Login (Head) Node — The Departure Hall / Check-in Desk:**
   - When you connect to the cluster via SSH, you arrive at the login node.
   - Just as you cannot board an airplane or take off in the check-in hall, **you must never run heavy computational analyses on the login node**.
   - The login node is strictly for light administrative tasks: organizing files, editing scripts, checking job status, and submitting requests.
2. **The Scheduler (SLURM) — Air Traffic Control:**
   - Air traffic control decides which flights take off, on which runway, and at what time based on runway availability and fuel.
   - The scheduler inspects your resource request (how many cores, how much RAM, how many hours) and assigns your job to available compute hardware.
3. **The Compute Nodes — The Airplanes:**
   - The powerful workhorses where the journey actually occurs.
   - Compute nodes have no monitors, keyboards, or direct internet access; they execute instructions passed to them by the scheduler.
4. **Shared Filesystem — The Baggage Carousel:**
   - A high-speed network storage system (such as Lustre or NFS) that is mounted identically across all compute nodes and login nodes. Whether your job runs on Node 1 or Node 50, it reads and writes to the exact same home directory.


## The Golden Rule of Cluster Etiquette

The most frequent error made by novice bioinformaticians on an HPC cluster is running tools directly in their login shell:

```bash
# ❌ THE CARDINAL SIN ON AN HPC:
trainee@login01:~$ bwa mem -t 32 reference.fasta reads_R1.fq reads_R2.fq > aligned.sam
```

::: {.callout-important}
## Why Running on the Login Node is Dangerous
The login node is shared by dozens (or hundreds) of researchers simultaneously. If one user launches a memory-heavy or multi-threaded tool directly on the login node:

1. The login node's CPU and RAM become completely saturated.
2. Other researchers' terminals freeze; SSH sessions drop; text editors lock up.
3. System administrators will promptly terminate the process and may suspend the offending user's account.

**The Golden Rule:** If a command takes more than a few minutes or consumes more than a modest amount of RAM (~1–2 GB), it **must** be submitted to the compute nodes via the scheduler.
:::


## The SLURM Workload Manager

While several workload managers exist (e.g. PBS/Torque, Grid Engine/SGE, LSF), **SLURM (Simple Linux Utility for Resource Management)** is the modern global de facto standard across academic and research computing.

### 1. Writing a SLURM Batch Script

A SLURM batch job is a standard Bash shell script with a series of special comment headers beginning with `#SBATCH`. The scheduler reads these headers to determine resource allocations before launching the script on a compute node.

```bash
#!/usr/bin/env bash
# ==============================================================================
# File: run_spades_assembly.sh
# ==============================================================================

#SBATCH --job-name=spades_tb          # Name shown in the job queue
#SBATCH --output=logs/%x_%j.out        # Standard output log (%x=job name, %j=job ID)
#SBATCH --error=logs/%x_%j.err         # Standard error log
#SBATCH --partition=standard           # Queue/partition to submit to
#SBATCH --nodes=1                      # Request 1 physical compute node
#SBATCH --ntasks=1                     # Request 1 task
#SBATCH --cpus-per-task=16             # Request 16 CPU cores for multi-threading
#SBATCH --mem=64G                      # Request 64 GB of total RAM
#SBATCH --time=04:00:00                # Maximum run time (DD-HH:MM:SS)
#SBATCH --mail-type=END,FAIL           # Send email when job finishes or fails
#SBATCH --mail-user=trainee@inst.edu   # Recipient email address

# Strict bash safety flags
set -euo pipefail

# Load required environment modules
module purge
module load spades/3.15.5

# Create directories
mkdir -p results/assembly logs

echo "Starting SPAdes assembly on host: $(hostname)"
echo "Job ID: ${SLURM_JOB_ID} on node: ${SLURUR_NODELIST:-local}"

# Execute tool using allocated CPU cores ($SLURM_CPUS_PER_TASK)
spades.py \
  -1 data/sample1_R1.fq.gz \
  -2 data/sample1_R2.fq.gz \
  -o results/assembly/sample1 \
  -t "${SLURM_CPUS_PER_TASK}" \
  -m 60

echo "Assembly completed successfully at: $(date)"
```

### 2. Managing Jobs: The Four Essential Commands

```
       sbatch                          squeue                           scancel
   "Submit my job"               "Check queue status"              "Cancel my job"
        │                                 │                               │
        ▼                                 ▼                               ▼
┌─────────────────┐             ┌───────────────────┐           ┌─────────────────┐
│ sbatch job.sh   │             │ squeue -u $USER   │           │ scancel 10842   │
│ Submitted 10842 │             │ JOBID ST TIME NODES│          │ Terminated.     │
└─────────────────┘             └───────────────────┘           └─────────────────┘
```

| Command | Purpose | Useful Flags |
| :------ | :------ | :----------- |
| `sbatch script.sh` | Submits a batch script to the scheduler queue. | Returns the unique numeric `JobID`. |
| `squeue` | Inspects the queue and pending/running jobs. | `squeue -u $USER` (view only your jobs). |
| `scancel <JobID>` | Cancels/kills a running or queued job. | `scancel -u $USER` (cancels all your active jobs). |
| `sinfo` | Displays the status of cluster nodes and partitions. | Shows which nodes are `idle`, `alloc`, or `down`. |

### Common SLURM Job State Codes (`ST`)
- **`PD` (Pending):** Waiting in queue for required CPUs/RAM to become available or waiting behind higher-priority jobs.
- **`R` (Running):** Currently executing on assigned compute nodes.
- **`CG` (Completing):** Finishing up and releasing resources.
- **`CD` (Completed):** Successfully exited with return code 0.
- **`OOM` / `F` (Out Of Memory / Failed):** Aborted due to exceeding requested RAM or encountering an error.


## Interactive Computing on Compute Nodes: `srun`

When developing a new pipeline, writing a script, or troubleshooting a tool, submitting a batch script and waiting for log files to appear is slow and cumbersome.

Instead, users can request an **interactive shell on a compute node** using `srun`:

```bash
# Request an interactive session with 4 CPUs and 16 GB RAM for 2 hours
srun --partition=standard --cpus-per-task=4 --mem=16G --time=02:00:00 --pty bash -i
```

Once granted, your terminal prompt changes:
```
# Before: You were on the shared login node
trainee@login01:~$ 

# After srun: You are now sitting directly on compute node 08!
trainee@node08:~$ 
```
You can now test commands interactively, inspect intermediate files, and experiment freely—without endangering the login node! When finished, simply type `exit` to release the resources back to the queue.


## Software Management on HPC: Environment Modules

Unlike personal laptops where users can install tools using `sudo apt` or custom paths, multi-user HPC clusters use **Environment Modules** (`Lmod` or `Tcl/C modules`). 

Modules dynamically modify the user's `$PATH`, `$LD_LIBRARY_PATH`, and environmental variables to make specific software versions active without conflicting with other packages:

```bash
# List all software packages installed on the cluster
module avail

# Search for a specific tool (e.g. samtools)
module avail samtools

# Load a specific version of samtools
module load samtools/1.19

# Verify that the binary is now in your $PATH
which samtools

# Check which modules are currently loaded in your session
module list

# Unload all modules to prevent version conflicts
module purge
```

::: {.callout-tip}
## Combining Modules with Containers on HPC
If your institutional cluster does not provide a module for a newly published tool, do not beg the system administrator to install it. Use **Apptainer / Singularity** (covered in Chapter 12):
```bash
module load apptainer
apptainer exec docker://biocontainers/fastp:v0.23.4_cv1 fastp --help
```
This gives you total software autonomy without requiring administrative privileges!
:::


## Resource Profiling: The "Good Citizen" Model

In resource-constrained environments, compute capacity is scarce and shared among many researchers. Asking for excessive resources "just to be safe" wastes cluster capacity and inflates queue wait times.

```
┌────────────────────────────────────────────────────────────────────────┐
│                   THE OVER-ALLOCATION PROBLEM                          │
├───────────────────────────────────┬────────────────────────────────────┤
│ ❌ Over-Allocated Request:        │ ✅ Right-Sized Request:            │
├───────────────────────────────────┼────────────────────────────────────┤
│ #SBATCH --cpus-per-task=32        │ #SBATCH --cpus-per-task=8          │
│ #SBATCH --mem=128G                │ #SBATCH --mem=16G                  │
│ #SBATCH --time=48:00:00           │ #SBATCH --time=03:00:00            │
│                                   │                                    │
│ Actual Usage:                     │ Actual Usage:                      │
│ • Uses 8 cores (24 idle cores!)   │ • Uses 8 cores (100% efficient)    │
│ • Uses 12 GB RAM (116 GB wasted!) │ • Uses 12 GB RAM (Comfortable)     │
│ • Finishes in 1 hour 45 minutes   │ • Finishes in 1 hour 45 minutes    │
│                                   │                                    │
│ Penalty: Waits 2 days in queue!   │ Benefit: Starts in 5 minutes!      │
└───────────────────────────────────┴────────────────────────────────────┘
```

### Inspecting Past Performance with `sacct`

SLURM keeps a complete historical ledger of every job. Teach your learners to perform **post-mortem profiling** using `sacct`:

```bash
# Inspect actual CPU and memory usage of a completed or failed job
sacct -j 10842 --format=JobID,JobName,Partition,AllocCPUS,MaxRSS,Elapsed,State,ExitCode
```
*Example Output:*
```
JobID        JobName    Partition  AllocCPUS     MaxRSS    Elapsed      State ExitCode 
---------- --------- ------------ ---------- ---------- ---------- ---------- -------- 
10842      spades_tb     standard         16              01:42:15  COMPLETED      0:0 
10842.bat+     batch                      16   14820456K  01:42:15  COMPLETED      0:0 
```
- **`MaxRSS`:** The maximum physical RAM the job ever consumed (here, ~14.8 GB).
- *Lesson:* If you requested `--mem=64G` and `MaxRSS` was `14.8 GB`, you can safely request `--mem=20G` next time. Your job will wait significantly less time in the queue!


## Regional & National HPC Initiatives for LMICs

Many researchers in low-resource settings believe they cannot perform large-scale genomic analyses because their home institution lacks a multi-million-dollar server room. In reality, numerous shared public and academic initiatives exist specifically to bridge this divide:

1. **National and Regional Supercomputing Centres:**
   - **South Africa / SADC:** The Centre for High Performance Computing (CHPC) in Cape Town provides massive computing clusters accessible to academic researchers across South Africa and partner SADC nations.
   - **Regional Research and Education Networks (NRENs):** Entities such as WACREN (West and Central Africa), UbuntuNet Alliance (Eastern and Southern Africa), and ASREN (Arab States) support shared compute and high-speed research networking.
2. **Pan-African Bioinformatics Networks:**
   - **H3ABioNet:** Established distributed compute nodes and training clusters across more than 15 African nations, establishing standardized pipelines for human genetics and pathogen surveillance.
   - **ILRI HPC (Kenya):** The International Livestock Research Institute hosts shared clusters serving agricultural and infectious disease researchers across East and Central Africa.
3. **Global Academic Partnerships:**
   - Many European and North American universities and consortia (e.g. ELIXIR, NIH Fogarty International Center) provide compute allocations and remote cluster accounts for collaborative LMIC research projects.


## Interactive Exercises for Future Trainers

These exercises will test your ability to diagnose common cluster mistakes, guide novices in writing robust batch scripts, and foster good cluster citizenship.

::: {.callout-exercise}
## Intercepting a Rogue Process on the Login Node

You are a teaching assistant during an advanced metagenomics workshop on an institutional cluster. Suddenly, all 20 students begin complaining that their terminal windows have frozen and their `nano` text editors are unresponsive. 

You log in to the cluster, run `top`, and see the following:

```
PID   USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
4219  student07 20   0   42.4g  38.1g   1.2g R 1598.2  62.1  14:22.08 spades.py
```

1. What has happened here, and why did everyone's terminal freeze?
2. What immediate operational action must you take to restore cluster usability?
3. How would you handle this situation pedagogically with `student07` without embarrassing them in front of their peers?
4. What concrete command should you show them so they can continue running their assembly properly?

::: {.callout-hint}
Notice the `%CPU` (~1600%, meaning 16 cores saturated) and `%MEM` (38.1 GB RAM) running on the login host.
:::

::: {.callout-answer}
### Incident Response & Pedagogical Intervention

1. **Diagnosis:**
   `student07` ran a massive multi-threaded *de novo* genome assembly (`spades.py`) directly on the shared login node instead of submitting it to the compute nodes. The job consumed 16 CPU cores and 38 GB of RAM, exhausting memory, triggering disk swapping, and locking up the system for all 20 participants.

2. **Immediate Operational Action:**
   Terminate the rogue process immediately to restore system responsiveness:
   ```bash
   kill -15 4219    # Gentle termination
   # If unresponsive:
   kill -9 4219     # Force kill
   ```

3. **Pedagogical Handling:**
   - **Do not publicly scold the student.** Treat this as an invaluable teaching moment for the whole room:
   - *"Everyone, our login node just froze because a heavy command was run here. This is the single most common mistake in HPC, and it happens to everyone at least once! Let's look at why it happened and how we do this the right way."*
   - Revisit the **airport terminal analogy**: remind the class that the login node is the ticket counter, not the airplane.

4. **Corrected Command:**
   Show the student how to launch an interactive session on a compute node:
   ```bash
   srun --partition=standard --cpus-per-task=16 --mem=40G --time=03:00:00 --pty bash -i
   # Once on the compute node:
   spades.py -1 R1.fq.gz -2 R2.fq.gz -o asm_out -t 16
   ```
   Or guide them to write a formal `#SBATCH` submission script.
:::
:::

::: {.callout-exercise}
## Deconstructing and Fixing a Faulty SLURM Script

A researcher brings you the following SLURM script, complaining: *"My job ran for 10 seconds, failed with an error, and produced no output files."*

```bash
#!/bin/bash
#SBATCH -J my_alignment
#SBATCH -c 8
#SBATCH --mem 100G
#SBATCH -t 24:00:00

bwa mem -t 8 /ref/hg38.fa reads_1.fq reads_2.fq > results/aligned.sam
samtools sort -@ 8 results/aligned.sam -o results/sorted.bam
```

Identify at least **four critical defects or missing best practices** in this script and provide a corrected, robust version.

::: {.callout-answer}
### Script Defects & Corrected Version

1. **Missing Directory Creation:** The script writes to `results/aligned.sam`, but never checks if the `results/` folder exists. If missing, `bwa` crashes instantly.
2. **Missing Environment Modules:** `bwa` and `samtools` are not loaded via `module load`. On an HPC compute node, non-standard binaries are not in `$PATH` by default.
3. **No Error Handling Flags:** The script lacks `set -euo pipefail`. If `bwa` fails, the script continues blindly and attempts to run `samtools` on an empty file.
4. **Intermediate Disk Waste:** Writing an uncompressed 100 GB `aligned.sam` to disk before sorting it wastes precious shared I/O bandwidth and disk quota. They should be connected via a pipe (`|`).
5. **No Explicit Log Files:** Omitting `--output` and `--error` headers causes logs to be dumped into generic `slurm-<jobid>.out` files in the submission directory.

**Corrected, Robust SLURM Script:**
```bash
#!/usr/bin/env bash
#SBATCH --job-name=bwa_alignment
#SBATCH --output=logs/%x_%j.out
#SBATCH --error=logs/%x_%j.err
#SBATCH --partition=standard
#SBATCH --cpus-per-task=8
#SBATCH --mem=32G                      # 100G is excessive for human BWA mapping; 32G is ample
#SBATCH --time=06:00:00

set -euo pipefail

# Create required directories
mkdir -p results logs

# Load required cluster modules
module purge
module load bwa/0.7.17
module load samtools/1.19

echo "Starting alignment on node: $(hostname) at $(date)"

# Stream BWA directly into samtools sort to save disk I/O
bwa mem -t "${SLURM_CPUS_PER_TASK}" /ref/hg38.fa reads_1.fq reads_2.fq | \
samtools sort -@ 4 -m 4G -o results/sorted.bam -

# Index the resulting BAM
samtools index results/sorted.bam

echo "Pipeline completed successfully at $(date)"
```
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- **Respect the Login Node:** The login node is a shared front desk for editing, script management, and queue submission. Heavy processing must **always** be delegated to compute nodes via the scheduler.
- **Master SLURM Fundamentals:** Understand `#SBATCH` directives (`--cpus-per-task`, `--mem`, `--time`, `--partition`), and use `sbatch` (submit), `squeue` (monitor), and `scancel` (abort).
- **Prototype Interactively with `srun`:** Use `srun --pty bash -i` to obtain an interactive terminal on a compute node for debugging pipelines without blind batch submission.
- **Environment Modules Manage Conflicts:** Use `module avail`, `module load`, and `module purge` to dynamically configure software environments without root access, combining with Apptainer containers when needed.
- **Profile Past Jobs with `sacct`:** Practice good cluster citizenship by checking `MaxRSS` and `Elapsed` times to right-size resource requests, reducing queue wait times for everyone.
- **Leverage Regional Facilities:** Regional HPC centers (such as CHPC and NREN networks) provide high-capacity computing accessible to LMIC researchers who lack local infrastructure.
:::
