---
title: Practical UNIX
---

::: {.callout-tip}
#### Learning Objectives

- Navigate filesystems, manage files, and inspect directory hierarchies safely using the Unix command-line interface.
- Inspect, filter, and manipulate biological text data (FASTA, FASTQ, SAM, VCF) using core Unix text-processing utilities (`head`, `tail`, `grep`, `wc`, `cut`, `sort`, `uniq`, `awk`).
- Construct streaming pipelines with pipes (`|`) and redirection (`>`, `>>`) to process data efficiently without writing massive intermediate files to disk.
- Automate multi-sample analyses using reproducible Bash shell scripts, variables, and loops.
- Apply process control and session resilience tools (`top`, `htop`, `tmux`, `nohup`) to guard against connectivity drops and power outages.
- Implement evidence-based pedagogical practices (participatory live coding, sticky-note signaling, cognitive deconstruction) to teach Unix to novice life scientists.
:::

## Introduction: The Bioinformatician's Operating System

For more than five decades, the Unix operating system and its open-source descendant, Linux, have served as the computational backbone of scientific computing. Today, virtually all high-throughput bioinformatics software, public biological databases, and high-performance computing clusters run natively on Linux.

In resource-constrained settings, UNIX offers distinct operational advantages:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   WHY UNIX EXCELS IN LOW-RESOURCE SETTINGS             │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  1. Low Hardware Overhead:                                             │
│     The terminal consumes negligible RAM (~15 MB) and CPU, allowing   │
│     older 4 GB RAM laptops to dedicate all resources to the analysis.  │
│                                                                        │
│  2. High-Efficiency Streaming:                                         │
│     Core utilities stream data line-by-line through memory rather than │
│     loading entire multi-gigabyte files into RAM.                      │
│                                                                        │
│  3. Zero Licensing Costs:                                              │
│     Ubuntu, Debian, and Linux-based tools are 100% free and open.      │
│                                                                        │
│  4. Automation & Reproducibility:                                      │
│     Repetitive tasks across 100 patient samples can be scripted with   │
│     a 3-line loop rather than hundreds of manual mouse clicks.         │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

However, for adult learners from wet-lab or clinical backgrounds, opening a black terminal window is often intimidating. As educators, our primary duty in a "Practical UNIX" module is not merely to demonstrate commands, but to demystify the environment and provide psychological safety.


## Essential Navigation and File Hygiene

Before manipulating genomic data, learners must master three basic abilities: finding where they are, moving around, and creating or organizing project directories.

```
       pwd                   cd ..                 ls -lh
   "Where am I?"        "Step up one level"    "What is in here?"
        │                      │                      │
        ▼                      ▼                      ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ /home/trainee/  │    │  /home/trainee  │    │ total 4.2G      │
│ projects/tb_amr │    │                 │    │ sample1.fq.gz   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### The Core Navigation Toolkit

- `pwd` (**P**rint **W**orking **D**irectory): Outputs the current absolute path. Teach learners to run this whenever they feel lost.
- `ls` (**L**i**s**t): Displays files and folders. Always teach useful flags early:
  - `ls -l`: Detailed long listing (permissions, file size, modification date).
  - `ls -lh`: "Human-readable" sizes (e.g. `24M`, `3.8G` instead of raw byte counts like `4080218931`).
  - `ls -a`: Displays hidden files (names beginning with a dot, such as `.bashrc` or `.gitignore`).
  - `ls -lt`: Sorts files by modification time (most recent first), which is invaluable when checking if a pipeline just created a new output file.
- `cd` (**C**hange **D**irectory):
  - `cd raw_data/`: Enter a child directory using a relative path.
  - `cd ..`: Move up one level to the parent directory.
  - `cd ~` or simply `cd`: Return instantly to the user's home directory.
  - `cd -`: Jump back to the previous directory (like the "back" button on a browser).

### Directory and File Management

- `mkdir -p project/{data,results,scripts}`: The `-p` flag creates nested parent directories without throwing errors if they already exist, and curly-brace expansion creates standard subdirectories in a single stroke.
- `cp -r source/ destination/`: The `-r` (recursive) flag is required when copying directories.
- `mv old_name.txt new_name.txt`: Renames files or moves them between paths.

::: {.callout-caution}
## Defensive Computing: Teaching Safe File Deletion
In Unix, `rm` deletes files **permanently and immediately**. There is no "Trash Can" or "Recycle Bin" to restore from.
- **Rule for Novices:** Never teach `rm -rf *` without warning that a single misplaced space (such as `rm -rf / *`) can permanently erase the entire operating system.
- **Safer Habit:** Encourage trainees to create a temporary folder (`mkdir tmp_trash`) and `mv` unwanted files there, deleting the folder only after confirming their results are intact.
- **Use Tab-Completion Religiously:** Pressing the `Tab` key auto-completes directory and file names. If the name does not complete, the path is wrong or the file does not exist. Tab completion prevents typos and eliminates 90% of beginner syntax errors.
:::


## Inspecting Biological Text Files Without Crashing

A common error among novice bioinformaticians is trying to open a 10 GB FASTQ file or a 2 GB VCF file in Microsoft Excel or a standard text editor like Notepad. The application either freezes, crashes due to RAM exhaustion, or silently corrupts the data.

::: {.callout-note}
## The Infamous "Excel Gene Name" Problem
In 2020, the HUGO Gene Nomenclature Committee had to permanently rename several human genes (e.g. *SEPT4* became *SEPTIN4*, and *MARCH1* became *MARCHF1*) because Microsoft Excel persistently converted them into calendar dates (*04-Sep* and *01-Mar*). Furthermore, Excel has a strict hard limit of 1,048,576 rows—opening a 4-million-line FASTQ file will silently discard three-quarters of the sequencing reads!
:::

Unix provides specialized stream utilities designed to inspect and sample massive text files instantly:

### 1. `head` and `tail`: Quick Sampling
- `head -n 20 sample.fastq`: Views the first 20 lines (5 sequencing reads).
- `tail -n 20 sample.fastq`: Views the last 20 lines.
- *Trainer Demonstration:* Show learners that `head` executes in under 2 milliseconds even on a 50 GB file because it only reads the beginning of the stream and exits immediately.

### 2. `less`: Interactive Browsing
- `less -S sample.sam`: Opens an interactive reader without loading the full file into RAM.
  - `-S` chops long lines instead of wrapping them, preserving the columnar layout of SAM and VCF files.
  - Use `/pattern` to search forward, `n` for next match, and `q` to quit safely.

### 3. `wc`: Measuring File Scale
- `wc -l sample.fastq`: Counts total lines.
- Because a standard FASTQ record consists of exactly 4 lines (identifier, sequence, separator, quality score), dividing total lines by 4 yields the exact number of reads:
  ```bash
  # Count reads in an uncompressed FASTQ
  echo $(( $(wc -l < sample.fastq) / 4 ))
  ```


## Text Wrangling: The Swiss Army Knife Utilities

Biological data files (FASTA, FASTQ, SAM, VCF, GFF, BED) are formatted plain text tables. With four core Unix tools, researchers can perform complex filtering, quality checks, and data extraction without writing a single line of Python or R.

```
┌────────────────────────────────────────────────────────────────────────┐
│                        THE UNIX TEXT-WRANGLING MATRIX                  │
├─────────────┬────────────────────────────────┬─────────────────────────┤
│ Tool        │ Primary Function               │ Common Bioinformatic    │
│             │                                │ Use Case                │
├─────────────┼────────────────────────────────┼─────────────────────────┤
│ grep        │ Search lines matching patterns │ Count contigs in FASTA, │
│             │                                │ filter out VCF headers  │
├─────────────┼────────────────────────────────┼─────────────────────────┤
│ cut         │ Extract specific columns       │ Extract chromosome and  │
│             │                                │ positions from BED/VCF  │
├─────────────┼────────────────────────────────┼─────────────────────────┤
│ sort        │ Order lines alphabetically/num │ Sort genomic positions  │
│             │                                │ or sort by read depth   │
├─────────────┼────────────────────────────────┼─────────────────────────┤
│ uniq        │ Collapse duplicates & count    │ Tally variant types,    │
│             │                                │ count unique species    │
├─────────────┼────────────────────────────────┼─────────────────────────┤
│ awk         │ Programmatic column filtering  │ Filter variants where   │
│             │ & conditional calculations     │ quality score > 30      │
└─────────────┴────────────────────────────────┴─────────────────────────┘
```

### 1. Searching with `grep`
- `grep "^>" genome.fasta`: Finds all FASTA header lines (the `^` anchors the search to the start of the line).
- `grep -c "^>" genome.fasta`: Counts the number of contigs or chromosomes.
- `grep -v "^#" variants.vcf`: Inverts the match (`-v`), stripping away metadata comment headers to leave only tabular variant calls.
- `grep -i "plasmodium" annotations.gff`: Performs a case-insensitive search.

### 2. Slicing Columns with `cut`
VCF, BED, and GFF files are tab-delimited. The `cut` utility extracts specific columns with zero memory overhead:
```bash
# Extract Chromosome (col 1), Position (col 2), Ref (col 4), and Alt (col 5) from a VCF
grep -v "^#" variants.vcf | cut -f 1,2,4,5 | head -n 5
```

### 3. Summarizing with `sort` and `uniq`
The `uniq` utility only compares adjacent lines, so data **must be sorted first**:
```bash
# What types of features exist in this GFF annotation file, and how many of each?
grep -v "^#" annotations.gff | cut -f 3 | sort | uniq -c | sort -nr
```
*Output:*
```
  14205 CDS
  15102 exon
   3840 gene
    412 tRNA
```

### 4. Conditional Filtering with `awk`
`awk` reads text line-by-line and breaks each line into fields (`$1`, `$2`, `$3`, etc.). It allows mathematical and logical filtering on the fly:
```bash
# Find all high-quality variants (Column 6 is QUAL > 50) on Chromosome 1 (Column 1)
awk '$1 == "chr1" && $6 > 50 { print $1, $2, $4, $5, $6 }' variants.vcf
```


## Streaming and Pipes: Eliminating Disk Bottlenecks

In low-resource environments, laptop hard drives are often small (e.g. 128 GB or 256 GB SSDs) and slow. Writing intermediate files during a multi-step pipeline fills the drive and wears out hardware.

**Piping (`|`) solves this problem by passing data directly from one program's memory into another's without touching the disk.**

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│  zcat reads.gz  │ ──►── │ grep -c "^@SRR" │ ──►── │  Terminal / Log │
│ (Decompress in  │ Stream│ (Count records  │ Stream│ (Final Count    │
│  Memory Only)   │       │  in Memory)     │       │  Printed)       │
└─────────────────┘       └─────────────────┘       └─────────────────┘
 [ NO 20 GB UNCOMPRESSED FILE IS EVER WRITTEN TO YOUR HARD DRIVE ]
```

### Streaming Compressed Files Directly
Never ask students to run `gunzip huge_file.fastq.gz` on a small laptop drive. Use stream-decompression instead:
- `zcat` (or `gzip -dc` on macOS):
  ```bash
  # Inspect the first two reads of a compressed FASTQ file
  zcat sample_R1.fastq.gz | head -n 8
  ```
- **Real-Time Read Mapping and Sorting:**
  ```bash
  # Align reads with BWA and stream directly into binary BAM sorting
  bwa mem -t 4 ref.fasta sample_R1.fq.gz sample_R2.fq.gz | \
  samtools sort -@ 2 -o sample_sorted.bam -
  ```
  *(Notice the trailing `-` in samtools: it instructs the tool to read from STDIN rather than a file on disk!)*


## Automating Analyses with Bash Scripts

Typing commands interactively is excellent for exploration, but scientific research demands reproducibility. If an analysis was performed by typing 40 commands from memory, it cannot be reproduced, audited, or applied to new samples.

A **Bash script** is simply a text file containing the exact series of commands you would have typed in the terminal, executed sequentially by the shell.

### Anatomy of a Robust Script

```bash
#!/usr/bin/env bash
# ==============================================================================
# Script Name: run_qc_and_trim.sh
# Description: Performs quality control and adapter trimming on paired FASTQs
# ==============================================================================

# Defensive Bash Flags (Fail Fast)
set -euo pipefail

# Define Variables
RAW_DIR="data/raw"
CLEAN_DIR="results/trimmed"
SAMPLE_ID="$1"

# Create output folder if missing
mkdir -p "${CLEAN_DIR}"

echo "Starting processing for sample: ${SAMPLE_ID}"

# Run fastp trimming
fastp \
  -i "${RAW_DIR}/${SAMPLE_ID}_R1.fastq.gz" \
  -I "${RAW_DIR}/${SAMPLE_ID}_R2.fastq.gz" \
  -o "${CLEAN_DIR}/${SAMPLE_ID}_trimmed_R1.fastq.gz" \
  -O "${CLEAN_DIR}/${SAMPLE_ID}_trimmed_R2.fastq.gz" \
  --html "${CLEAN_DIR}/${SAMPLE_ID}_fastp.html" \
  --thread 2

echo "Completed processing for sample: ${SAMPLE_ID}"
```

::: {.callout-tip}
## The "Fail-Fast" Holy Trinity: `set -euo pipefail`
Teach this standard safety header in every scripting workshop:
- `set -e`: Exit immediately if any command returns a non-zero exit code (stops execution before bad data propagates).
- `set -u`: Treat unset/uninitialised variables as errors (prevents catastrophic typos like `rm -rf /${MISSING_VAR}`).
- `set -o pipefail`: If any command in a multi-stage pipe fails, the entire pipeline fails, rather than masking errors behind the final tool's exit status.
:::

### Automating Multi-Sample Processing with Loops

Once a script works for one sample, a `for` loop extends it across dozens or hundreds of files:

```bash
#!/usr/bin/env bash
set -euo pipefail

for file in data/raw/*_R1.fastq.gz; do
    # Extract the base sample name (e.g. "ERR12345" from "data/raw/ERR12345_R1.fastq.gz")
    sample=$(basename "${file}" _R1.fastq.gz)
    
    echo "=========================================="
    echo "Processing: ${sample}"
    echo "=========================================="
    
    bash scripts/run_qc_and_trim.sh "${sample}"
done
```


## Process Management and Session Resilience

In low-resource training venues, electrical power cuts and internet drops are common occurrences. When working over an SSH connection to a remote workstation or cloud instance, losing your local Wi-Fi immediately kills the SSH session, terminating whatever pipeline was running.

Trainers must teach learners how to safeguard their jobs:

```
┌────────────────────────────────────────────────────────────────────────┐
│                     SURVIVING UNSTABLE CONNECTIONS                     │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  Traditional SSH:                                                      │
│  [Laptop] ─── Wi-Fi Drop ───X─── [Server: Pipeline Terminated by OS]   │
│                                                                        │
│  SSH with tmux:                                                        │
│  [Laptop] ─── Wi-Fi Drop ───X─── [tmux Session Running Safely]         │
│                                            │                           │
│  [Laptop Reconnects] ──────────► [Reattach: Pipeline Still Running!]   │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

### The Terminal Multiplexer: `tmux`

`tmux` allows users to create persistent shell sessions on a host machine that survive network disconnects:

1. **Start a new named session:** `tmux new -s variant_calling`
2. **Launch your analysis:** Run your heavy pipeline inside this session.
3. **Detach safely:** Press `Ctrl-b`, release, then press `d`. You return to your local shell, but the pipeline continues running in the background on the server.
4. **Reattach after reconnecting:** `tmux attach -t variant_calling`

### Quick Backgrounding with `nohup`
If `tmux` is not available, run long-running scripts with `nohup`:
```bash
nohup bash run_all_samples.sh > pipeline.log 2>&1 &
```
- `nohup`: Prevents the Hangup Signal (`SIGHUP`) from killing the job when the terminal closes.
- `> pipeline.log 2>&1`: Redirects both normal output (STDOUT) and errors (STDERR) into a log file.
- `&`: Sends the process directly into the background, immediately freeing up your prompt.

### Real-Time Resource Monitoring
Teach learners to monitor their machine's vital signs:
- `htop` (or `top`): Displays CPU usage per core, memory consumption per process, and allows users to terminate frozen processes (`k` or `kill -9 <PID>`).
- `free -h`: Displays available vs used RAM and swap space in human-readable gigabytes.
- `df -h`: Displays remaining disk space across mounted filesystems.


## Pedagogical Strategies: How to Teach UNIX Effectively

Teaching the command line to beginners requires deliberate instructional design. Research from computing education and initiatives like The Carpentries highlights several key practices:

### 1. Participatory Live Coding
- **Never simply click through static PowerPoint slides of shell commands.**
- Open a terminal and type every command live in front of the class while students type along on their own machines.
- **Set font size large:** Increase terminal font to 18pt–24pt so learners in the back of the room can read easily.
- **Narrate your actions:** Explain *why* you are pressing `Tab`, *why* you added a space, and *what* each flag means before pressing Enter.
- **Embrace your mistakes:** When you make a typo live, celebrate it! Show the room how to read the resulting error message, diagnose the problem, and fix it. This teaches resilience and real-world debugging.

### 2. The Two-Color Sticky Note Feedback System
During hands-on exercises, give each learner two differently colored sticky notes (e.g. Green and Red/Pink) to place on their laptop lid:
- **Green Sticky Up:** *"I have completed the exercise and everything worked."*
- **Red/Pink Sticky Up:** *"I am stuck or encountered an error; I need help."*

This system provides trainers with instant visual telemetry of the room's progress without forcing shy learners to interrupt the lecture. Workshop "helpers" or rovers can quietly walk over to assist students with red stickies.

```
       [ Learner Laptop Screen ]
       ┌───────────────────────┐
       │                       │
       │     Terminal CLI      │
       │                       │
       └───────────────────────┘
          [GREEN]         [RED]
       "All good /     "Stuck /
        Finished"       Need Help"
```


## Interactive Exercises for Future Trainers

These exercises will test your ability to diagnose common classroom hurdles and design effective teaching interventions.

::: {.callout-exercise}
## Deconstructing a Data-Wrangling One-Liner

A common pattern for summarizing variants in a VCF file is:

```bash
grep -v "^#" clinical_samples.vcf | cut -f 7 | sort | uniq -c | sort -nr
```

1. Explain what each component of this pipeline does in plain English.
2. What biological or clinical question is this command answering?
3. If a student forgets the first `sort` and runs `... | cut -f 7 | uniq -c | sort -nr`, what erroneous result will they see, and why?

::: {.callout-hint}
Recall that `uniq` operates strictly on consecutive adjacent lines.
:::

::: {.callout-answer}
### Pipeline Deconstruction

1. **Component Explanation:**
   - `grep -v "^#"`: Discards all header and metadata comment lines, leaving only the tab-separated variant records.
   - `cut -f 7`: Extracts field 7 (the `FILTER` column in the VCF specification, which indicates whether a variant passed quality filters, e.g. `PASS`, `LowQual`, `q10`).
   - `sort`: Alphabetically sorts the filter labels so identical values appear consecutively.
   - `uniq -c`: Collapses adjacent identical filter labels and counts their occurrences.
   - `sort -nr`: Sorts the final counts numerically (`-n`) in descending/reverse (`-r`) order.

2. **Biological / Clinical Question:**
   *"How many variants passed quality filters versus failed, and what were the most common reasons for quality failure in these clinical samples?"*

3. **Consequence of Omitting the First `sort`:**
   Because `uniq` only merges adjacent identical lines, if `PASS` appears at line 1 and again at line 10, it will be counted as two separate entries rather than combined into a single grand total. The resulting frequency table will have dozens of fragmented duplicate categories.
:::
:::

::: {.callout-exercise}
## Debugging a Novice's Shell Script

One of your workshop participants is trying to convert all uncompressed FASTQ files in a directory to compressed format. They wrote the following script:

```bash
#!/bin/bash
for f in *.fastq
do
  gzip $f
  echo "Compressed $f"
done
```

The script worked during class, but when they tried running it on their research data at their home institution, it threw this error:

```
gzip: My: No such file or directory
gzip: Patient: No such file or directory
gzip: Data: No such file or directory
gzip: 1.fastq: No such file or directory
```

1. What caused this error?
2. How should the script be modified to make it robust?
3. What general naming advice should you provide to your learners to prevent this problem entirely?

::: {.callout-answer}
### Diagnosis & Remediation

1. **Cause:**
   The file on their computer contained spaces in its name: `My Patient Data 1.fastq`. When the loop expanded `$f` without quotation marks, `gzip` received four separate arguments: `My`, `Patient`, `Data`, and `1.fastq`.

2. **Robust Code:**
   Always wrap variable expansions in double quotes:
   ```bash
   #!/usr/bin/env bash
   set -euo pipefail
   
   for f in *.fastq; do
     # Double quotes preserve whitespace as a single argument
     gzip "${f}"
     echo "Compressed ${f}"
   done
   ```

3. **Preventative Advice for Trainers:**
   Teach the "Golden Rule of Scientific File Naming":
   - Use only lowercase/uppercase letters, numbers, hyphens (`-`), and underscores (`_`).
   - Never use spaces, parentheses, slashes, or special symbols in file names.
:::
:::

::: {.callout-exercise}
## Designing a 5-Minute "First Contact" CLI Lesson

Imagine you are standing in front of 20 life-science researchers who have never seen a terminal before in their lives. You have 5 minutes to introduce the command line and dispel their anxiety before diving into the curriculum.

Outline:
1. What opening metaphor or explanation would you use to describe what the terminal actually is?
2. What is the very first command you would have them type, and why?
3. What common beginner anxiety would you explicitly address?

::: {.callout-answer}
### Model Lesson Plan

1. **Opening Metaphor:**
   *"A graphical user interface (like Windows or macOS Finder) is like dining at a restaurant with a set menu—you can only order what the chef has put on the page, and you have to point with your finger. The command line is like walking into the kitchen and speaking directly to the chef. You have complete freedom to combine any ingredients you want, but you have to know how to speak the chef's language."*

2. **First Command:**
   Have everyone type `whoami`, followed by `pwd`.
   - *Why:* `whoami` immediately gives a reassuring, human-relatable answer (it prints their own name or username). It proves the computer knows who they are and is listening. Following it with `pwd` establishes spatial grounding: *"You are right here in your home folder."*

3. **Addressing Anxiety:**
   *"You cannot break your computer by typing a command during our exercises. The computer will never judge you if you make a spelling error; it will simply say 'command not found', which is just the computer politely saying 'could you repeat that?'"*
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- **The Terminal is a Low-Resource Superpower:** It requires minimal RAM and CPU, costs nothing, handles massive files line-by-line without crashing, and runs uniformly across local laptops, institutional clusters, and remote servers.
- **Safety First:** Teach tab-completion and absolute vs. relative paths before introducing destructive commands. Emphasize that Unix lacks an "undo" or "recycle bin" for `rm`.
- **Avoid GUI Data Corruption:** Standard text utilities (`head`, `less -S`, `grep`, `wc`, `cut`, `awk`, `sort`, `uniq`) allow researchers to inspect and summarize multi-gigabyte genomic files safely without risking Excel date conversions or memory crashes.
- **Piping Saves Disk Space:** Chaining utilities with `|` streams data in memory, preventing slow writes of massive intermediate files to small laptop hard drives.
- **Defensive Scripting:** Teach `set -euo pipefail` and quote all variable expansions (`"${var}"`) to make Bash scripts reproducible and resilient against silent errors.
- **Surviving Outages:** Use `tmux` or `nohup` to ensure long-running analyses continue running uninterrupted on servers even when local Wi-Fi or electricity fails.
- **Empathetic Pedagogy:** Use participatory live coding, enlarged fonts, sticky-note signaling, and error destigmatization to build confidence in novice learners.
:::
