---
title: Software Installation
---

::: {.callout-tip}
#### Learning Objectives

- Explain how operating systems discover and execute programs via the `$PATH` environment variable and file permissions.
- Evaluate the spectrum of bioinformatics installation methods (static binaries, Conda/Mamba, language package managers, system packages, and source compilation) based on resource constraints.
- Manage isolated computational environments using Mamba and Micromamba to prevent dependency conflicts and avoid memory-exhaustion crashes.
- Deploy offline installation workflows (such as `conda-pack` and USB-distributed binary caches) in classrooms with limited or zero internet connectivity.
- Identify and resolve common installation failures, including missing shared libraries, architecture mismatches (x86_64 vs. ARM64), and permission denials.
- Design pre-course installation clinics and automated verification scripts to ensure zero classroom downtime on day one.
:::

## Introduction: The Installation Dilemma in Bioinformatics

Few tasks induce as much anxiety in beginner bioinformaticians as installing software. Unlike consumer applications installed with a single click from an app store, bioinformatics tools often exist as command-line binaries, Python scripts, R packages, or raw C/C++ source code. 

In low-resource environments, software installation is compounded by three systemic hurdles:

1. **Limited or Unstable Bandwidth:** Downloading hundreds of megabytes of package indices and dependencies during a live workshop can overwhelm classroom networks or exhaust mobile data bundles.
2. **Hardware Constraints:** Older laptops with 4 GB of RAM frequently crash when running memory-intensive dependency solvers (such as classic Conda).
3. **Restricted Permissions:** Learners in institutional computer labs often lack administrative (`sudo` or root) privileges, rendering system-wide package managers (`apt`, `yum`) unusable.

```
┌────────────────────────────────────────────────────────────────────────┐
│                   THE WORKSHOP INSTALLATION TRAP                       │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│   Scenario A: Live Installation during Workshop                        │
│   • 09:00 - Class starts: "Please install Conda and tools"             │
│   • 09:30 - Wi-Fi collapses under 30 concurrent downloads              │
│   • 11:00 - Instructors still troubleshooting missing C++ libraries    │
│   • 12:30 - Lunch break: 0 biology taught, learners demoralized        │
│                                                                        │
│   Scenario B: Resource-Aware Pre-Flight Strategy                       │
│   • Week before: Pre-flight test script or pre-packaged USB delivery   │
│   • 09:00 - Class starts: Tools ready, immediate hands-on analysis!    │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

As an instructor, your goal is to equip learners with sustainable installation skills for their future research while safeguarding workshop instructional time from installation chaos.


## How the Operating System Finds Software: Demystifying `$PATH`

Before teaching package managers, instructors must demystify how the operating system executes a command. Novice learners frequently encounter the error `command not found` and assume their installation failed, when in reality the executable simply resides in an unindexed folder.

### The `$PATH` Environment Variable

When a user types `fastp` and hits **Enter**, the operating system does not search the entire computer. Instead, it consults an environment variable called `$PATH`—a colon-separated list of directories where executable programs reside.

```
User types: fastp
     │
     ▼
Consult $PATH:  /usr/local/bin : /usr/bin : /bin : /home/user/.local/bin
                      │              │        │               │
                      ▼              ▼        ▼               ▼
                 Check here     Check here  Found!        (Skipped)
                 (Not found)    (Not found) [Execute]
```

To see which directories are currently searched:
```bash
echo "$PATH"
```

To determine which specific binary is being executed:
```bash
which fastp
# or
type -a fastp
```

### Making a Program Executable: Permissions

In Unix, a downloaded file cannot run simply because it has a particular extension. It must have the **executable (`x`) permission** bit set:

```bash
# Check file permissions
ls -l my_script.sh
# -rw-r--r-- 1 trainee trainee 1024 Oct 1 09:00 my_script.sh (Cannot run!)

# Grant execute permission
chmod +x my_script.sh

# Now it can run
ls -l my_script.sh
# -rwxr-xr-x 1 trainee trainee 1024 Oct 1 09:01 my_script.sh (Executable!)
```

::: {.callout-note}
## The `.` in `./program`
Beginners often ask: *"Why do I have to type `./fastp` when I am inside the folder containing `fastp`, but I can type `ls` from anywhere?"*

- `ls` lives in `/bin`, which is listed in `$PATH`.
- For security reasons, the current working directory (`.`) is almost never included in `$PATH`.
- Typing `./program` explicitly instructs the shell: *"Look right here in the current folder (`.`) and execute `program`."*
:::


## The Spectrum of Installation Methods

Bioinformatics tools can be installed via several distinct modalities. Understanding the trade-offs allows trainers to choose the right approach for each setting:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   SPECTRUM OF INSTALLATION METHODS                     │
├─────────────────────┬───────────────────┬──────────────┬───────────────┤
│ Method              │ Ease for Beginners│ Root Needed? │ Offline-Ready?│
├─────────────────────┼───────────────────┼──────────────┼───────────────┤
│ Static Binaries     │ ★★★★★ (Easiest)   │ No           │ ★★★★★         │
│ Containers (Appt.)  │ ★★★★☆             │ No           │ ★★★★★         │
│ Micromamba / Mamba  │ ★★★★☆             │ No           │ ★★★★☆         │
│ Language Pkgs (pip) │ ★★★☆☆             │ No           │ ★★★☆☆         │
│ System Pkgs (apt)   │ ★★★☆☆             │ Yes (Root)   │ ★★☆☆☆         │
│ Compile from Source │ ★☆☆☆☆ (Hardest)   │ Sometimes    │ ★☆☆☆☆         │
└─────────────────────┴───────────────────┴──────────────┴───────────────┘
```

### 1. Static and Pre-Compiled Binaries: The Low-Resource Champions

A **statically linked binary** has all of its supporting libraries compiled directly into a single executable file. It has no external dependencies.

- **Examples:** `seqkit`, `minimap2`, `fastp`, `samtools` (standalone releases).
- **Why they excel in low-resource settings:**
  - Zero dependencies: no Python, Perl, or Conda required.
  - Extremely small download footprint (typically 5 MB – 25 MB).
  - Can be downloaded once, placed onto a USB drive, copied into any user's `~/.local/bin/` folder, and executed immediately.


## Modern Package Management: Conda, Mamba, and Micromamba

For software with complex multi-language dependencies, package managers are essential. In bioinformatics, the **Conda** ecosystem (specifically the **Bioconda** and **Conda-forge** channels) is the standard.

```
       ┌─────────────────────────────────────────────────┐
       │                 THE CONDA ECOSYSTEM             │
       ├────────────────────────┬────────────────────────┤
       │ conda-forge            │ bioconda               │
       │ (General scientific    │ (Specialized genomic & │
       │  libraries, Python, R) │  bioinformatics tools) │
       └────────────────────────┴────────────────────────┘
                                │
                                ▼
       ┌─────────────────────────────────────────────────┐
       │   Client: Mamba / Micromamba (C++ fast solver)  │
       └─────────────────────────────────────────────────┘
```

### Why Classic Conda Fails on Low-Resource Hardware

Classic `conda` was written in Python and uses a Boolean Satisfiability (SAT) solver to resolve dependencies. As the Bioconda repository grew to tens of thousands of packages, solving an environment became computationally intensive:

- Classic Conda often requires **2.5 GB to 4 GB of RAM** just to calculate the dependency graph.
- On an older 4 GB RAM student laptop, the OS runs out of memory, triggers disk swapping, and kills the process with `Killed` or hangs indefinitely ("Solving environment: \").

### The Solution: Mamba and Micromamba

**Mamba** replaces Conda's Python solver with a high-performance C++ solver (`libsolv`), reducing solve times from 20 minutes to 15 seconds while consuming a fraction of the RAM.

**Micromamba** goes one step further: it is a single, self-contained C++ executable (~10 MB) that requires **no existing Python installation** and can create complete bioinformatics environments from scratch.

::: {.callout-tip}
## Best Practice: Always Teach Micromamba / Mamba
When teaching package management in low-resource workshops, always recommend Mamba or Miniforge instead of the bloated Anaconda Distribution (which installs over 5 GB of unneeded data science libraries).
:::

### Essential Environment Hygiene: The "Never Base" Rule

One of the most frequent support tickets in bioinformatics is a corrupted base environment. 

**Rule to teach your learners:** *Never install research tools into the `base` environment.* Always create dedicated, isolated environments for distinct projects:

```bash
# Create a dedicated environment for bacterial genome assembly
mamba create -n assembly_env -c conda-forge -c biococonda \
  spades fastp quast

# Activate the environment
mamba activate assembly_env

# Check which environments exist
mamba env list

# Deactivate when finished
mamba deactivate
```


## Managing Python and R Dependencies

Bioinformaticians frequently work with custom Python and R scripts that require community libraries.

### 1. Python Environments
Never install packages globally using `sudo pip install`. Instead:

- Use Python's built-in virtual environment module:
  ```bash
  python3 -m venv my_project_env
  source my_project_env/bin/activate
  pip install pandas biopython matplotlib
  ```
- **Modern Alternative:** In resource-constrained environments, tools like `uv` (written in Rust) install Python wheels 10–50 times faster than `pip` and manage local Python versions with minimal disk footprint.

### 2. R Packages and Bioconductor
R packages in bioinformatics are split between CRAN and **Bioconductor**:

```r
# Installing BiocManager and genomic packages
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("DESeq2")
```

::: {.callout-warning}
## The Hidden C Library Trap in R
Many R bioinformatics packages (e.g. `DESeq2`, `RCurl`, `xml2`) are wrappers around underlying C/C++ libraries. Installing them from source in R on a clean Linux machine will fail if system libraries like `libxml2-dev`, `libcurl4-openssl-dev`, or `libssl-dev` are missing.

*Trainer Advice:* If students are working on Linux or WSL, prefer installing R packages via Conda/Mamba (`mamba install r-deseq2`), which installs the underlying compiled system libraries automatically without requiring root permissions.
:::


## Strategies for Low-Bandwidth and Offline Workflows

How can instructors deliver a hands-on workshop when the classroom internet is unreliable or completely absent?

```
┌────────────────────────────────────────────────────────────────────────┐
│                   OFFLINE CONDA PACKING WORKFLOW                       │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  1. Instructor Machine (High-Speed Internet at Home/Office):           │
│     mamba create -n course_env -c bioconda fastp bwa samtools          │
│     pip install conda-pack                                             │
│     conda-pack -n course_env -o course_env.tar.gz                      │
│                                                                        │
│  2. Physical Transfer (USB Thumb Drives):                              │
│     Copy course_env.tar.gz onto 5 USB flash drives                     │
│                                                                        │
│  3. Student Machine (Offline Classroom):                               │
│     mkdir -p ~/miniconda3/envs/course_env                              │
│     tar -xzf /media/usb/course_env.tar.gz -C ~/miniconda3/envs/course_env│
│     conda activate course_env                                          │
│     * Tools are immediately available with ZERO network traffic!       │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

### 1. `conda-pack`: Transporting Pre-Built Environments
`conda-pack` is an open-source tool that archives an existing Conda environment into a `.tar.gz` file. 
- It preserves all compiled binaries, dependencies, and path prefixes.
- Students unpack the archive into their local `envs/` directory and activate it immediately.
- **Advantage:** Bypasses all package index downloads, dependency resolution, and compilation.

### 2. Standalone Binary Bundles
For courses focusing on standard sequencing pipelines (QC, mapping, variant calling), create a single zipped folder containing pre-compiled static Linux/macOS binaries (`fastp`, `samtools`, `minimap2`, `bedtools`).
Students unzip the folder and add it to their `$PATH` in one command:
```bash
unzip course_binaries.zip -d ~/
echo 'export PATH="$HOME/course_binaries:$PATH"' >> ~/.bashrc
source ~/.bashrc
```


## Pedagogical Guidelines: Zero-Downtime Installation

### 1. The Pre-Course Installation Clinic
Never schedule installation as the opening lecture on Day 1. Instead:

- Host a drop-in virtual "Installation Clinic" 2–3 days prior to the course.
- Assign teaching assistants or workshop helpers to test student machines one-on-one.
- If a student cannot resolve their issues before Day 1, transition them to a pre-configured backup option (e.g. a cloud instance, web-based platform, or loaner USB with pre-packaged binaries).

### 2. Automated Pre-Flight Verification Scripts
Provide learners with a simple, self-contained shell script that checks whether all required tools are correctly installed and functional before the course begins:

```bash
#!/usr/bin/env bash
# ==============================================================================
# preflight_check.sh: Verifies required workshop tools
# ==============================================================================

echo "Checking workshop tools..."
TOOLS=("fastp" "bwa" "samtools" "spades" "python3")
MISSING=0

for tool in "${TOOLS[@]}"; do
    if command -v "${tool}" >/dev/null 2>&1; then
        echo "  [OK] ${tool} is installed: $(which ${tool})"
    else
        echo "  [FAIL] ${tool} is NOT found in your \$PATH!"
        MISSING=$((MISSING + 1))
    fi
done

if [ ${MISSING} -eq 0 ]; then
    echo "SUCCESS: All tools verified! You are ready for the workshop."
else
    echo "WARNING: ${MISSING} tool(s) missing. Please contact a trainer."
fi
```


## Interactive Exercises for Future Trainers

These exercises will challenge you to troubleshoot real-world installation failures and plan resilient teaching workflows.

::: {.callout-exercise}
## Diagnosing the "Command Not Found" Paradox

During a morning practical, a student downloads the static binary for `seqkit` from GitHub. They place it in their home directory `~/Downloads/`. In their terminal, they type:

```
$ cd ~/projects/malaria/
$ seqkit stats sample.fasta
bash: seqkit: command not found
```

In distress, the student raises their hand: *"I downloaded seqkit, but my computer says it isn't there! Did the download fail?"*

1. What are the two distinct computational reasons why this command failed?
2. How would you guide the student to diagnose and fix the problem using terminal commands?
3. What long-term configuration step should you teach the student so they can execute `seqkit` from any directory in the future?

::: {.callout-hint}
Check whether the directory containing `seqkit` is in the user's `$PATH`, and whether the downloaded file has execute permissions.
:::

::: {.callout-answer}
### Diagnosis & Remediation

1. **Root Causes:**
   - **Path Disconnect:** The binary is in `~/Downloads/`, but `~/Downloads/` is not in `$PATH`. When the user is in `~/projects/malaria/`, the shell cannot find it.
   - **Missing Permissions:** Freshly downloaded files from web browsers typically lack the executable bit (`x`).

2. **Diagnosis & Immediate Fix:**
   ```bash
   # Check if file exists and inspect permissions
   ls -l ~/Downloads/seqkit
   
   # Grant execute permission
   chmod +x ~/Downloads/seqkit
   
   # Run with explicit path
   ~/Downloads/seqkit stats sample.fasta
   ```

3. **Permanent Solution:**
   Move the binary to a standard user directory that is already in `$PATH` (or add a custom directory to `$PATH` in `.bashrc`):
   ```bash
   mkdir -p ~/.local/bin
   mv ~/Downloads/seqkit ~/.local/bin/
   echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```
:::
:::

::: {.callout-exercise}
## Selecting the Best Installation Strategy

You are designing a 4-day metagenomics workshop for 20 master's students at an institute in East Africa. The institutional computer lab has 10 desktop machines running an old version of Ubuntu Linux without internet access. Students will bring 10 personal Windows laptops connected to an unstable 4 Mbps shared mobile Wi-Fi hotspot.

The course requires `fastp`, `megahit`, and `kraken2` (with an 8 GB mini-database).

For each of the two groups (Lab Desktops vs. Personal Windows Laptops), select the most robust installation and distribution strategy. Justify your choices based on internet bandwidth, administrative permissions, and hardware constraints.

::: {.callout-answer}
### Strategic Deployment Plan

1. **For the Lab Linux Desktops (No Internet, Unknown Root Access):**
   - **Strategy:** Standalone `.sif` container images via **Apptainer** or pre-packed Conda archives via **`conda-pack`**, distributed via USB flash drives.
   - **Justification:** Because there is zero internet access, network-based package managers are impossible. Apptainer `.sif` files or unpacked `conda-pack` folders run entirely offline without requiring root access or internet connectivity. The 8 GB Kraken2 database can be copied directly to local `/scratch` or `/data` partitions from the same USB drive.

2. **For Personal Windows Laptops (Unstable 4 Mbps Hotspot):**
   - **Strategy:** Provide a pre-configured **WSL2 (Windows Subsystem for Linux)** environment or lightweight Linux live USB drives pre-loaded with the software, OR distribute `conda-pack` archives for Windows/WSL via USB.
   - **Justification:** Attempting to have 10 Windows laptops download Conda environments and the 8 GB Kraken2 database over a shared 4 Mbps hotspot will take days and exhaust data quotas. Delivering all tools and the database offline via USB flash drives eliminates bandwidth dependency entirely.
:::
:::


## Summary

::: {.callout-tip}
#### Key Points

- **The `$PATH` Variable Controls Execution:** The operating system searches only directories listed in `$PATH`. Understanding paths and the executable bit (`chmod +x`) resolves the vast majority of "command not found" errors.
- **Prefer Mamba/Micromamba Over Classic Conda:** Classic Conda is prone to memory exhaustion (OOM crashes) on 4 GB–8 GB laptops due to its heavy Python solver. Mamba and Micromamba solve environments rapidly with minimal RAM.
- **Isolate Project Environments:** Enforce the "Never Base" rule—never install research tools directly into the base Conda environment.
- **Static Binaries are Low-Resource Allies:** Standalone compiled binaries (e.g. `fastp`, `seqkit`) have zero dependencies, tiny download footprints, and can be circulated offline via USB.
- **Bypass Classroom Bandwidth with Offline Packaging:** Tools like `conda-pack` and pre-built container images allow trainers to distribute complete, complex pipelines on USB flash drives without consuming a single megabyte of classroom internet.
- **Never Waste Day One on Installation:** Run pre-course virtual installation clinics and provide automated pre-flight check scripts to ensure learners are ready to analyze data from minute one.
:::
