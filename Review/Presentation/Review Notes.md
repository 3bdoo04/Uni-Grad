# Uni-Grad midterm presentation — review draft

Prepared from the approved 44-page thesis at `798e1611042be81b086a27a02259942b3f9d89ab`, the uploaded `Presentation_Template.pptx`, and both presentation rubrics. The thesis and original `PreMid Presentation` files are not modified.

## Files

- **Uni-Grad - Midterm Presentation.pptx** — editable slides and speaker notes. Slides 1–16 are the main deck; slides 17–20 are hidden Q&A backups.
- **Uni-Grad - Midterm Presentation.pdf** — full 20-slide review export, including backups.
- **Uni-Grad - Main Slides.pdf** — the 16 visible main slides only.
- **Uni-Grad - Rehearsal Guide.pdf / .md** — timed run order, proposed speaking split, objective pairing, delivery cues, Q&A, and rubric mapping.
- **Slide Overview.png** — visual contact sheet of all slides.
- **Presentation-checks.json** — timing/content/template checks.

## Timing

The prepared talk is 12:45; 2:15 is reserved for questions and transitions, within a 15-minute total plan. Suggested speaking time is Omar 6:15 and Abdelrahman 6:30. These are rehearsal targets, not automatic slide advances. Rehearse the actual delivery with a timer.

## Content decisions

- Original template masters, layouts and themes are retained. Navy headings, the green ribbon/wave, campus image, olive branch and lower rule remain. Cards and native editable diagrams replace long instructional bullets.
- Logos appear MSA → CSE → Engineering → Greenwich. Source logo bytes are unchanged; transparent margins use native PowerPoint crop properties.
- The eight thesis objectives are paired 1+8, 2+7, 3+4, and 5+6 into four objectives. No original objective is dropped.
- Exactly two main literature slides cover DispatchMAS and TriAgent, each with method, results, limitations and publication date. DispatchMAS's supplied PDF prints year 2026, not an exact publication day/month; only the verified year is shown. TriAgent prints 18 June 2026.
- Published study measurements are not presented as prototype results. The 1.5-second value is a target. DispatchMAS's 94% concerns mocked contact. TriAgent's gains include structured inputs and a trained classifier.
- Cost analysis is a proposed measurement method, matching the thesis's current stage. No numerical budget, service price, project publication, secured partnership or clinical benefit is invented.
- The industrial-standards backup follows the thesis's current five selections and has no standards bibliography citations. Web Audio remains excluded.

## Rubrics

The midterm presentation rubric has six criteria totaling 10 marks: visual quality (2), organization (1), explanation (3), oral delivery (1), timing (1), and Q&A (2). The common rubric separately grades content, visuals, presentation skills, organization and questions on 4/3/2/0 quality levels. The two scoring systems are not combined. Actual delivery, timing and answers need rehearsal; the deck and guide support these criteria without promising a grade.

## Rebuild from the source bundle

Use Python with `python-pptx`, `pillow`, `pymupdf`, `lxml`, and `reportlab`. With LibreOffice/soffice available, run:

```sh
python3 build_all.py
```

PowerPoint uses the template's Calibri/Calibri Light family. PDF rendering uses the bundled, metrically compatible Carlito fonts through a local fontconfig file. Carlito's OFL licence is included in `fonts/OFL.txt`. No system font configuration is changed. `build_presentation.py` alone creates the editable PowerPoint without requiring LibreOffice.

The audit checks original masters/layouts/themes, logo bytes and order, all eight objectives, paper slide content, timing, hidden backup slides, off-slide shapes and estimated text fit. Every slide is also rendered for visual inspection. Logo files and original template are included as inputs; the thesis and research PDFs remain available in the project repository.

The user has approved publication of this presentation on `main`. The original thesis and pre-midterm presentation files remain unchanged.
