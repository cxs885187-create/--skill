# Output Conventions

Use this reference when generating user-facing outputs for `nuwa-mends-the-sky`.

## Naming by User Language

Choose file names according to the user's current dominant chat language.

- Chinese chat: prefer Chinese file names
- English chat: prefer English file names
- Mixed chat: prefer the currently dominant language

The file name should immediately show:

- course
- mode or urgency
- document purpose

Examples:

- `高数-3天突击-核心骨架.md`
- `高数-24小时突击-速看总表.md`
- `calculus-3day-cram-core-skeleton.md`
- `calculus-24h-cram-shot.md`

## Minimal File Layout

When file mode is available, keep V1 small.

At the top level, separate raw materials from generated cram notes whenever possible.

Recommended structure:

```text
workspace/
├─ to-confirm/
├─ course-name/
│  ├─ materials/
│  ├─ index.md
│  ├─ core-skeleton.md
│  ├─ self-test-and-gaps.md
│  └─ cram-summary.md
└─ ...
```

Rules:

- `materials/` should contain the source files for that course when safe and supported
- `to-confirm/` should contain low-confidence or unclassified files
- do not leave all raw files mixed in the workspace root if file mode is available
- keep the course note library unified at the course-folder level, but split it into a few purpose-specific files

Recommended per-course layout:

```text
course-name/
├─ materials/
├─ index.md
├─ 核心骨架.md / core-skeleton.md
├─ 自测与错因.md / self-test-and-gaps.md
└─ 冲刺摘要.md / cram-summary.md
```

Do not explode into many files unless the user clearly has time and wants the extra structure.

Do not collapse everything into one giant file unless you are in `24-Hour Mode`.

## Topic Card Files

If a topic file cannot help the user start reviewing or solving immediately, it is not a good topic file.

Prefer topic cards for content-heavy areas.

Each topic card should answer:

- what to memorize
- how to solve
- common mistakes
- how to self-test

Examples:

- `重积分专题.md`
- `曲线曲面积分专题.md`
- `无穷级数专题.md`
- `multiple-integrals-topic.md`
- `surface-integrals-topic.md`

An `index.md` can navigate, but it should not replace real topic cards.

## Time-Mode Compression

### 7-Day Mode

Allowed:

- separate skeleton note
- separate self-test note
- separate cram summary

### 3-Day Mode

Prefer:

- one compact skeleton note
- one combined self-test and weakness note
- one short summary note

Do not add extra sidecar files unless they replace one of those three files.

### 24-Hour Mode

Prefer a single main file:

- `24H-CRAM-SHOT.md`
- or the same pattern in the user's language

That file should contain only:

- highest-value skeleton
- likely weak points
- one short self-test round
- final skim section

If the file starts becoming too long, cut lower-priority material instead of adding more sections.

## Explanation Aid Blocks

Use external explanation aids only to make a topic easier to understand or remember.

Good uses:

- clearer memory hook
- worked example
- misconception warning

Bad uses:

- replacing course evidence
- redefining the exam scope
- turning the note into a generic tutorial

Label explanation aid blocks clearly, for example:

```markdown
### Explanation Aid: Why this works
```

## School-Specific GitHub Evidence

If the user provides a school name, GitHub repositories can be used as stronger question-style references only when the match is explicit.

Record:

- repository URL
- school match
- course match
- year or semester, if available
- material type, such as final exam, homework, quiz, or question bank

Label the evidence clearly:

```markdown
### School-Specific Open Question Reference
```

Do not use a generic GitHub repository as school-specific evidence.

If the repository helps explain a topic but does not match the school/course, label it as an explanation aid instead.

## Visual Explanation Blocks

Use visual blocks for topics where shape, direction, region, or transformation matters.

Good candidates:

- multiple integrals
- line integrals
- surface integrals
- vector fields
- coordinate transforms
- spatial geometry

Acceptable formats:

- ASCII sketch
- Mermaid diagram
- table
- coordinate-region description
- generated image, if the environment supports it

Label visual blocks clearly:

```markdown
### Visual: Region and Orientation
```

For surface integrals, include:

- surface description
- projection region
- normal or orientation
- boundary direction when relevant
- formula choice explained from the visual

## Cornell-Style Markdown Blocks

Prefer a stable plain-Markdown protocol:

```markdown
### Topic: XXX

- Q1: ...

<details>
<summary>Reference answer / scoring points</summary>

- **Core point**: ...
- **Common miss**: ...
- **Backlink**: [...]

</details>
```

Rules:

- Use question phrasing, not vague keywords
- Call the answer a `reference answer` or `scoring points`
- Include one backlink when possible
- Keep each block short enough for quick recall

## Low-Confidence Labels

When evidence is weak, label it explicitly.

Use phrases such as:

- `low confidence grouping`
- `external skeleton reference`
- `likely recall question`
- `standard understanding question`
- `potential high-risk blind spot`
- `low priority if time remains`

Do not hide uncertainty behind authoritative wording.

## Incremental Update Conventions

When new materials arrive later, avoid full rebuilds by default.

Each course `index.md` should track a simple materials list or update section that marks files as:

- `new`
- `replacement`
- `possible duplicate`
- `to confirm`

When an update changes conclusions:

- say which note was affected
- say whether confidence increased or decreased
- say whether new self-tests are needed
