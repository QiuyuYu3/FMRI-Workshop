# fMRI workshop

**Instructor:** Qiuyu Yu, Human Development and Family Science (HDFS), Auburn University

**Contact:** qiuyuyu.psych@gmail.com

# Syllabus

## How to use this syllabus

- **This is a hands-on workshop.** You learn by running, breaking, and fixing things, not by reading alone. Feeling lost during the first couple of weeks is normal.
- **"Required" means recommended, not mandatory.** There is a lot of material; treat the readings and assignments as strong recommendations and budget your time accordingly rather than attempting everything at once.
- **Form a study group.** Reviewing each other's assignments and progress helps you learn faster and catch mistakes earlier.
- **Ask when you are stuck.** Use Q&A forums (e.g. Neurostars) and software-specific boards (e.g. the AFNI message board); most questions have already been asked. When posting, include a minimal reproducible example, the exact error text, and your software/container versions; this yields a useful answer far faster than a vague report.
- **Who this is for.** This workshop is designed for true beginners: no programming experience and no prior fMRI theory or data-analysis background are required. You should, however, have a basic grasp of applied statistics and be comfortable reading papers and writing academically. No mathematics or theoretical-statistics background is needed.
- **Textbooks.** If you are short on time, read *Principles of fMRI* (Wager & Lindquist); with more time, add the other two. All three are classic, carefully chosen texts. The *Principles of fMRI* video course covers a great deal, so some parts may feel fast or shallow; if a video is unclear, skip it or consult the companion book rather than dwelling on it.
- **HPC access.** First check whether your university provides an HPC cluster. If not, install Linux and the required software on your own computer. If you cannot install anything locally either, at minimum learn how to write the CLI commands.
- **Get set up early.** HPC accounts and data downloads can take time to arrange, so arrange them before you need them. If you do not have your own dataset, start from an open one (e.g. OpenNeuro).
- **Keep a decision log.** Record what you chose and why: template, number of TRs dropped, censoring thresholds. This aids reproducibility and makes writing your Methods easier.

## Format

- Prerequisites: complete the Prerequisite section before Session 1 (especially Linux and Python basics).
- What to bring: an HPC account, a laptop, and (ideally) your own dataset.

## Learning Objectives

- Basic understanding of Bash syntax and HPC principles.
- Familiarity with CLI-based analysis software (AFNI, fMRIPrep) and proficiency in its use.
- Proficiency in the fMRI preprocessing workflow on HPC, from reconstruction through quality control, with awareness of how it differs across modalities.
- Understanding of experimental design and the GLM, from stimulus timing files to contrasts.
- Ability to troubleshoot failed jobs and recognize silent errors.
- Basic understanding of post-processing (secondary analysis).
- Ability to write a clear, reproducible Methods section.

# Textbook

**Required**

- [**Principles of fMRI by Tor D. Wager and Martin A. Lindquist**](https://leanpub.com/principlesoffmri)
    - Great introduction for newbies to get started within only 200 pages.

**Optional**

- **Handbook of Functional MRI Data Analysis** by Russell A. Poldrack
    - Brief introduction of fMRI data analysis, not a hands-on manual.
- **Functional Magnetic Resonance Imaging** by Scott A. Huettel, Allen W. Song, and Gregory McCarthy
    - ***Highly Recommend*** Classic textbook on fMRI, very comprehensive. The first few chapters can be skipped if you find them difficult to understand (e.g. the formula section)

# Prerequisite

**Python**

Very friendly introductory videos and tutorials!

- https://www.youtube.com/playlist?list=PLtfEWMIgWS22MMZjPIzBRE2cHhMcvEKwp

- https://neuraldatascience.io/

**Linux**

- https://andysbrainbook.readthedocs.io/en/latest/unix/Unix_Intro.html

- https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/introduction/

**HPC**

Generally, each university’s HPC team provides relevant tutorials or wikis. If not, there are also plenty of HPC-related videos on YouTube.

- https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/introduction/

## Session 1: Principles

### Topics

- Introduction to bash, Linux, HPC.
- Command-line essentials: paths, redirection and pipes, reading logs (grep/less/tail).
- How to install packages, Singularity, and create an environment.
- How to submit a job on HPC (login node vs compute node; tmux for long sessions).
- How to use GitHub and Jupyter Notebook.

### Reading

- **Required**
    - https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/introduction/
    - https://andysbrainbook.readthedocs.io/en/latest/unix/Unix_Intro.html
- **Optional**
    - https://missing.csail.mit.edu/ (MIT: The Missing Semester of Your CS Education)
    - https://www.hpc-carpentry.org/ (HPC Carpentry: Intro to High-Performance Computing)

### Assignment

- Submit a job.
- Create a repository.
- Create a Python environment. Use (or download) Singularity.
- Create and run a Jupyter Notebook (via your HPC's portal, e.g. OnDemand).

## Session 2: Overall Pipeline 1

### Topics

- How an MRI machine works and the data collection procedure.
- From DICOM to NIfTI and BIDS.
- Data ethics and de-identification (defacing, removing PII).
- Where to get data: open datasets (e.g. OpenNeuro).
- Preprocessing pipeline overview.
- Software for fMRI: AFNI, fMRIPrep, XCP-D. Other modalities (brief): QSI-Prep / MRtrix3 (diffusion), FreeSurfer (surface).

### Reading

- **Required**
    - https://www.youtube.com/playlist?list=PLfXA4opIOVrGHncHRxI3Qa5GeCSudwmxM Module 1-8
    - https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/preprocessing-pipeline/
    - *Principles of fMRI*: Ch 1-4 (intro, why fMRI, imaging types, brain mapping)
- **Optional**
    - *Principles of fMRI*: Ch 7-12 (fMRI basics & data structure, MR environment & safety, PET vs MRI, MRI physics, physiological basis, spatial/temporal resolution)
    - Richard C. Reynolds, Daniel R. Glen, Gang Chen, Ziad S. Saad, Robert W. Cox, Paul A. Taylor; Processing, evaluating, and understanding FMRI data with afni_proc.py. Imaging Neuroscience 2024; 2 imag–2–00347. doi: https://doi.org/10.1162/imag_a_00347
    - Esteban, O., Markiewicz, C.J., Blair, R.W. et al. fMRIPrep: a robust preprocessing pipeline for functional MRI. Nat Methods 16, 111–116 (2019). https://doi.org/10.1038/s41592-018-0235-4

### Assignment

- Pull a preprocessing container (e.g. fMRIPrep) via Singularity.
- Read the documentation/landing pages of the main software (AFNI, fMRIPrep, XCP-D, etc.).
- Survey and summarize which software fits which modality / analysis (produce a short comparison table: modality or analysis -> recommended software -> why).

## Session 3: Overall Pipeline 2

### Topics

- Why preprocess: noise from the subject (motion, physiology) and scanner (slice timing, drift, distortion); raising SNR.
- Core steps: remove initial TRs, slice-timing, motion correction, co-registration, segmentation, normalization, smoothing, mask, scaling.

### Reading

- **Required**
    - https://www.youtube.com/playlist?list=PLfXA4opIOVrGHncHRxI3Qa5GeCSudwmxM Module 13-14
    - *Principles of fMRI*: Ch 16 (BOLD signal & noise), Ch 17 (preprocessing), Ch 21 (artifacts and noise)
    - https://andysbrainbook.readthedocs.io/en/latest/AFNI/AFNI_Short_Course/AFNI_04_Preprocessing.html
- **Optional**
    - *Functional Magnetic Resonance Imaging*: Ch 8 (Signal, Noise, and Preprocessing of fMRI Data).

### Assignment

- Convert a raw dataset to BIDS format and inspect its structure (optional).
- Submit a preprocessing job.
- Read the provided preprocessing scripts and work out what each step does.
- (Advanced) Write your own fMRIPrep preprocessing script.
- Write a short Methods paragraph describing the preprocessing.

## Session 4: Experimental Design and GLM

### Topics

- Experimental design: block vs event, and design efficiency.
- From design to stimulus timing files (including amplitude/duration modulation).
- The BOLD signal and HRF convolution.
- The GLM and contrasts (GLT).
- Multiple comparisons and correction.

### Reading

- **Required**
    - https://www.youtube.com/playlist?list=PLfXA4opIOVrGHncHRxI3Qa5GeCSudwmxM Module 11-12, 15-21
    - *Principles of fMRI*: Ch 14 (experimental design), Ch 15 (resting state & non-experimental designs), Ch 18 (GLM), Ch 19 (conditions & contrasts), Ch 20 (flexible hemodynamics & mis-modeling), Ch 23 (multiple comparisons)
- **Optional**
    - *Functional Magnetic Resonance Imaging*: Ch 9 (Experimental Design).

### Assignment

- Find a task-fMRI paper and interpret its Methods section
- Compute the stimulus timing files for the provided task.
- (Optional) Build a modulated timing file (amplitude or duration), e.g. a value regressor for an RL-style task.

## Session 5: Quality Control

### Topics

- Qualitative check (fMRIPrep & AFNI).
- Quantitative check (MRIQC & AFNI).

### Reading

- **Required**
    - https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/quality-control/
    - https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/rs1/
    - Reynolds RC, Taylor PA and Glen DR (2023) Quality control practices in FMRI analysis: Philosophy, methods and examples using AFNI. Front. Neurosci. 16:1073800. doi: 10.3389/fnins.2022.1073800
    - Paul A. Taylor, Daniel R. Glen, Gang Chen, Robert W. Cox, Taylor Hanayik, Chris Rorden, Dylan M. Nielson, Justin K. Rajendra, Richard C. Reynolds; A Set of FMRI Quality Control Tools in AFNI: Systematic, in-depth, and interactive QC with afni_proc.py and more. Imaging Neuroscience 2024; 2 imag–2–00246. doi: https://doi.org/10.1162/imag_a_00246
    - Provins C, MacNicol E, Seeley SH, Hagmann P and Esteban O (2023) Quality control in functional MRI studies with MRIQC and fMRIPrep. Front. Neuroimaging 1:1073734. doi: 10.3389/fnimg.2022.1073734
- **Optional**
    - https://youtube.com/playlist?list=PL_CD549H9kgoK9mGH3IVm1Ai6pB_Ns64K&si=qN-7pKMLr-WJAuKI

### Assignment

- Rate one subject's APQC & fMRIPrep report HTML.

## Session 6: Troubleshooting

### Topics

- Reading logs: find the first real error.
- Common failure types: job-level (memory/walltime/scratch), environment/container, and script-level.
- Silent errors: it runs but the result is wrong.
- Debugging strategy; special topics (distortion correction, multi-echo, despiking, censoring and denoising strategy, template/parcellation choice, etc.).

### Reading

- **Required**
    - https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/special-issues/
    - https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/bfc/
    - https://discuss.afni.nimh.nih.gov/ (AFNI message board)
    - https://neurostars.org/ (Neurostars: fMRIPrep / BIDS / general)

### Assignment

- Diagnose a failed job: find the first real error and fix it (path/template/timing).
- (Optional) Run distortion correction on one subject and judge it in QC.
- (Optional) Re-run with a different template and compare how the results change.

## Session 7: Postprocessing

### Topics

- Group-level analysis.
- ROI-based analysis.
- Functional connectivity, resting-state, and network/graph analysis.
- Independent component analysis (ICA).
- Structural / morphometric analysis.
- Multimodal integration.
- Machine learning / MVPA.

### Reading

- **Required**
    - *Principles of fMRI*: Ch 22 (group analysis), Ch 24 (assessing brain connectivity), Ch 25-26 (multivariate analysis / MVPA)
- **Optional**
    - *Functional Magnetic Resonance Imaging*: Ch 10 (Statistical Analysis I: Basic Analyses), Ch 11 (Statistical Analysis II: Advanced Approaches).

### Assignment

- In your own words, summarize which data / task each post-processing method suits, and when it works best.
- Find a paper you are interested in and analyze its post-processing.
- (Optional) Run your own post-processing analysis (e.g. a group-level test with cluster correction).

## Session 8: Projects and Writing

### Topics

- Present your own project (question, design, pipeline and analysis choices).
- Writing: what to watch out for (clear, reproducible Methods; reporting QC, exclusions, versions, correction).
- Reproducibility and data/code sharing.

### Reading

- **Required**
    - *Principles of fMRI*: Ch 5 (limitations in brain-map inferences), Ch 6 (how to lie with brain imaging)

### Assignment

- Write a simple project proposal (question, design, planned pipeline and analysis).
- (Optional) Draft a Methods section for it.