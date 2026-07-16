# fMRI Workshop

> A hands-on, application-focused workshop that takes complete beginners from raw MRI data to a reproducible fMRI analysis on an HPC cluster.

The emphasis is on actually running the pipeline — preprocessing, the GLM, quality control, troubleshooting, and post-processing — with just enough principles and experimental design to use them well.

## Who it's for

True beginners with no programming or fMRI background. A basic grasp of applied statistics and comfort reading papers and writing academically are expected; no mathematics or theoretical-statistics background is needed.

## Sessions

| # | Session | Focus | Key tools |
|---|---------|-------|-----------|
| 1 | Linux essentials | the command line | bash, paths, scripting, permissions |
| 2 | HPC & SLURM | clusters and jobs | ssh, modules, sbatch, arrays |
| 3 | Developer tools | version control & environments | git/GitHub, VS Code, conda, containers, Jupyter |
| 4 | Overall Pipeline 1 | scanner, data, software | DICOM/NIfTI, BIDS, AFNI, fMRIPrep |
| 5 | Overall Pipeline 2 | preprocessing | sswarper2, afni_proc.py |
| 6 | Design & GLM | experimental design, modeling | stimulus timing, GLM, contrasts |
| 7 | Quality Control | qualitative + quantitative QC | APQC, MRIQC, gen_ss_review |
| 8 | Troubleshooting | reading logs, failure types | SLURM, containers |
| 9 | Post-processing | secondary analysis | group, connectivity, ICA, MVPA |
| 10 | Projects & Writing | reproducibility, Methods | NA |

## What's inside

- **[Syllabus](MRI_workshop.md)** — objectives, prerequisites, and the ten sessions (topics, readings, assignments).
- **[Slides](Slides/working/)** — per-session teaching slides in Marp-compatible Markdown.

## Companion handbook

The sessions draw on the [fMRI Data Processing Manual on HPC](https://qiuyuyu3.github.io/fMRI-Data-Processing-Manual-on-HPC/), which contains the step-by-step reference material.

## Instructor

Qiuyu Yu, Human Development and Family Science (HDFS), Auburn University (qiuyuyu.psych@gmail.com)
