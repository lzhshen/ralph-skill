# SpecKit Agent Instructions

## Overview

SpecKit is an agentic framework for specifying, planning, and implementing software features. It replaces the legacy manual PRD process with a structured, autonomous pipeline.

## Core Workflow

1.  **Initialize**: `/.specify/scripts/bash/create-new-feature.sh "Feature Description"`
2.  **Specify**: Agent runs `/speckit.specify` to generate `spec.md`.
3.  **Clarify**: Agent runs `/speckit.clarify` to resolve ambiguities.
4.  **Plan**: Agent runs `/speckit.plan` to create `plan.md`.
5.  **Tasks**: Agent runs `/speckit.tasks` to generate `tasks.md`.
6.  **Implement**: Agent runs `/speckit.implement` to execute tasks.

## Key Files & Directories

- `.specify/memory/constitution.md`: Core project rules and principles.
- `specs/[branch-name]/`: Directory containing all artifacts for a feature.
  - `spec.md`: The requirements.
  - `plan.md`: The technical plan.
  - `tasks.md`: The execution tasks.
  - `checklists/`: Quality assurance checklists.

## Commands

The agent operates by executing specific slash commands defined in `.claude/commands/`:

- `/speckit.constitution`: Update project principles.
- `/speckit.specify`: Create/update requirements.
- `/speckit.clarify`: Interactive ambiguity resolution.
- `/speckit.plan`: Generate technical architecture.
- `/speckit.tasks`: Break plan into executable tasks.
- `/speckit.implement`: Execute the code changes.
- `/speckit.analyze`: consistency check.

## Operational Guide

- **Always** check the `.specify/scripts/bash/check-prerequisites.sh` status before starting.
- **Always** update `AGENTS.md` with new patterns found during implementation.
- **Never** modify `spec.md` or `plan.md` manually during implementation unless a critical error is found (use `/speckit.clarify` or update process).
