# AWS Golden Jacket

Goal: earn every active AWS Certification required for the AWS Golden Jacket.

This repository is a learning log, service dictionary, quiz archive, and progress tracker for the fastest practical path to the Golden Jacket.

## Current status

- Current exam focus: AWS Certified Solutions Architect - Associate (SAA-C03)
- Current state: Quiz-ready
- Next action: start the SAA 30-question diagnostic quiz using `exams/saa/diagnostic-quiz-plan.md`
- Progress source of truth: `roadmap/progress.md`
- Exam order source of truth: `roadmap/exam-order.md`

## Current strategy

- Prioritize active AWS Certifications, not an old fixed meaning of "12 crowns".
- Use AWS official sources as the baseline.
- Learn by quiz -> mistake analysis -> service note update.
- Optimize for speed while avoiding fragile memorization.

## Profile assumptions

- Around 2 years of AWS application operations experience.
- Hands-on with ECS Fargate, CloudFront, Lambda, ECS RunTask, and async batch jobs.
- Previous Kubernetes experience.
- Strength: architecture thinking and requirement-based service selection.
- Gap: AWS-specific service vocabulary and edge-case rules.

Do not store confidential company information, customer architecture, credentials, private diagrams, or internal incident details in this repository.

## Repository structure

```text
roadmap/       Certification list, progress, exam order, and study plan
exams/         Per-exam workspaces, starting with SAA
services/      AWS service dictionary focused on exam traps and design decisions
concepts/      Cross-service architecture concepts
comparisons/   Service comparison notes for exam traps
quizzes/       Quiz logs and review notes
official/      Official documentation coverage tracking
resources/     Official references and source list
templates/     Reusable note formats
```

## How to continue

1. Open `roadmap/progress.md` to see current status.
2. Open `roadmap/exam-order.md` to see the planned certification order.
3. Open `exams/saa/diagnostic-quiz-plan.md` to start the next quiz.
4. Record wrong or uncertain answers in `exams/saa/mistakes.md` and `quizzes/`.
5. Promote repeated weak points into `services/`, `concepts/`, or `comparisons/`.

## Active working loop

1. Solve 5-10 AWS quiz questions.
2. Record wrong or uncertain answers.
3. Create or update service notes.
4. Re-test weak areas after several days.
5. Book the next exam before motivation cools down.

## Open decisions

- Confirm current Golden Jacket eligibility rules from official AWS event/certification pages.
- Decide the first SAA exam date after the 30-question diagnostic.
- Confirm how to handle Advanced Networking retirement/replacement for Golden Jacket timing.
