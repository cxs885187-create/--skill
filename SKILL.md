---
name: nuwa-mends-the-sky
description: Use when users want fast university final-exam prep from real course materials such as PPTs, lecture notes, textbook chapters, homework, question banks, or past exams, especially when the work should become a semi-automatic cram workflow with one course at a time, Markdown notes, self-testing prompts, and explicit fallback behavior when evidence is weak.
---

# Nuwa Mends the Sky

## Overview

Turn messy course materials into a reliable cram workflow.

Use this skill to build a `one course at a time` final-exam prep loop with material triage, skeleton-first notes, cautious web-backed gap checks, and self-tests that rely on user self-evaluation rather than fake automatic grading.

## Core Rules

- Work on one course at a time.
- Treat this as a semi-automatic system, not a full autopilot.
- Prefer real user materials over outside knowledge.
- Use the web only to support course skeletons or verify uncertain facts from authoritative sources.
- Use external explanation aids only to improve understanding and memory, not to redefine the exam scope.
- If the user provides a school name, search for school-specific open question banks or past-paper repositories before relying on generic question patterns.
- Use visual explanations for topics where geometry, orientation, regions, graphs, or transformations are the real bottleneck.
- Do not pretend to know the real exam style when there is not enough evidence.
- Do not claim the user has "mastered" something based on your own grading.
- Ask for the exam time before building the cram package whenever the user has not already provided it.

## Mode Check

Before doing substantive work, determine which mode is available.

### File Mode

Use this when the environment can:

- read local files
- write local files
- read those files again later

In file mode, create or update Markdown outputs and keep an `index.md` per course when useful.

### Chat Mode

Use this when the environment cannot reliably write or re-read files.

In chat mode:

- output directory suggestions as plain Markdown
- output the note content directly in chat
- do not promise that future turns can automatically reopen prior notes
- ask the user to paste key notes back if later reuse is needed

State the current mode briefly before proceeding if it affects output behavior.

## Input Gate

Require at least one real material source:

- PPT
- lecture notes
- textbook chapter
- teacher-highlighted topics
- homework
- question bank
- past exam

If the user has no real material, do not fabricate a full cram system. Offer only a minimal fallback outline and ask for materials.

Before building the first real output, ask:

- which course should be handled first
- when that exam happens

If the exam date is missing:

- ask for it first
- only fall back to an inferred urgency mode if the user cannot provide it or the wording clearly implies urgency
- default to `3-day mode` when the date is vague but near
- default to `24-hour mode` when the user says the exam is tomorrow or otherwise immediate

Treat the fallback result as temporary and say that it should be revised once the real exam date is known.

## Workflow

### Step 1: Choose the Active Course

Do not start by generating multiple finished cram packages.

First determine:

- which course is being handled now
- when that course is being tested

If the user provided many courses but no priority, ask which one should go first or choose the nearest exam when dates are known.

### Step 2: Triage Materials

If the user gives mixed materials from multiple subjects, do a rough grouping first.

Use:

- file names
- titles
- directory names
- visible content

Label each grouping with confidence:

- `high`
- `medium`
- `low`

Do not silently merge low-confidence items into a course. Put them into a `to-confirm` bucket or explicitly mark them as uncertain.

If file mode is available, physically reflect this grouping in the workspace:

- create one materials folder per course
- move or copy source materials into the matching course folder when safe and appropriate
- create a real `to-confirm` folder for low-confidence files

Do not stop at a textual grouping summary if the environment supports file organization.

### Step 3: Work One Course at a Time

After grouping, choose one course to process.

Priority order:

1. the course with the nearest exam
2. the course the user explicitly names as most urgent
3. the course with the strongest material evidence

Do not attempt to fully process all courses in one pass if context or time is tight.

Do not generate complete cram outputs for multiple courses before the active course is stable.

### Step 4: Assess Evidence Quality

For the active course, identify whether you have:

- skeleton evidence
- topic evidence
- question-style evidence

Skeleton evidence usually means:

- syllabus
- textbook table of contents
- teacher-provided outline
- PPT or lecture-note section structure

Question-style evidence usually means:

- past exams
- homework
- question bank
- teacher practice sheets

If question-style evidence is weak, explicitly say so and downgrade later outputs that depend on it.

### Step 5: Build the Course Skeleton First

Always map the course before compressing it.

Skeleton source priority:

1. user syllabus
2. user textbook contents
3. user teacher highlights
4. PPT or lecture-note structure
5. authoritative web sources as external skeleton references

Build a simple hierarchy such as:

- course
- chapter
- major topic
- subtopic

Do not start with a freeform summary if the course map is still unclear.

### Step 6: Use the Web Carefully

Use web lookup only when one of these is true:

- the user materials are too incomplete to build a stable course skeleton
- a fact is uncertain and needs authoritative verification
- the user asks you to verify something current or official

When browsing, use authoritative sources only when possible:

- official university pages
- official course pages
- official publisher pages
- official documentation or standard references

If the source is only an external skeleton reference, label it as such.

Do not use browsing to:

- invent likely exam topics
- replace missing user materials wholesale
- overfit to random forum advice or generic study blogs

If web evidence does not clearly match the user's course, say so.

### Step 7: Search School-Specific Open Question Sources

If the user provides their school name, search for open GitHub repositories or public pages that match:

- school name
- course name
- course code, if known
- teacher name, if known
- exam type, such as final, midterm, homework, quiz, or question bank

Good source types:

- school-specific GitHub past-exam repositories
- student-maintained open question banks for the same school and course
- public homework or review repositories that clearly match the course
- official open course pages that link assignments or sample exams

Treat a school-specific GitHub question bank as strong question-style reference only when it matches the school and course clearly.

Before using it, record:

- repository or page URL
- matching evidence
- year or semester, if available
- course name or code
- whether it is past exam, homework, quiz, or notes

Do not treat a random GitHub repository as strong evidence just because the topic name is similar.

Evidence priority:

1. user-provided teacher materials
2. user-provided past exams, homework, and question banks
3. school-specific open repositories that clearly match the course
4. official or publisher skeleton references
5. generic GitHub explanation aids

If the school repository conflicts with the user's teacher materials, trust the user's teacher materials first and mark the repository as secondary evidence.

### Step 8: Use Explanation Aids Carefully

If a topic is hard to understand or hard to remember, you may look for external explanation aids.

Good uses include:

- open-source textbook notes
- GitHub repositories that explain the same topic clearly
- open lecture notes
- worked-example repositories

Use them only to improve:

- intuition
- memory hooks
- worked-step templates
- common mistake explanations

Do not use them to:

- redefine the exam scope
- replace the user's textbook or teacher materials
- pretend a GitHub explanation is a confirmed exam point

Priority for deciding what is in scope:

1. user syllabus and teacher materials
2. user textbook and homework
3. past exams and question banks
4. authoritative external references
5. GitHub or other open explanation aids

If an external explanation is useful, label it as an explanation aid rather than core course evidence.

## Planning Rules

Create plans as heuristics, not fake precision schedules.

Plan layers:

- overall cram plan
- per-course plan

Time-mode defaults:

- `7-day mode`: balanced attack plus spaced review
- `3-day mode`: compress to high-value topics, more review than expansion
- `24-hour mode`: extreme compression, mostly retrieval, mistakes, and likely test patterns

Do not hard-code brittle rules like "exactly two knowledge blocks per day." Instead:

- keep heavy tasks limited
- allow short recall and review tasks to be interleaved

Treat "strategic abandonment" as high risk.

Only recommend explicit abandonment when there is evidence such as:

- past-exam distribution
- homework distribution
- teacher statements
- the user's own declared choice to give up that section

Without such evidence, downgrade the recommendation to:

- `low priority`
- `last if time remains`

## Note Generation Rules

The output is not a pretty summary. It should support:

- active recall
- rapid compression
- follow-up reuse

The note system should be logically unified but physically split into a small number of purpose-specific files.

Do not make one giant file for normal cases.

Do not make many tiny files that act like a maze.

Preferred pattern:

- one course folder as the unified note library
- one `index.md` for navigation and status
- a small number of focused content files

Every user-facing content file must let the user start reviewing or solving immediately. An index-only file is not enough unless its only purpose is navigation.

For hard topics, prefer topic-card files over pure index files. A topic card should answer:

- what to memorize
- how to solve
- what mistakes are common
- how to self-test

Examples of topic-card files:

- `multiple-integrals-topic.md`
- `line-and-surface-integrals-topic.md`
- `series-topic.md`

If you are in file mode, follow the naming and layout conventions in `references/output-conventions.md`.

In `3-day mode`, keep the output compact. Do not create bonus files unless they replace an existing core file rather than expanding the set.

If a file cannot help the user directly review, recall, solve, or diagnose a weak point, it is probably not a useful user-facing note.

For chapter notes, prefer a Cornell-like Markdown protocol that works in plain text:

```markdown
### Topic: TCP Four-Way Handshake

- Q1: Why must TIME_WAIT remain after the final ACK?

<details>
<summary>Reference answer / scoring points</summary>

- **Core point**: Ensure the passive closer receives the final ACK and prevent stale packets from polluting a new connection.
- **Common miss**: Forgetting the meaning of 2MSL.
- **Backlink**: [transport-layer-tcp]

</details>
```

If there is strong question-style evidence, make the questions closer to real exam wording.

If there is weak question-style evidence, write:

- likely recall questions
- standard understanding questions

Do not market those as real exam questions.

When a concept is hard, you may add a short explanation-aid block derived from an external teaching source, but keep it subordinate to the course materials and label it clearly.

### Visual Notes

Use visual explanations when text alone is likely to fail.

Good targets:

- double and triple integral regions
- surface integrals
- line integrals
- vector fields
- coordinate transforms
- geometry in space
- graph or relation concepts in discrete math

Use the simplest available visual form:

- ASCII sketch
- Markdown table
- Mermaid diagram
- coordinate-region description
- generated image or local rendered diagram, if the environment supports it

For surface integrals, a useful visual note should show or describe:

- the surface
- projection region
- orientation or normal direction
- boundary direction, if relevant
- which formula follows from the picture

Do not add decorative visuals. Add visuals only when they reduce confusion or improve recall.

## Self-Test Rules

V1 does not perform authoritative grading.

Your role is:

- generate questions
- generate reference answers or scoring points
- help the user compare
- help the user reflect on weak areas

The user's role is:

- answer
- self-evaluate
- decide whether they truly recalled enough

Recommended loop:

1. Give up to 5 questions.
2. Let the user answer or speak through them.
3. Show reference answers or scoring points.
4. Ask the user to self-label each as:
   - `know`
   - `partial`
   - `dont know`
5. Use that self-labeling to decide the next move.

Use multi-round questioning to locate weak points.

Pattern:

1. ask one core question
2. inspect the user's self-evaluation or stated confusion
3. ask a narrower follow-up on:
   - definition
   - formula
   - recognition
   - method step
4. stop when the weak layer is located

The goal is not to interrogate the user endlessly. The goal is to find whether the failure is mostly:

- missing definition
- memory weakness
- pattern-recognition weakness
- unstable solving steps

Do not pre-bake a long static bank of 15 to 20 questions as if it were the interactive loop itself.

If writing a file-mode self-test document, keep it to one short round or a small starter set, then tell the user to continue interactively after self-evaluation.

Do not claim you can reliably detect:

- exact proof correctness
- subtle derivation mistakes
- whether a humanities answer earned full marks

### Self-Test Fuse

If the user self-labels three consecutive items as `dont know`, or explicitly says the whole block is broken:

- stop extending the test
- route them back to the relevant note section
- suggest a short retrieval-focused rebuild
- then generate replacement questions later

### Error Labels

Keep error analysis coarse:

- `dont know`
- `memory weak`
- `pattern recognition weak`
- `expression or steps unstable`

Present these as aids, not objective verdicts.

## Mastery Language

Do not overclaim mastery.

Safer labels:

- `not started`
- `in progress`
- `temporary recall ok`
- `needs rebuild`

Only use stronger language when the user has actually gone through repeated recall and application cycles.

## Follow-Up Reuse

If file mode is available and prior Markdown exists, reuse the course `index.md` or equivalent summary first.

If file mode is not available, ask the user to paste the most relevant prior notes instead of pretending you remember them.

Good follow-up tasks include:

- regenerate a shorter cram sheet
- make a new round of self-tests
- focus only on weak topics
- turn long notes into last-minute recall prompts
- rewrite one hard topic using a clearer explanation style
- replace an abstract explanation with a more memorable worked pattern

### Incremental Updates

Expect materials to change over time.

When the user adds files later, do not assume a full rebuild is required.

Instead:

1. compare the new files against the existing course materials list
2. label them as:
   - `new`
   - `replacement`
   - `possible duplicate`
   - `to confirm`
3. update only the affected notes, evidence labels, and self-tests
4. record what changed in the course index or summary

If a new file changes a prior conclusion, explicitly mark the old conclusion as downgraded or revised.

## Failure Modes To Avoid

- Pretending low-confidence course grouping is correct
- Producing only a textual grouping summary when file mode can create real course folders
- Starting the cram build before asking for the exam time when it is missing
- Pretending web-derived skeletons are guaranteed to match the teacher's exam
- Pretending self-tests are objectively graded
- Pretending weak evidence supports "real exam style" outputs
- Generating too many files for short time modes
- Expanding to multiple courses when one urgent course still lacks a stable skeleton
