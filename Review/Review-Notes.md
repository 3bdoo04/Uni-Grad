# Thesis revision: evidence and review notes

## Scope and publication

- The `Papers` folder contains the six recent research PDFs plus the five newly supplied historical source files: four PDFs and the original 911.gov link text file. The supervisor form and sample thesis are excluded. All 11 uploaded files are unchanged; hashes, file types, and PDF page counts are in `paper-manifest.json`.
- The original six papers were added to `main` in `d9017bb16da2aa3fc438e0753af76c0e42c17d1d`. Only the five new historical source files were added to `main` in `2a14d08c03a8aabde28d81a16ec5d02c7b265d98`. No revised thesis files are included in either papers-only update.
- The revised thesis and source are provided on `review/thesis-ieee-20261117` for review and file access. These changes have not been merged into `main`.
- The reference list is generated from `references.bib` using the standard BibTeX `ieeetr` style. The `cite` package supplies IEEE numeric citation formatting; `notoccite` keeps the front-matter figure/table lists from changing first-citation numbering in the body.
- The sample thesis was used to guide formal explanatory paragraphs, measurable objectives, figure explanations, and comparisons. Its topic, findings, and references were not imported.

## Supervisor feedback addressed

- Sections 1.1 and 1.2 distinguish background from the specific problem. Quantitative statements come from the supplied original studies, rather than unattributed population statistics.
- Table 1.1 compares voice communication, clinical decision, caller location, and dispatch support using common criteria. It distinguishes untested features from demonstrated capabilities.
- Sections 1.4 and 1.5 have no citations. Objectives identify measurements and tests; contributions are anticipated, not achieved results.
- Section 2.1 restores the historical account using the five supplied sources: the 1966 emergency-care report, the national emergency-number history, structured questioning and pre-arrival instructions in the 1970s, the evaluated 1985 priority-dispatch system, computerized protocols and quality review, and the 2013 dispatch-research synthesis. It then connects those developments to the six recent studies and the proposed telephone prototype. It does not repeat the Chapter 1 comparison table.
- Each of six paper sections has Methodology, Results, Strengths, Limitations, and Summary. The Chapter 2 summary connects gaps to design choices and planned checks.
- Five original architecture figures are reproduced with source attribution and black frames. The Shekhar paper contains result figures, not a system architecture; its results are shown as a denominator-preserving table.
- Section 2.8 identifies industrial standards and professional guidance after the six detailed study reviews; the chapter summary is now Section 2.9. It explains transport security, application security, conditional hospital data exchange, human-training guidance, and the Egyptian context.
- The Chapter 3 introduction explains the development phases and scope. Section 3.1 retains the functional and non-functional requirement bullets. The new Section 3.1.1 follows the requirements and maps selected standards to design decisions and planned checks. The existing block diagram and two-part flowchart are now Section 3.1.2; their labels and content are retained.
- Chapter 4 contains only a portrait vector Gantt chart and its caption. Eleven tasks appear by plain names, without T/M/W numbering. The chart includes phases, calendar weeks, durations, dependency arrows, completion-milestone diamonds, proposed leads, and the 14–16 January correction buffer. It runs from 23 November 2026 to the user-confirmed deadline of 17 January 2027. Internal dates and leads are proposed; the final deadline is confirmed. Internal JSON identifiers remain solely for dependency validation and are not printed in the thesis.
- Chapter 5 contains exactly three paragraphs, without section headings: progress so far, the proposed approach and anticipated contribution, and next steps. The final paragraph covers the post-midterm detailed diagrams, interface wireframes, tool and component selection, algorithms, relevant connection/circuit diagrams, cost analysis, implementation, and evaluation. No empty future sections or invented results are added.
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

## Historical-source evidence and recency

| Source | Evidence checked | Use in Section 2.1 |
|---|---|---|
| National Research Council, 1966 | PDF pp. 19–20 (printed pp. 16–17), and PDF pp. 38–39 (printed pp. 35–36) | Fragmented radio/telephone links, centralized coordination, medical supervision, and a proposed common telephone number. The report’s old injury totals are not presented as current statistics. |
| National 911 Program, “DOT in 911 History” | Official page fetched directly with HTTP 200 on 17 November 2026; last updated 15 December 2021. The extracted page text and source metadata are included in the editable source package. | February 1968 first call; 2002 wireless Enhanced 911 initiative and January 2003 action plan; December 2004 NG911 initiative; July 2008 demonstration using three laboratories/five public safety answering points; 2009 architecture and caller-location support. The source establishes historical milestones, not current nationwide deployment or a claim that our prototype integrates with E911/NG911. The IEEE title, publication/update month/year, and access date are corrected. |
| Zachariah and Pepe, 1995 | PDF pp. 1–3 | Mid-1970s pre-arrival instructions, 1977 protocol development/1978 introduction, 1979 training, 1986 computerized protocols, 1989 quality tracking, and subsequent standards. The text uses “mid-1970s” because this account says approximately 1975 while Gardett et al. identify 1976 for the early Phoenix instruction. |
| Slovis et al., 1985 | PDF pp. 2–6, especially Tables 1 and 5 and the discussion | 36 initial complaint categories; historical before/after mean urgent-case response 14.2 to 10.4 minutes; 1,694 complete reports, 46% agreement, 47% higher priority, 7% lower; 0.3% is only the lowest-to-highest mismatch. Dispatch plus travel time is distinguished from spoken-reply time. |
| Gardett et al., 2013 | PDF pp. 1–3 and 8–9 | 149 publications (114 original studies/35 concept papers), four research themes, computer-aided dispatch, inconsistent timing definitions, and limits of comparing telephone assessments with later diagnoses. |

The midterm rubric allows justified exceptions to its recent-publication guideline. The four older works are retained for the historical milestones and foundational dispatch methods they document, not as current performance estimates. All six contemporary detailed reviews remain from 2025–2026. With ten dated publications plus the government webpage, the unadjusted recent-publication fraction is six of ten; it is not described as meeting 80% without the stated historical exceptions.

## Industrial standards and midterm Criterion 13

The latest edit follows the supplied paragraph-style examples: each standards section now has four short paragraphs, with no internal subheadings or mapping table. Section 2.8 is approximately 245 words and Section 3.1.1 approximately 263 words, about 60% shorter in total. IEEE citations and the relevant project-specific scope distinctions are retained.

- TLS 1.3 / RFC 8446: the published metadata and security objective were read from the IETF-tools maintained BibXML archive. Configuration and certificate checks are supported by the full OWASP ASVS 5.0.0 standard. An unpublished TLS revision was not used as the normative reference.
- OWASP ASVS 5.0.0 (May 2025): the official PDF and requirement CSV were read from the OWASP release tag. Selected controls cover V8 authorization, V12 transport, V14 data protection, and V16 security logging; no entire ASVS level is claimed.
- HL7 FHIR R5, version 5.0.0: the overview and conformance source pages were read from the official HL7 release tag. The thesis identifies it as conditional on a later hospital interface agreement, while the present test receiver uses its own documented incident schema.
- National 911 Program training guidance: the official project summary, updated 25 August 2026, describes the June 2026 guidelines and explicitly states that training is not federally mandated. It informs discussion of human call-handler competence; it does not validate AI urgency labels or establish an Egyptian operating requirement. The obsolete 2016 PDF link led to an unavailable-resource document, which is excluded from the evidence package.
- Source URLs, retrieval dates, SHA-256 values, and the selected source files are recorded in `standards-sources/manifest.json` and included in the editable source ZIP. The source-access date for this addition is 18 November 2026.

The sections address the rubric's required distinctions through named references and scope; technical constraints (telephone/speech availability, languages, delays, locations, simulated resources); ethics and privacy (automation disclosure, consent, access, retention and deletion); safety (medical review, staff takeover and approval, explicit unknowns and failed delivery); and sustainability (bounded processing, usage/cost measurement, no unmeasured carbon claim). All verification is planned. No compliance, security certification, clinical effectiveness, or completed evaluation is asserted.

The standards are cited as reference specifications and professional guidance, separately from the recent experimental research. The rubric expressly permits justified standards exceptions to its publication-recency guideline.

## Figure handling

- Architecture figures are clipped from the supplied papers, retaining the original content. The added outer frame is black; no study architecture is invented.
- The project block diagram comes from `Thesis Diagrams/Proposed_Project_Block_Diagram.pdf`.
- The two project flowchart parts come from `Thesis Diagrams/Project_Flowchart.pdf`. The thesis copy excludes presentation headers/footers and changes only the first call-entry label from browser voice to telephone entry. The thesis captions identify the adaptation. Repository source diagrams are unchanged.
- Every thesis page is portrait with zero page rotation. Existing project diagrams are retained as scalable vector figures within black frames and fitted to portrait pages. The Gantt chart is drawn specifically for portrait presentation. Its phase bars and matching legend now use vivid blue, orange, purple, and green; the correction buffer is yellow. Dates, tasks, ownership, dependencies, and milestones are unchanged.

## Items remaining outside this rewrite

- The older supervisor comments referred to a submission ending at Chapter 2. The current user request expressly includes Chapter 3, so the revised contents include its requested requirements and diagrams.
- The time plan and initial conclusion required by the later midterm rubric are now included as Chapters 4 and 5. The new standards sections address the preliminary professional-context requirement. Remaining submission items include completing the Arabic cover, checking the full bilingual-front-matter requirement, and strengthening authoritative problem statistics. This update does not claim that every remaining rubric item has been completed.
- The approved English/Arabic abstracts, English cover, acknowledgment, and existing Arabic back cover are preserved. The Arabic back cover still has the original student/title/supervisor placeholders and reversed academic-year text; completing it requires a separate cover-page edit. The body no longer contains template instructions.
- Existing contact statements in Section 1.6 remain reported outreach, not confirmed partnerships.
- The presentation's older indicative 12-week implementation timetable is not changed in this request. Chapter 4 is the remaining Grad I design/submission plan for the confirmed 17 January 2027 deadline; it retains the proposed division of leads but uses the new calendar.
- Hospital authorization, an available test telephone route, reviewed medical guidance, reviewed reference labels, and implementation/evaluation remain prerequisites. No clinical effectiveness, real ambulance dispatch, or regulatory compliance is claimed.

## Editable source

`main.tex`, `chapter1.tex`, `chapter2.tex`, `chapter2b.tex`, `chapter3.tex`, `chapter4.tex`, `chapter5.tex`, `references.bib`, `ieeetr.bst`, `.latexmkrc`, and `assets/` form the editable source. `make_time_plan.py` and the time-plan JSON files reproduce the portrait Gantt chart and record the confirmed deadline and proposed task assignments. `validate_revision.py` checks page orientation, the requirement-list format, chart-only Chapter 4, the three-paragraph conclusion, retained approved pages, references, links, and source-paper integrity. Build in this directory with:

```sh
latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
python3 assemble_final.py
```

The required packages are standard TeX Live packages plus PyMuPDF for final assembly. The final assembly step retains the approved covers, abstracts, and acknowledgment as exact PDF pages and restores links/bookmarks. The Arabic abstract does not require Arabic typesetting packages to rebuild.
