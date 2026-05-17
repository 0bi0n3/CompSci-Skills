<!-- <p>
  <a href="https://www.aihero.dev/s/skills-newsletter">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skills-repo-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png">
      <img alt="Skills" src="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png" width="369">
    </picture>
  </a>
</p> -->

# CompSci Skills (Fork of Matt Pocock Skills)

[![skills.sh](https://skills.sh/b/mattpocock/skills)](https://skills.sh/mattpocock/skills)

This fork keeps the original skills-first architecture and adapts it for computer science experimentation work.

It is based on Matt Pocock’s **Real Skills for Engineers: Claude’s Guild Breakdown**, with adapted wording and workflows for experimental pipelines instead of only end-to-end product shipping.

The underlying structure remains: small composable skills, prompt-driven setup, and agent workflows that can push/pull work via GitHub issues.

## Fork Goal

Build a repeatable agent-assisted methodology for:

- end-to-end **experiments**
- data processing pipelines with tests
- ablation/toggle studies
- result and model-log tracking

This fork targets computer science workflows where correctness, reproducibility, and observability are first-class.

## Methodology Shift (Product → Experiment)

Compared with the original framing, this fork emphasizes:

1. **Problem framing in CS language**  
   Build shared terminology around research questions, hypotheses, modalities, dataset splits, metrics, and failure modes.
2. **Pipeline-first execution**  
   Design and test data ingestion, preprocessing, training/eval loops, and reporting as explicit stages.
3. **Ablation as a default loop**  
   Treat config toggles and controlled comparisons as part of normal development.
4. **Tracking as core infrastructure**  
   Keep issue tracking in GitHub and add hooks for experiment systems (for example Weights & Biases) to track model logs and outcomes.
5. **Handoff-ready documentation**  
   Keep context docs and ADRs up to date so multiple agents can safely continue work.

## Initial Experiment Intake Questions

For early prompting and grilling, agents should start with:

1. **What area of computer science are these experiments designed for?**
2. **What modalities will you be working with?**
3. **What datasets will you be working with?**

Then follow with:

- What is the primary hypothesis?
- What baseline should be compared against?
- What metrics define success/failure?
- What ablation toggles are required?
- How will runs and artifacts be tracked and reproduced?

## Quickstart (30-second setup)

1. Run the skills.sh installer:

```bash
npx skills@latest add mattpocock/skills
```

2. Pick the skills you want, and which coding agents you want to install them on. **Make sure you select `/setup-matt-pocock-skills`**.

3. Run `/setup-matt-pocock-skills` in your agent. It will:
   - Ask you which issue tracker you want to use (GitHub, Linear, or local files)
   - Ask you what labels you apply to ticks when you triage them (`/triage` uses labels)
   - Ask you where you want to save any docs we create

4. Bam - you're ready to go.

## Chaptered Buildout Plan For This Fork

Use these as implementation chapters other agents can pick up independently:

### Chapter 1 — Domain & Vocabulary Layer

- Adapt shared language docs from software-product terms to computer-science experiment terms.
- Define canonical terminology for datasets, modalities, task families, metrics, and ablations.
- Keep `CONTEXT.md` and ADRs as source-of-truth artifacts.

### Chapter 2 — Grilling & Planning Layer

- Reframe grilling to stress methodology and experimental design quality.
- Ensure intake includes CS area, modalities, datasets, hypotheses, and evaluation plan.
- Produce issue-ready slices for experiment milestones.

### Chapter 3 — Experiment Pipeline Execution Layer

- Keep TDD and diagnosis loops, but apply them to data and model pipelines.
- Focus on deterministic stages, testable transformations, and reproducible runs.
- Encourage vertical slices that produce measurable experiment outputs.

### Chapter 4 — Ablation & Evaluation Layer

- Standardize ablation toggle definition and execution.
- Ensure each run can be compared against a clear baseline.
- Define a reporting template for metrics, regressions, and tradeoffs.

### Chapter 5 — Tracking & Integrations Layer

- Keep GitHub issue push/pull and triage as a foundation.
- Add integration hooks for experiment tracking platforms such as Weights & Biases.
- Track model logs, configs, metrics, and artifacts for full reproducibility.

### Chapter 6 — Multi-Agent Collaboration Layer

- Keep handoff and issue decomposition workflows from the original.
- Require each chapter to produce clear, delegable outputs so multiple agents can parallelize work safely.
- Preserve compatibility with existing skill architecture wherever possible.

## What Stays the Same from the Original

- Small, composable skills instead of monolithic process frameworks.
- Prompt-first setup and explicit issue-tracker workflows.
- Strong emphasis on shared language, iterative feedback loops, and architecture quality.

## What Changes in This Fork

- Product-centric wording becomes experiment-centric wording.
- End-to-end app delivery expands to end-to-end experiment + data pipeline delivery.
- Testing remains mandatory, and is paired with ablation studies and experiment tracking.
- GitHub remains central for planning/triage, with additional hooks for model observability tooling.

## Reference

### Engineering

Skills I use daily for code work.

- **[diagnose](./skills/engineering/diagnose/SKILL.md)** — Disciplined diagnosis loop for hard bugs and performance regressions: reproduce → minimise → hypothesise → instrument → fix → regression-test.
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)** — Grilling session that challenges your plan against the existing domain model, sharpens terminology, and updates `CONTEXT.md` and ADRs inline.
- **[triage](./skills/engineering/triage/SKILL.md)** — Triage issues through a state machine of triage roles.
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)** — Find deepening opportunities in a codebase, informed by the domain language in `CONTEXT.md` and the decisions in `docs/adr/`.
- **[setup-matt-pocock-skills](./skills/engineering/setup-matt-pocock-skills/SKILL.md)** — Scaffold the per-repo config (issue tracker, triage label vocabulary, domain doc layout) that the other engineering skills consume. Run once per repo before using `to-issues`, `to-prd`, `triage`, `diagnose`, `tdd`, `improve-codebase-architecture`, or `zoom-out`.
- **[tdd](./skills/engineering/tdd/SKILL.md)** — Test-driven development with a red-green-refactor loop. Builds features or fixes bugs one vertical slice at a time.
- **[to-issues](./skills/engineering/to-issues/SKILL.md)** — Break any plan, spec, or PRD into independently-grabbable GitHub issues using vertical slices.
- **[to-prd](./skills/engineering/to-prd/SKILL.md)** — Turn the current conversation context into a PRD and submit it as a GitHub issue. No interview — just synthesizes what you've already discussed.
- **[zoom-out](./skills/engineering/zoom-out/SKILL.md)** — Tell the agent to zoom out and give broader context or a higher-level perspective on an unfamiliar section of code.
- **[prototype](./skills/engineering/prototype/SKILL.md)** — Build a throwaway prototype to flesh out a design — either a runnable terminal app for state/business-logic questions, or several radically different UI variations toggleable from one route.

### Productivity

General workflow tools, not code-specific.

- **[caveman](./skills/productivity/caveman/SKILL.md)** — Ultra-compressed communication mode. Cuts token usage ~75% by dropping filler while keeping full technical accuracy.
- **[grill-me](./skills/productivity/grill-me/SKILL.md)** — Get relentlessly interviewed about a plan or design until every branch of the decision tree is resolved.
- **[handoff](./skills/productivity/handoff/SKILL.md)** — Compact the current conversation into a handoff document so another agent can continue the work.
- **[write-a-skill](./skills/productivity/write-a-skill/SKILL.md)** — Create new skills with proper structure, progressive disclosure, and bundled resources.

### Misc

Tools I keep around but rarely use.

- **[git-guardrails-claude-code](./skills/misc/git-guardrails-claude-code/SKILL.md)** — Set up Claude Code hooks to block dangerous git commands (push, reset --hard, clean, etc.) before they execute.
- **[migrate-to-shoehorn](./skills/misc/migrate-to-shoehorn/SKILL.md)** — Migrate test files from `as` type assertions to @total-typescript/shoehorn.
- **[scaffold-exercises](./skills/misc/scaffold-exercises/SKILL.md)** — Create exercise directory structures with sections, problems, solutions, and explainers.
- **[setup-pre-commit](./skills/misc/setup-pre-commit/SKILL.md)** — Set up Husky pre-commit hooks with lint-staged, Prettier, type checking, and tests.
