# Design Note — LLD Practice Platform

## MVP Scope

The prototype supports:
1. Problem discovery
2. Starting an attempt
3. Structured text design submission
4. Submission status
5. Rubric-based evaluation
6. Explainable feedback
7. Attempt history
8. Retry

## User Flow

```text
Problem List
    ↓
Problem Details
    ↓
Start Attempt
    ↓
Write Design
    ↓
Submit
    ↓
Submitted → Evaluating → Completed / Failed
    ↓
Feedback
    ↓
History / Try Again
```

## Domain Model

```text
Problem
  └── requirements

Attempt
  ├── Problem
  └── Submission

Submission
  └── content

Evaluation
  ├── status
  ├── evaluatorType
  └── FeedbackItem[]

FeedbackItem
  ├── criterion
  ├── score
  ├── evidence
  ├── concern
  ├── suggestion
  └── confidence
```

## Evaluator Abstraction

The core design treats evaluation as a replaceable behaviour:

```text
Evaluator
├── RuleBasedEvaluator (implemented in MVP)
├── AIEvaluator (future)
└── HumanEvaluator (future)
```

A future backend could expose:

```js
class Evaluator {
  evaluate(problem, submission) {}
}
```

The practice flow should not know how evaluation is performed. This supports the assignment's change test: adding another evaluator should not require rewriting problem selection, attempt creation, or history.

## Submission Format Change Test

The MVP uses structured text. A future `Submission` model can contain a `type` and format-specific content, for example `text`, `code`, or `diagram`. The attempt and evaluation lifecycle remains unchanged.

## Evaluation Approach

The prototype uses deterministic heuristics to demonstrate explainable evaluation without depending on an external API key. Each criterion produces:
- score
- evidence
- concern
- suggestion
- confidence

This is intentionally preferable to an unconstrained “give a score out of 100” prompt.

A production version could send the same fixed rubric to an LLM and require structured JSON output. Deterministic validation would remain responsible for required fields and state transitions, while AI would handle design-quality reasoning.

## State Handling

Submission states are:
- `Submitted`
- `Evaluating`
- `Completed`
- `Failed`

The prototype transitions through these states locally. In a production system, the submission would be persisted before evaluation starts, and evaluation could run asynchronously so a slow evaluator does not block the submission request.

## Architecture

The prototype is intentionally a modular client-side MVP:

```text
UI
 ↓
Application Functions
 ↓
Domain / Evaluation Logic
 ↓
localStorage Repository
```

A backend version could evolve to:

```text
React UI → REST API → Application Services → Domain → Repository → DB
                                      ↓
                                  Evaluator
```

A monolith is sufficient for the expected scale.

## Trade-offs

- **Text instead of UML editor:** much faster to build while still capturing responsibilities and reasoning.
- **LocalStorage instead of a database:** adequate for a demonstrable two-day prototype; not suitable for multi-user production use.
- **Rule-based evaluation instead of mandatory AI:** makes the demo reliable and reproducible without API credentials. AI is a clear extension point.
- **One application instead of microservices:** keeps domain logic understandable and avoids infrastructure unrelated to the assignment's LLD focus.
