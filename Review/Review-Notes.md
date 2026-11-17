# Thesis revision: evidence and review notes

## Scope and publication

- The `Papers` folder contains exactly the six uploaded research PDFs. The supervisor form and sample thesis are excluded. The files are unchanged; hashes and page counts are in `paper-manifest.json`.
- Papers-only commit pushed to `main`: `d9017bb16da2aa3fc438e0753af76c0e42c17d1d`.
- The revised thesis and source are provided on `review/thesis-ieee-20261117` for review and file access. These changes have not been merged into `main`.
- The reference list is generated from `references.bib` using the standard BibTeX `ieeetr` style. The `cite` package supplies IEEE numeric citation formatting; `notoccite` keeps the front-matter figure/table lists from changing first-citation numbering in the body.
- The sample thesis was used to guide formal explanatory paragraphs, measurable objectives, figure explanations, and comparisons. Its topic, findings, and references were not imported.

## Supervisor feedback addressed

- Sections 1.1 and 1.2 distinguish background from the specific problem. Quantitative statements come from the supplied original studies, rather than unattributed population statistics.
- Table 1.1 compares voice communication, clinical decision, caller location, and dispatch support using common criteria. It distinguishes untested features from demonstrated capabilities.
- Sections 1.4 and 1.5 have no citations. Objectives identify measurements and tests; contributions are anticipated, not achieved results.
- Section 2.1 explains the progression from protocol-based calls through classifiers and language models to coordinated agents. It does not repeat the Chapter 1 comparison table.
- Each of six paper sections has Methodology, Results, Strengths, Limitations, and Summary. The Chapter 2 summary connects gaps to design choices and planned checks.
- Five original architecture figures are reproduced with source attribution and black frames. The Shekhar paper contains result figures, not a system architecture; its results are shown as a denominator-preserving table.
- Section 3.1 specifies functional and non-functional requirements, acceptance checks, human review, privacy, and failure handling. Section 3.1.1 uses the repository block diagram and two-part flowchart. All other former Chapter 3 sections are removed.
- Chapter 4 now gives an eight-week remaining Grad I plan from 23 November 2026 to the user-confirmed deadline of 17 January 2027. It includes a vector Gantt chart, 11 task packages, seven milestones, durations, dependencies, proposed team ownership, and a 14–16 January correction buffer. Internal dates and leads are proposed; the final deadline is confirmed.
- Chapter 5 now gives the initial conclusion: problem, principal research findings, identified gap, anticipated contribution, proposed direction, and next design steps. It does not invent implementation or evaluation results.
- Contents, figure/table lists, abbreviations, references, and cross-references are regenerated from actual content. The old template directions and phantom later chapters are removed from these lists.

## Source evidence used

Page numbers below are physical pages in the uploaded PDFs, not thesis page numbers.

| Source | Evidence locations | Important interpretation |
|---|---|---|
| Collaborative Medical Triage | pp. 1–4: record cleaning, three core agents and Figure 1; pp. 5–7: results and ablations | 3,360 main cases; 89.6% primary, 74.3% secondary, 74.2% reported overall accuracy after four rounds. The 100% result is on 258 cases selected for successful correction. Figure 5 instead labels n=3,660, which is flagged rather than silently reconciled. The arXiv v2 date is August 4, 2025; the file also has a 2026 copyright notice. |
| ED-Triage-Agent | pp. 4–7: architecture, roles, retrieval and 60-case protocol; pp. 8–10: results, timing and errors | 66.67% pre-vital and 80.00% post-vital exact ESI agreement. Two ESI-2 cases become ESI-3. “Zero undertriage” counts errors of at least two levels. Mean total processing is 48.95 s, not spoken-turn latency. The file is an unreviewed preprint. |
| Emergency Calls Assistant | pp. 4–6: workflow, Figure 1, 400 text samples and classifier; pp. 7–12: metrics and runtime | Main accuracy 92.70%; cross-validation mean 92.35%; separate 700-recording result 97.34%. Reported aggregate metrics are preserved. The 2.13 s path includes STT, preprocessing, and inference, not TTS. Ten calls in 5.6 s is throughput evidence, not a 0.56 s response per caller. |
| LLM for Ambulance Dispatch | pp. 1–5: setting, procedure, results and limitations | 98 analysed groups/392 requests; 45/48 unanimous and 30/44 majority agreement; six split groups have no majority reference. Overall 75/98 is retained. No reason is invented for the reduction from 100 sampled to 98 analysed groups. |
| DispatchMAS | pp. 4–7: 50 adult records, 100 synthetic calls, Figure 2 and mocked resources; pp. 9–12: expert evaluation; pp. 14–17: timing and limitations | 94% mocked auxiliary contact, 97% callback advice, 91% advice where considered necessary. Fixed “123 Main Street.” English-only communication experiments. Pacing is calculated from utterances, not measured computation/audio delay. |
| TriAgent | pp. 4–10: 1,000-case cohort, Figure 2, 49,000-note retrieval and trained classifier; pp. 11–18: results, comparisons, timing and limitations | 65.7% overall accuracy and 85.0% critical recall. A classifier trained on 415,423 encounters uses structured inputs. The comparison cannot isolate agent count. Median paths are 64 s and 186 s. The reused 20-case clinician review is formative, not an independent trial. |

## Figure handling

- Architecture figures are clipped from the supplied papers, retaining the original content. The added outer frame is black; no study architecture is invented.
- The project block diagram comes from `Thesis Diagrams/Proposed_Project_Block_Diagram.pdf`.
- The two project flowchart parts come from `Thesis Diagrams/Project_Flowchart.pdf`. The thesis copy excludes presentation headers/footers and changes only the first call-entry label from browser voice to telephone entry. The thesis captions identify the adaptation. Repository source diagrams are unchanged.
- Project diagrams use landscape pages to make labels readable.

## Items remaining outside this rewrite

- The older supervisor comments referred to a submission ending at Chapter 2. The current user request expressly includes Chapter 3, so the revised contents include its requested requirements and diagrams.
- The time plan and initial conclusion required by the later midterm rubric are now included as Chapters 4 and 5. Other previously flagged submission items remain: completing the Arabic cover, checking the full bilingual-front-matter requirement, and strengthening authoritative problem statistics and named professional-guideline references. This update does not claim that every remaining rubric item has been completed.
- The approved English/Arabic abstracts, English cover, acknowledgment, and existing Arabic back cover are preserved. The Arabic back cover still has the original student/title/supervisor placeholders and reversed academic-year text; completing it requires a separate cover-page edit. The body no longer contains template instructions.
- Existing contact statements in Section 1.6 remain reported outreach, not confirmed partnerships.
- The presentation's older indicative 12-week implementation timetable is not changed in this request. Chapter 4 is the remaining Grad I design/submission plan for the confirmed 17 January 2027 deadline; it retains the proposed division of leads but uses the new calendar.
- Hospital authorization, an available test telephone route, reviewed medical guidance, reviewed reference labels, and implementation/evaluation remain prerequisites. No clinical effectiveness, real ambulance dispatch, or regulatory compliance is claimed.

## Editable source

`main.tex`, `chapter1.tex`, `chapter2.tex`, `chapter2b.tex`, `chapter3.tex`, `chapter4.tex`, `chapter5.tex`, `references.bib`, `ieeetr.bst`, `.latexmkrc`, and `assets/` form the editable source. `make_time_plan.py` and the time-plan JSON files reproduce the Gantt chart and record the confirmed deadline and proposed task assignments. Build in this directory with:

```sh
latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
python3 assemble_final.py
```

The required packages are standard TeX Live packages plus PyMuPDF for final assembly. The final assembly step retains the approved covers, abstracts, and acknowledgment as exact PDF pages and restores links/bookmarks. The Arabic abstract does not require Arabic typesetting packages to rebuild.
