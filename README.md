# LLD Practice Platform

A focused MVP for practicing Low-Level Design problems, submitting a design, receiving explainable rubric-based feedback, and reviewing previous attempts.

## MVP Flow
Choose Problem → Start Practice → Write Design → Submit → Receive Feedback → Review History → Try Again

## Features
- 4 LLD practice problems: Parking Lot, Vending Machine, Elevator, Library Management
- Structured text submission
- Rubric-based deterministic evaluation
- Explainable feedback with criterion, score, evidence, concern, and suggestion
- Submission status: Submitted → Evaluating → Completed / Failed
- Attempt history stored in browser localStorage
- Retry flow
- Basic validation and failure handling

## Tech Stack
- HTML5
- CSS3
- Vanilla JavaScript
- Browser localStorage

This deliberately uses a lightweight client-only implementation for a 2-day MVP. The domain boundaries and evaluator abstraction are documented so an API/database/LLM evaluator can be added later.

## Run
Open `app/index.html` in a modern browser. No build step is required.

## Test
Open `tests/test.html` in a browser. It runs lightweight unit-style tests for the core evaluation logic.

## Design
See `docs/RESEARCH.md` and `docs/DESIGN.md`.

## Limitations
- No authentication or multi-user backend
- Attempts are stored locally in the browser
- Evaluation is rule-based in this prototype rather than calling an external LLM
- No visual UML editor or code execution sandbox

## Future Extension
The evaluator can be replaced/extended behind an `Evaluator` interface with AI, rule-based, or human evaluators. Submission formats can also be extended beyond text without changing the learner journey.
