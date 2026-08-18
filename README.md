# llm-council-skill (backup)

This repository is a clean backup of a community-created Claude Code skill, saved into ruaijunggold's GitHub account for safekeeping and reuse.

## Source

Upstream repository: https://github.com/ngmeyer/council-review
Author: Neal Meyer
Commit backed up: e9a9ee372bc4e96eaa37ed1802dea2dafc245551 ("Sync to council-review V2.1 + point to ngmeyer/skills monorepo", 2026-05-30)
License: MIT (see LICENSE, upstream copyright retained)
Installation date: 2026-08-18

## What this skill does

council-review runs any question, plan, PR, or piece of code through a council of five independent AI advisors, each using a distinct reasoning method: The Contrarian (Inversion — assumes it shipped and failed, traces backward to the cause), The First Principles Thinker (Decomposition — breaks the problem into atomic claims and challenges each one), The Expansionist (Analogy — looks for the upside everyone else is missing), The Outsider (Naive questioning — zero-context fresh eyes, flags anything that needs insider knowledge), and The Executor (Dependency graphing — maps the critical path and the first concrete action).

The five advisors answer independently and in parallel. Their answers are then anonymized (shuffled and relabeled Response A through E, persona language stripped) before a peer-review round, so each advisor critiques the other four without knowing who wrote what and without being able to favor its own answer. A mandatory Devil's Advocate step then attacks whatever answer the council is converging on. Finally, a Chairman (running in the main session, not a sub-agent) synthesizes everything into one verdict that separates consensus, disagreements, blind spots, a recommendation, and a single concrete next action.

This is explicitly designed to reduce AI sycophancy: advisor prompts contain a sycophancy guardrail ("do not defer to any answer the framing seems to expect"), and the devil's-advocate step is specifically aimed at breaking premature, deferential consensus.

## Why this repo, not karpathy slash llm-council

Karpathy's original llm-council project queries multiple different model providers. This skill instead runs entirely inside Claude Code using sub-agents with distinct personas and reasoning methods on a single model family, so no external API keys are required.

## Local modifications

None. The files in this repository (SKILL.md, CLAUDE.md, this README's Source and Usage sections, LICENSE, tests folder, docs folder) are an unmodified copy of the upstream commit listed above. The original upstream README is preserved as UPSTREAM_README.md.

## Usage

Install SKILL.md into your Claude Code skills directory, for example a user-level path like council-review/SKILL.md under your Claude skills folder, or a project-level path under your project's .claude/skills folder. Then in a Claude Code session, invoke it with a slash command such as: council-review Should we adopt GraphQL for our public API question mark

Or simply say one of the trigger phrases in conversation: "council this", "run the council", "pressure-test this", "stress-test this", "war room this".

A quick lite mode runs three advisors with no peer review, but still runs the mandatory devil's advocate step: council-review with the quick flag.

See SKILL.md for the full protocol and all flags: adaptive, confidence, measure-diversity, and jury.
