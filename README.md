<p align="right">
  <strong>English</strong> | <a href="./README.zh-CN.md">简体中文</a>
</p>

# Nuwa Mends the Sky

A Codex Skill for last-minute university final-exam preparation.

Nuwa Mends the Sky is not an automatic exam-prediction tool or a universal study assistant. It is a semi-automatic exam-prep workflow that turns slides, lecture notes, textbooks, question banks, past papers, and supplemental materials into a Markdown note library that can be reviewed, self-tested, and iterated.

## Best-Fit Scenarios

- Finals are near, and the material pile is large and messy.
- One folder contains PPTs, PDFs, question banks, textbooks, and images from multiple courses.
- You want to archive materials by course before processing one course at a time.
- You want compressed topic cards that can be reviewed directly, not only an index.
- You want to infer high-frequency question patterns from question banks, homework, and past papers.
- You want multi-round questioning to locate whether the real weakness is definitions, formulas, pattern recognition, or unstable steps.
- You want open lecture notes, GitHub textbooks, GitHub question banks, diagrams, and visual aids only when abstract material is hard to understand.

## Core Principles

- Process one course at a time: do not generate complete cram packages for multiple courses in one pass.
- Ask for the exam time first: remaining time determines granularity and strategy.
- Archive materials before generating notes: in file mode, create real course material folders instead of only writing classification conclusions in an index.
- Grade evidence: distinguish user materials, teacher materials, past papers, school-specific open repositories, and generic explanation aids.
- Do not auto-grade authoritatively: the Skill provides reference answers and scoring points; the user self-evaluates.
- Notes must be reviewable: if a file cannot help the user start memorizing, solving, or diagnosing mistakes immediately, it is not good enough.

## Features

### Material Archiving

In file mode, the Skill should first organize materials into a structure like:

```text
workspace/
├─ to-confirm/
├─ Advanced-Mathematics-A/
│  ├─ materials/
│  ├─ index.md
│  ├─ core-skeleton.md
│  ├─ self-test-and-gaps.md
│  └─ cram-summary.md
└─ Ideology-and-Morality/
   └─ materials/
```

Low-confidence materials go into `to-confirm/` or are explicitly marked as needing confirmation.

### Course Skeleton

Evidence priority:

1. User-provided syllabus, teacher highlights, and course slides.
2. User textbooks and homework.
3. User-provided past papers and question banks.
4. School-specific open question banks or past-paper repositories.
5. Official, publisher, or authoritative course pages.
6. Generic GitHub notes or open textbooks.

Generic GitHub repositories can only be used as explanation aids. They cannot replace teacher materials or define exam scope.

### School-Targeted GitHub Search

If the user provides a school name, the Skill should prioritize school-specific open question banks, past papers, homework repositories, and review repositories.

They should be treated as stronger question-style references only when:

- the school matches
- the course name or course code matches
- the material type is clear, such as final, midterm, homework, quiz, or question bank
- the year or semester is traceable when possible

Otherwise, mark them as `explanation aid` or `low confidence reference`.

### Topic-Card Notes

For topics such as multiple integrals, line integrals, surface integrals, and infinite series, the Skill should not generate only an index. It should create topic cards.

Each topic card should answer at least four questions:

- what to memorize
- how to solve
- where mistakes usually happen
- how to self-test

Examples:

- `multiple-integrals-topic.md`
- `line-and-surface-integrals-topic.md`
- `series-topic.md`

### Visual Aids

When abstract content is hard to understand, the Skill may generate:

- ASCII sketches
- Mermaid diagrams
- tables
- region, projection, or normal-direction descriptions
- local rendered diagrams or generated images, if the environment supports them

Good targets for visualization include:

- multiple-integral regions
- line-integral directions
- surface-integral normals
- vector fields
- coordinate transforms
- spatial geometry
- graphs, relations, and paths in discrete mathematics

### Self-Tests and Weakness Diagnosis

The Skill does not perform authoritative automatic grading.

Recommended loop:

1. Give 4 to 5 questions in one round.
2. Let the user answer closed-book.
3. Show reference answers or scoring points.
4. Ask the user to self-label each item as `know`, `partial`, or `dont know`.
5. Continue with narrower follow-ups based on the self-labels.

Weakness layers include:

- missing definitions
- weak formula memory
- weak question-pattern recognition
- unstable solution steps

If the user labels 3 consecutive items as `dont know`, stop asking more questions and route them back to the relevant topic card for rebuilding.

## What It Does Not Do

- It does not guarantee exam prediction.
- It does not treat GitHub repositories as the default exam scope.
- It does not replace textbooks or teacher materials with random webpages.
- It does not call something "must appear on the exam" when evidence is weak.
- It does not split one course into dozens of tiny files that are hard to navigate.
- It does not put everything into one oversized Markdown file unless the user is in 24-hour emergency mode.

## Theoretical Support and Classic Methods

| Function | Theory or classic method | How it appears in the Skill |
| --- | --- | --- |
| One-course-at-a-time processing | Cognitive load theory, goal shielding, monotasking | The Skill refuses to generate complete packages for multiple courses before the active course is stable. |
| Asking for exam time first | Backward planning, timeboxing, exam-oriented constraint planning | The Skill chooses 7-day, 3-day, or 24-hour mode based on the exam date and remaining time. |
| Material archiving | Information chunking, source provenance, evidence-based learning | Materials are grouped by course; low-confidence files are separated into `to-confirm/` instead of silently merged. |
| Course skeleton first | Advance organizers, schema theory, concept mapping, constructive alignment | The Skill maps course/chapter/topic/subtopic before writing compressed summaries. |
| Evidence grading | Evidence hierarchy, triangulation, source criticism | User materials outrank school-specific repositories, which outrank generic explanation aids. |
| School-targeted GitHub search | Situated learning, near transfer, ecological validity | School and course matches can strengthen question-style evidence, but only with explicit match criteria. |
| Topic-card notes | Cornell notes, active recall, chunking, worked-example effect | Each topic card answers what to memorize, how to solve, common mistakes, and how to self-test. |
| Cornell-style question blocks | Cornell note-taking method, testing effect, generation effect | Notes use question prompts plus collapsible reference answers so the user recalls before reading. |
| Cram-mode planning | Backward planning, Pareto principle, spaced repetition, Ebbinghaus forgetting curve | Shorter time windows shift the workflow toward high-value topics, retrieval, mistake review, and repeated recall. |
| Visual aids | Dual coding theory, multimedia learning, spatial reasoning externalization | Diagrams are used for regions, directions, normals, transforms, and graph structures only when they reduce confusion. |
| Explanation aids | Feynman technique, elaborative encoding, analogy-based learning | Open notes and worked examples may improve intuition or memory hooks, but they do not redefine exam scope. |
| Self-tests | Retrieval practice, testing effect, formative assessment | The Skill asks short rounds of questions and reveals scoring points only after the user attempts recall. |
| User self-evaluation | Metacognitive calibration, self-regulated learning | Users label answers as `know`, `partial`, or `dont know`; the Skill uses labels to choose the next move. |
| Weakness diagnosis | Diagnostic assessment, mastery learning, error analysis | Follow-up questions locate whether the problem is definition, formula, recognition, or execution. |
| Self-test fuse | Cognitive load management, scaffolding, frustration control | After repeated `dont know` labels, the Skill stops testing and routes the user back to rebuilding notes. |
| Conservative mastery language | Metacognitive bias control, validity limits | The Skill uses cautious labels such as `temporary recall ok` and avoids claiming mastery from its own grading. |
| Incremental updates | Spaced repetition, forgetting-curve-aware review, learning logs | Existing `index.md` files and prior notes are reused; new materials update only affected sections. |

## Installation

Copy `nuwa-mends-the-sky/` into your Codex skills directory.

Windows example:

```powershell
Copy-Item -Recurse ".\nuwa-mends-the-sky" "$env:USERPROFILE\.codex\skills\nuwa-mends-the-sky"
```

Then restart Codex, or start a new Codex session.

## Repository Structure

```text
--skill/
├─ README.md
├─ README.zh-CN.md
└─ nuwa-mends-the-sky/
   ├─ SKILL.md
   ├─ agents/
   │  └─ openai.yaml
   └─ references/
      └─ output-conventions.md
```

## Usage Example

```text
Use $nuwa-mends-the-sky.
I put review materials for Advanced Mathematics, Ideology and Morality, and Discrete Mathematics in this folder.
My school is XX University.
The Advanced Mathematics exam is on July 1.
Please process only Advanced Mathematics A first.
```

The Skill should first:

- confirm file mode or chat mode
- confirm the exam time
- process only one course
- archive materials by course
- build an evidence-based course skeleton
- search school-specific open question sources when useful
- generate directly reviewable topic cards, self-tests, and a cram summary

## Current Status

V0.1

Implemented:

- semi-automatic final-exam cram workflow
- one-course-at-a-time processing
- file mode and chat mode
- material archiving rules
- evidence grading
- school-targeted GitHub question-bank search rules
- GitHub and open lecture notes as explanation aids
- topic-card note rules
- visual aid rules
- self-test and user self-evaluation rules
- incremental material update rules

## License

This repository is licensed under the MIT License.
