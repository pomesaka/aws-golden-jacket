# AWS Golden Jacket

Goal: earn every active AWS Certification required for the AWS Golden Jacket.

This repository is a learning log, service dictionary, quiz archive, and progress tracker for the fastest practical path to the Golden Jacket.

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
roadmap/       Certification list, progress, and target timeline
services/      AWS service dictionary focused on exam traps and design decisions
quizzes/       Quiz logs and review notes
resources/     Official references and source list
templates/     Reusable note formats
```

## Active working loop

1. Solve 5-10 AWS quiz questions.
2. Record wrong or uncertain answers in `quizzes/`.
3. Create or update service notes in `services/`.
4. Re-test weak areas after several days.
5. Book the next exam before motivation cools down.

## Next actions

- [ ] Confirm current Golden Jacket eligibility rules from official AWS event/certification pages.
- [ ] Decide the first exam date.
- [ ] Start with SAA-level review while collecting AWS-specific unknown services.
- [ ] Build a weak-area list from quizzes.
