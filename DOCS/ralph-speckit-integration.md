# Ralph + Spec-Kit Integration Analysis

## 1. Project Understanding

### Ralph (Current Project)
**Summary**: An "Infinite Loop" Autonomous Coding System.
**Core Mechanism**: Designed to overcome Context Window limitations. It breaks large features into small, independent "User Stories" and restarts the AI agent context for each story.
- **Persistence**: `prd.json` (Tasks), `progress.txt` (Learnings), Git (Code).
- **Pipeline**: `ralph.sh` loop -> New Agent Instance -> Implement Story -> Test -> Commit -> Next.
**Pain Point**: Relies heavily on a pre-existing, perfect task list (`prd.json`). Lacks macro-architectural awareness during execution.

### Spec-Kit
**Summary**: An "Architect-First" Agentic Workflow (Spec-Driven Development).
**Core Mechanism**: Forces "Thinking before Coding".
- **Constitution**: Immutable project rules.
- **Workflow**:
    1.  `/speckit.specify` -> `spec.md` (What & Why)
    2.  `/speckit.plan` -> `plan.md` (Architecture, Schema, API)
    3.  `/speckit.tasks` -> `tasks.md` (Execution Roadmap)
**Pain Point**: Great planning, but execution still requires manual hand-holding or long-context sessions.

---

## 2. Integration Proposal: "The Architect & The Builder"

**Concept**: Use **Spec-Kit** as the "Brain" (Architect) to generate the blueprint, and **Ralph** as the "Hands" (Builder) to execute it tirelessly.

### The Pipeline

#### Phase 1: The Architect (Spec-Kit)
User interacts with Spec-Kit to define the feature.
1.  **Define**: `spec.md` (Requirements)
2.  **Design**: `plan.md` (Technical Architecture)
3.  **Decompose**: `tasks.md` (Step-by-step checklist)

#### Phase 2: The Bridge (Glue Layer)
A transition step to format Spec-Kit's output for Ralph.
- **Action**: Convert `tasks.md` -> `prd.json`.
- **Context Injection**: ensure `plan.md` is available to Ralph.

#### Phase 3: The Builder (Ralph)
Ralph enters its infinite loop to execute the converted tasks.
- **Enhanced Prompt**: Ralph's `prompt.md` is updated to strictly follow `plan.md` as the source of truth for architecture, ensuring consistency across isolated iterations.

### Benefits
1.  **Architectural Integrity**: Ralph no longer "guesses" the architecture; it follows the `plan.md`.
2.  **Autonomous Execution**: Spec-Kit's detailed plan is executed without human intervention.
3.  **Context Management**: Solves the context window issue for large Spec-Kit plans.

---

## 3. Implementation Plan

1.  **Environment Setup**: Verify Ralph is working.
2.  **Integration**:
    - Import Spec-Kit templates (`.specify/`).
    - Develop `tasks-to-prd` bridge script.
    - Update `prompt.md` to reference `spec.md` and `plan.md`.
3.  **Execution**: Run the full cycle.
