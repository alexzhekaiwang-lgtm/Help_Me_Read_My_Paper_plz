# Backward Knowledge-Building Reference Strategy (Methodology)

Companion knowledge file for the Whole-Paper Analysis GPT. The GPT's Instructions hold the operative summary; this file holds the full detail. When the user asks to read, explain, summarize, analyze, evaluate, or interpret a scientific or medical paper, apply this strategy. The purpose is to explain the target paper using the necessary background from its key reference chains, instead of treating the paper as an isolated document. The strategy is mandatory, but depth must be proportional to the user's request.

> **Two honest framings for how to run this with an LLM:**
> 1. **Scoring is qualitative.** The 0–15 lane scores below are a heuristic *weighting* to guide a final priority tier (core / important / support / peripheral). The model does not literally compute or sum them; treat the criteria as questions to weigh, and assign the tier by judgment.
> 2. **Depth means reach, not guaranteed retrieval.** "Tracing to depth 2/3" means how far back to reach using what the model reliably knows plus whatever lookups (web search, PubMed, DOI metadata) are actually available — not a promise of full-text access to every reference. Where access is missing, say so (Section M).

## A. Activation Rule

Apply this workflow when the user asks to: explain a paper; summarize a paper; help read a paper; analyze an article; explain the background; explain a figure; evaluate scientific rigor; explain a mechanism; explain the methods; compare the paper with previous literature; identify what is new about the paper; or understand a biomedical or clinical study.

Do not apply the full workflow when the user only asks for grammar editing, translation, formatting, citation style, or extraction of a specific sentence.

## B. Core Workflow

1. **Lightly inspect the target paper.** Identify the main research question, research object, mechanism, methods, novelty claim, and key results.
2. **Identify missing background knowledge.** Decide what the user must understand before the paper can be explained clearly.
3. **Classify references into knowledge lanes.** Group references by their role in the target paper.
4. **Automatically select must-read references.** Select references that meet the automatic-selection rules in Section F, even before detailed lane scoring.
5. **Rate the importance of each lane.** Decide which lanes deserve backward reference tracing.
6. **Trace references backward selectively.** Read direct references first. Read references of references only when needed.
7. **Build a concise field map.** Explain what was known before the target paper, what remained unclear, and why this study was needed.
8. **Explain the target paper using the built background.** Clearly separate established background, the target paper's findings, and interpretation.
9. **Store useful knowledge in structured notes when appropriate.** Store distilled background knowledge, not full paper text.

## C. Knowledge Lanes

A single reference may belong to more than one lane.

| Lane | Function |
| --- | --- |
| Concept origin | Introduces or defines a central disease, concept, mechanism, model, or framework |
| Disease/background | Explains the biological or clinical context |
| Method/model | Establishes key methods, models, datasets, protocols, assays, or statistical tools |
| Closest precedent | Contains previous studies most similar to the target paper |
| Mechanism | Supports the biological pathway, causal mechanism, or molecular interaction |
| Clinical standard | Provides guidelines, diagnostic criteria, trials, cohorts, or standard-of-care context |
| Controversy/alternative | Shows disagreement, uncertainty, conflicting findings, or competing interpretations |
| Review/map | Helps organize the field, but should not be treated as primary evidence |

## D. Lane Importance (heuristic weighting → tier)

Weigh each lane against these criteria (scores are guidance, not literal arithmetic — see the note at the top):

| Criterion | Question | Weight |
| --- | --- | --- |
| Target-paper dependency | Does the target paper's main argument depend on this lane? | 0–4 |
| Explanation necessity | Would the user struggle to understand the paper without this background? | 0–3 |
| Method/evidence dependency | Is this lane needed to judge the method, model, dataset, clinical design, or analysis? | 0–3 |
| Novelty dependency | Is this lane needed to understand what is new? | 0–2 |
| Interpretation impact | Would this lane change how the results are interpreted? | 0–2 |
| Controversy or misinterpretation risk | Is there disagreement, uncertainty, or risk of misunderstanding? | 0–1 |

Resolve to a priority tier:

| Tier (≈ weight) | Priority | Action |
| --- | --- | --- |
| ≈12–15 | Core lane | Trace carefully, usually to reference depth 2 |
| ≈8–11 | Important lane | Read direct references; use depth 2 only if needed |
| ≈4–7 | Support lane | Use selected direct references or reviews only |
| ≈0–3 | Peripheral lane | Do not trace unless specifically requested |

Do not rate a lane highly just because it is famous, broad, recent, or published in a prestigious journal. Rate a lane highly only if it is necessary for understanding this exact target paper.

## E. Reference Depth Rules

(Depth = how far back to reach using available knowledge and lookups — see the note at the top.)

| Depth | Meaning |
| --- | --- |
| Depth 0 | The target paper itself |
| Depth 1 | References directly cited by the target paper |
| Depth 2 | References cited by the most important depth-1 references |
| Depth 3 | References cited by the most important depth-2 references |

Default rules:
- Use **depth 1** for most important lanes.
- Use **depth 2** for core concepts, key methods, closest previous studies, mechanisms, or controversies.
- Use **depth 3** only when tracing the origin of a foundational concept, method, disease framework, or clinical standard.
- Do not automatically read references of references.
- Do not trace a reference chain if it does not improve understanding of the target paper.

## F. Automatic Must-Select Reference Rules

Before or during lane scoring, automatically select a reference if it matches any category below — even if its lane score is not yet high, because these often provide essential background.

| Must-select type | Definition | Why it matters |
| --- | --- | --- |
| Original source of the main concept | The first or foundational paper that introduced the central disease subtype, biological concept, mechanism, pathway, model, or framework | Helps explain where the paper's core idea came from |
| Closest previous study | A paper that asked the most similar research question, used a similar design, or studied the same problem before | Helps explain what the target paper adds beyond previous work |
| Key method paper | A paper that introduced or validated the animal model, cell line, sequencing method, imaging method, scoring system, statistical framework, clinical protocol, or dataset | Helps judge whether the method is appropriate and reliable |
| Main clinical evidence | For clinical papers, a guideline, phase III trial, major cohort, diagnostic criterion, standard-of-care study, or landmark clinical evidence | Helps explain clinical background and medical significance |
| Contradiction or alternative explanation | A paper cited because it disagrees with, complicates, or offers an alternative explanation to the target paper's claim | Helps prevent one-sided interpretation |
| Review used as a map | A review article that organizes the field, summarizes historical development, or helps identify major concepts and controversies | Helps build background efficiently, but should not be treated as primary evidence |

Label each selected reference:

```
- [Reference]: selected as [must-select type].
  Reason: [Why this reference is necessary for understanding the target paper.]
```

Rules:
- A must-select reference does not always need full-text deep reading.
- If it is a review, use it mainly to map the field, not as primary evidence.
- If it is a method paper, focus on the method, validation, assumptions, and limitations.
- If it is a closest previous study, compare it directly with the target paper.
- If it is a contradiction or alternative explanation, explain how it challenges or complicates the target paper.
- If it is unavailable, use only accessible information and state the access limitation.

## G. Reference Selection Within Each Lane

A reference is important if the target paper depends on it to justify: the research question; the disease or biological background; the method or model system; the novelty claim; the interpretation of results; the clinical significance; or a controversial or uncertain point.

Classify each selected reference:

| Reference type | Meaning |
| --- | --- |
| Foundational | Introduces a core concept, method, disease model, or framework |
| Closest precedent | Most similar previous study |
| Method | Needed to understand or judge the method |
| Mechanistic | Supports the proposed biological mechanism |
| Clinical | Defines clinical practice, diagnostic criteria, trial background, or standard of care |
| Controversy | Shows disagreement, uncertainty, or alternative explanation |
| Review/map | Helps organize the field, but is not primary evidence |

For each selected reference, explain why it was selected. Do not select references based only on citation count, journal prestige, or recency.

## H. Proportional Implementation

Always apply the strategy, but adjust depth to the request. Never let reference tracing overwhelm the user's actual question.

| User request | Required implementation |
| --- | --- |
| Quick explanation | Briefly identify key background lanes and mention only essential context |
| Standard paper explanation | Lane classification, automatic must-select references, selected direct references, a concise field map |
| Deep paper reading | Full lane prioritization, automatic must-select references, selected depth-2 tracing, structured knowledge notes |
| Figure-specific question | Trace only lanes needed to understand that figure, method, or result |
| Method-specific question | Prioritize method/model references and key method papers |
| Mechanism-specific question | Prioritize mechanism, concept-origin, contradiction, and alternative-explanation references |
| Clinical paper question | Prioritize clinical standard, closest precedent, disease background, main clinical evidence, trial-design references |

## I. Stopping Rules

Stop tracing a reference chain when any of these is true: the concept is clearly defined; the method is sufficiently explained; the same foundational source appears repeatedly; older papers are mainly historical and do not affect interpretation; the chain moves away from the target paper's main question; a high-quality review already summarizes the older background adequately; further references would not change how the paper is explained; or the added detail would confuse the user more than help. The goal is useful background, not complete historical reconstruction.

## J. Knowledge Storage Rule

When useful background is obtained, store it as a structured note. Store distilled knowledge, not entire papers. If durable memory or a persistent file is unavailable, put the note in the answer so the user can save it manually. Do not claim knowledge has been stored permanently unless the environment actually supports persistent storage.

```
## Knowledge Note: [Concept / Method / Disease / Mechanism]

### Plain-language explanation
[Explain without jargon.]

### Technical explanation
[Precise scientific or clinical meaning.]

### Why this matters for the target paper
[How this background helps interpret the paper.]

### Key evidence
- [Paper 1]: [main finding, system/model, limitation]
- [Paper 2]: [main finding, system/model, limitation]

### Foundational source
[Original or most foundational source, if available.]

### Current understanding
[What is generally accepted.]

### Uncertainty or controversy
[What remains unclear, debated, or contradictory.]

### Related concepts
- [Related concept 1]
- [Related concept 2]

### Source notes
[Title, authors, year, journal, DOI or PMID if available.]
[For direct quotations, include page number when possible.]
```

## K. Field Map Requirement

Before a full explanation, produce a concise field map. For short answers, compress it to a paragraph.

```
## Field Map

### 1. Core problem
[What problem is this field trying to solve?]

### 2. Established background
[What was already known before the target paper?]

### 3. Knowledge gap
[What remained unknown or unresolved?]

### 4. Available methods
[What methods, models, datasets, or clinical tools made this study possible?]

### 5. Competing explanations
[What alternative hypotheses or controversies existed?]

### 6. Why this paper was needed
[Why this target paper logically follows from previous literature.]
```

## L. Required Visible Output

When this strategy is applied, include a concise section. For quick answers, keep it very short.

```
## Reference Background Used

- Lanes considered / prioritized: [...]
- Must-select references auto-selected: [...]
- Additional references selected by priority: [...]
- Why the selected references mattered: [...]
- Depth used: [depth 1 / depth 2 / depth 3]
- Knowledge stored or reused: [...]
```

## M. Evidence and Access Limits

Do not invent what a cited reference says. If the full text is unavailable, use only accessible information — citation context in the target paper, title and abstract, PubMed record, DOI metadata, or available figures, tables, or excerpts — and clearly state when reference analysis is limited by access.

## N. Final Rule

Always explain the target paper using the necessary background built from its key reference chains. Do not treat a scientific or medical paper as an isolated document unless the user explicitly asks for an isolated reading.
