# Research Note — LLD Practice Platform

## 1. Learner Problem

Low-Level Design practice is easy to start but difficult to evaluate. A learner can produce a design for a Parking Lot, Elevator, or Vending Machine and still be uncertain about whether responsibilities are well separated, abstractions are appropriate, or the design will remain maintainable when requirements change.

The core problem is therefore not simply access to more questions. The learner needs a repeatable practice loop and feedback that points to evidence in the submitted design.

## 2. Lightweight Research

I reviewed common LLD/interview preparation approaches including coding-interview platforms, GitHub LLD repositories, and community/tutorial-style LLD resources.

### Observed approaches
- **Coding practice platforms:** strong problem discovery and repeat practice, but their evaluation is generally optimized for executable code and automated test cases rather than class responsibility and design reasoning.
- **GitHub LLD repositories:** provide many examples and reference implementations, but feedback is usually absent and learners may compare their design against one reference implementation even when several designs can be valid.
- **Tutorial/community resources:** explain SOLID principles, design patterns, and common problems well, but the learner often has to self-evaluate the quality of an original attempt.

## 3. Gaps Identified

1. Feedback should evaluate design dimensions rather than only correctness.
2. A reference solution should not be treated as the only valid design.
3. Feedback should quote or identify evidence from the learner's own submission.
4. Attempt history should help learners see improvement over repeated practice.
5. Evaluation should be separated from the practice flow so a slower evaluator can run asynchronously later.

## 4. Product Direction

The MVP focuses on four problems and one submission format: structured text. The learner records assumptions, classes and responsibilities, relationships, patterns/reasoning, and edge cases.

The evaluator uses a fixed rubric across requirement understanding, responsibilities, encapsulation/interfaces, coupling/cohesion, abstraction, extensibility, edge cases, and explanation quality.

The product intentionally avoids a full UML editor, code execution environment, LMS, or complex infrastructure. Those features add implementation cost without improving the first version of the core learning loop enough to justify them in a two-day assignment.

## 5. Key Product Principle

The product should answer: **“What can I improve in my next design?”** rather than simply: **“What score did I get?”**
