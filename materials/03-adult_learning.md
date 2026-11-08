---
title: Learning Principles
---

::: {.callout-tip}
#### Learning Objectives

- Distinguish between pedagogy (child learning) and andragogy (adult learning), identifying why traditional teacher-centred models fail in professional bioinformatics training.
- Apply Knowles’ six core assumptions of andragogy to the design and delivery of bioinformatics workshops.
- Mitigate imposter syndrome, terminal anxiety, and the psychological vulnerability adult scientists experience when learning computational tools.
- Transition instructor practice from an authoritative content transmitter to an empathetic facilitator of learning.
- Design learning activities centered on immediate problem-solving, local relevance, and active knowledge co-construction.
:::

## Pedagogy versus Andragogy

When designing training for researchers, university lecturers, laboratory technicians, or clinicians, instructors often fall back on the teaching models they experienced during primary or secondary school: an authoritative instructor delivering a lecture from the front of the room, followed by standardized tests. 

In professional training, this traditional teacher-centred approach frequently leads to disengagement, frustration, and poor retention.

::: {.callout-note}
## Defining the Terms

- **Pedagogy:** Literally "to lead the child" (from the Greek *paid*, child, and *agogos*, leading). It describes the art, theory, and methods of teaching children, where the instructor assumes full responsibility for determining what will be learned, how it will be learned, when it will be learned, and if it has been learned.
- **Andragogy:** Literally "to lead the adult" (from the Greek *aner*, adult). Popularized by Malcolm Knowles in 1968, andragogy refers to the art and science of helping adults learn. It recognizes that adults learn through fundamentally different psychological motivations, experiences, and cognitive frameworks than children.
:::

Even though the term "pedagogy" is colloquially used in academic discourse as a general synonym for teaching, this course strictly adopts an **andragogical framework**.

| Pedagogy (Child / Traditional) | Andragogy (Adult Learning) |
| :--- | :--- |
| Learner is dependent on teacher | Learner is self-directed |
| Teacher controls content & pace | Learner shares control & goals |
| Learner brings little experience | Rich reservoir of domain experience |
| Subject-centred (curriculum) | Problem-centred (real research) |
| External motivation (grades) | Internal motivation (career/publications) |
| Passive content absorption | Active, experiential facilitation |

: Pedagogy vs Andragogy in bioinformatics


## Knowles’ Core Assumptions of Andragogy

Malcolm Knowles and colleagues (2015) identified core assumptions that distinguish adult learners. Understanding these assumptions allows bioinformatics instructors to design empathetic, highly effective training programs:

**1. The Need to Know**

Adults need to know **why** they need to learn something before undertaking to learn it. They resist learning things simply because an instructor says "it's on the syllabus."

- *In Bioinformatics:* Never introduce a tool (e.g. `fastp` or `samtools`) with raw syntax alone. First demonstrate the problem: *"Here is an unaligned read file with adapter contamination. If we don't trim these sequences, 15% of our reads will fail to map to the reference genome, wasting your sequencing budget."*

**2. The Learner’s Self-Concept**

Adults need to be perceived as self-directed, autonomous individuals. When placed in situations where they are treated like passive schoolchildren or talked down to, they may experience cognitive friction and resentment.

- *In Bioinformatics:* Avoid rigid, lockstep dictation. Give learners autonomy over project choices, choice of example datasets, and space for exploratory debugging.

**3. The Role of Learner Experience**

Adults enter the classroom with a vast reservoir of prior professional and personal experience. This experience is a rich resource for learning, but it also carries entrenched mental models and cognitive biases.

- *In Bioinformatics:* Tap into their wet-lab knowledge. An experienced molecular biologist already understands PCR amplification, primer design, and DNA denaturation. Connect computational steps directly to the physical benchwork they already master:

  - *Quality scores $\rightarrow$ Gel electrophoresis band clarity.*
  - *Read alignment $\rightarrow$ Hybridization of primers.*
  - *PCR duplicates $\rightarrow$ Over-amplification on the thermal cycler.*

**4. Readiness to Learn**

Adults become ready to learn things when they experience a need to know them in order to cope with real-life situations, career requirements, or research challenges.

- *In Bioinformatics:* Trainees rarely attend workshops for abstract curiosity; they attend because they have sequencing data sitting on a hard drive that they cannot analyze, or a grant review demanding computational validation. Align workshop exercises with their immediate professional needs.

**5. Orientation to Learning**

Children are subject-centred (e.g. "We are studying History or Mathematics today"). Adults are **problem-centred** or **task-centred**.

- *In Bioinformatics:* Structure lessons around authentic scientific questions: *"Can we identify the transmission cluster in this hospital outbreak?"* rather than *"Chapter 3: The Syntax of BCFtools."*

**6. Motivation**

While adults respond to external motivators (e.g. promotion, certificates, higher salary), the most potent motivators are internal: job satisfaction, self-esteem, curiosity, and the desire to overcome a research barrier.

## Shifting Roles: From Teacher to Facilitator

Applying andragogy requires redefining the instructor's professional identity:

| The Traditional Teacher | The Learning Facilitator |
| :--- | :--- |
| "I hold the knowledge" | "We co-construct knowledge" |
| Transmits fixed syllabus | Manages the learning process |
| Controls timing and content | Responds to learner needs |
| Evaluates and grades students | Promotes self-evaluation |
| Focuses on presentation skills | Focuses on relational & process design skills |

: Table 1: Teacher versus facilitator

Following Knowles *et al.* (2015), the facilitator prepares in advance an operational structure involving:

1. **Preparing the learner:** Setting clear, realistic expectations and demystifying prerequisites before Day 1.
2. **Establishing an empathetic climate:** Creating an environment where questions are welcomed and errors are celebrated as learning moments.
3. **Mutual planning:** Diagnosing learner needs and negotiating priorities.
4. **Designing authentic learning experiences:** Using participatory live coding, micro-datasets, and localized biological problems.
5. **Evaluating and improving:** Gathering continuous formative feedback (e.g. sticky notes, minute papers) to adapt the course dynamically.


## Andragogy in Low-Resource Environments

In low-resource settings, the principles of adult learning intersect with systemic socio-economic and institutional realities:

- **High Opportunity Cost:** Adult professionals taking 3–5 days away from clinical wards, wet laboratories, or heavy teaching loads need to know their investment of time will immediately translate into tangible productivity. If a course wastes two days on failed installations, learners will disengage.
- **The "Lone Bioinformatician" Reality:** Many adult trainees are the sole individual from their institution attending the course. They carry the immense burden of needing to return home and become the computational expert, mentor, and pipeline developer for their entire department.
- **Empowerment Through Local Relevance:** Adult learners in LMICs are intensely motivated by solving regional health and agricultural problems (e.g. local AMR surveillance, malaria eradication, climate-resilient crop breeding). When instructors replace abstract examples with datasets reflecting their local reality, learning ceases to be an academic exercise—it becomes an act of scientific self-determination.


## Interactive Exercises for Future Trainers

These exercises will challenge you to identify andragogical principles in action and transform traditional teacher-centred lessons into engaging, facilitator-led workshops.

::: {.callout-exercise}
## Transforming a Teacher-Centred Lecture

You are reviewing an introductory lesson plan designed by a colleague for a two day variant-calling workshop for hospital microbiologists. 

The current lesson plan reads:

> *"09:00 - 10:30: Slide presentation (60 slides) explaining the history of sequencing technologies, Sanger chemistry, Illumina sequencing-by-synthesis, and quality score logarithmic mathematical formulas. Trainer will lecture from the front; students listen quietly."*

1. Identify three specific ways this lesson plan violates Knowles’ assumptions of andragogy.
2. What emotional or cognitive state will this design trigger in adult clinical microbiologists?
3. Redesign this 90-minute block into an andragogically sound, facilitator-led learning experience.

::: {.callout-hint}
Consider the "Need to Know", "Problem-Centred Orientation", and the value of active, hands-on participation.
:::

::: {.callout-answer}
### Andragogical Redesign

1. **Violations of Andragogy:**
   - **Passive Transmission (Pedagogical):** Treats learners as empty vessels to be filled with historical theory rather than self-directed practitioners.
   - **Lack of "Need to Know":** Memorizing Phred logarithmic math formulas ($P = 10^{-Q/10}$) in the abstract has zero immediate relevance to clinical practice.
   - **Subject-Centred, Not Problem-Centred:** Focuses on the history of sequencing instead of the clinical challenge the microbiologists care about.

2. **Likely Learner Reaction:**
   Boredom, fatigue, cognitive overload, and anxiety: *"Why am I sitting through 60 slides of history when I have patient samples to analyze? Is bioinformatics just endless theory?"*

3. **Facilitator-Led Redesign:**
   - **09:00 - 09:15 (The Clinical Hook):** Start with an authentic patient case study: *"A patient in our ICU has a hospital-acquired infection resistant to carbapenems. We sequenced the isolate. How do we know if our sequencing data is reliable enough to make a clinical decision?"*
   - **09:15 - 09:40 (Interactive Exploration):** Open a real FastQC report on screen. Have trainees explore the report in pairs. Ask them: *"Where does the quality drop? What does this red warning mean?"*
   - **09:40 - 10:10 (Targeted Explanation):** Briefly explain Phred quality scores and Illumina error profiles *in response to what they just observed* on their screens.
   - **10:10 - 10:30 (Hands-on Action):** Trainees run a read-trimming command on a micro-dataset and compare the "before" and "after" quality reports with their partner.
:::
:::

::: {.callout-exercise}
## Navigating the Expert-Novice Paradox in Live Classrooms

During the afternoon practical, Professor K., a distinguished 55-year-old professor of virology, is attempting to change directories in the terminal. They type `cd data` and receive `bash: cd: data: No such file or directory`. 

Professor K. visibly stiffens, crosses their arms, pushes their laptop away, and stops participating. When a roving helper approaches, Professor K. mutters: *"This computer interface is useless nonsense. In our wet lab, we generate real data; this is just academic games."*

1. What psychological dynamic is Professor K. experiencing?
2. Why is defensive frustration a common coping mechanism for senior adult experts learning computation?
3. How should the instructor/helper respond to de-escalate the tension, restore psychological safety, and re-engage Professor K.?

::: {.callout-answer}
### Facilitator Intervention

1. **Psychological Dynamic:**
   Professor K. is experiencing acute **cognitive vulnerability and loss of self-concept**. As a senior, highly respected virologist, having a computer tell them they made a mistake ("No such file or directory") threatens their professional identity and sense of competence.

2. **Why Defensive Frustration Occurs:**
   When adult experts feel deskilled, dismissing the subject ("useless nonsense", "academic games") is a natural psychological defense mechanism to protect self-esteem and deflect perceived inadequacy.

3. **Facilitator Response:**
   - **Validate Domain Expertise First:** Empathize and reaffirm their high status: *"Professor K., you are completely right that wet-lab data generation is the foundation of all biology. Without your viral culture work, bioinformatics has nothing to compute."*
   - **De-escalate the Error:** Demystify the error as a mechanical miscommunication, not an intellectual failure: *"The terminal is completely literal and a bit stubborn. It only says 'No such file' because our current working directory is one level above where the folder sits. It's like dialing a phone number missing one area code."*
   - **Guide, Don't Take Over:** Never grab their keyboard! Guide them verbally: *"Let's type `pwd` together to see where we are... Perfect. Now type `ls` to see what is in this room... Ah, look, the folder is called `raw_data`. If we type `cd raw_data`, it will jump right in."*
   - **Affirm Success:** When it succeeds: *"Excellent! Now your sequencing reads are right in front of you."*
:::
:::

## Summary

::: {.callout-tip}
#### Key Points

- **Andragogy Governs Adult Learning:** Adult learners are self-directed, bring vast reservoirs of domain experience, and learn best when knowledge is problem-centred, immediately applicable, and internally motivated.
- **Connect Computational Syntax to Wet-Lab Concepts:** Ground abstract command-line concepts in the physical biology they already understand (e.g. connecting quality scores to gel electrophoresis or PCR duplicates to over-cycling).
- **Shift from Teacher to Facilitator:** Abandon the "sage on the stage" model. Successful trainers manage the learning environment, design authentic practical experiences, and facilitate active inquiry rather than delivering monologues.
- **Maximize Relevance in Low-Resource Contexts:** Respect the high opportunity cost of adult professional training by using authentic local health and agricultural datasets that empower trainees to solve pressing regional challenges.
:::
