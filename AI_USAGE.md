# AI_USAGE.md

AI tools were used as an engineering assistant, while final product and design decisions were reviewed and adapted by the candidate.

## 1. MVP Scope
AI suggested several possible features including UML editing, code execution, authentication, leaderboards, and advanced analytics. I rejected these for the two-day MVP because they increase implementation effort without improving the core practice-feedback-retry loop enough.

## 2. Evaluation Model
AI suggested that a simple overall score could be used. I rejected a score-only approach because LLD has multiple valid designs. I chose criterion-level feedback containing score, evidence, concern, suggestion, and confidence.

## 3. Evaluator Abstraction
AI helped identify the benefit of separating evaluation behaviour from the practice flow. I used an evaluator abstraction so a rule-based evaluator can later be replaced or supplemented by an AI or human evaluator.

## 4. Submission Extensibility
AI suggested separating the submission concept from its content format. I adopted this direction so text can be the MVP while code or diagram submissions can be added later without changing the attempt lifecycle.

## 5. Reliability
AI suggested explicit evaluation states. I adopted `Submitted`, `Evaluating`, `Completed`, and `Failed` so slow or failed evaluation is visible rather than appearing as a lost submission.
