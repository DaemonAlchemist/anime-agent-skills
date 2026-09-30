---
name: continuous-learning
description: Analyzes agent interactions, user feedback, and project corrections to continuously update, refine, or create agent skills that better adhere to the user's workflow preferences.
---

# Continuous Learning & Skill Evolution Skill

This skill governs the agent's meta-learning and self-improvement processes. As the agent collaborates with the user across creative, engineering, and production tasks, it continuously reflects on user feedback, corrections, recurring preferences, and operational friction points to systematically analyze, update, and evolve its own skill library.

---

## Core Principle: Adaptive Self-Improvement

An agent should never make the same mistake twice or require the user to repeat the same preference. Every correction, preference, and workflow realization represents institutional knowledge that must be codified into the project's living skills.

```text
User Interaction / Correction / Preference
           │
           ▼
[1. Learning Signal Detection]
  ├── Explicit corrections ("No, do it this way...")
  ├── Clarifications on style, staging, or architecture
  ├── Recurring workflow patterns or preferred toolchains
  └── Post-milestone directorial / technical reviews
           │
           ▼
[2. Knowledge Routing & Classification]
  ├── Is it a reusable methodology? ──► Update or Create Skill in `.agents/skills/`
  ├── Is it project-specific structure? ──► Update `project_structure.md`
  └── Is it a hard behavioral constraint? ──► Update Rule in `.agents/rules/`
           │
           ▼
[3. Skill Audit & Delta Analysis]
  ├── Inspect existing skills for coverage gaps or obsolete instructions
  └── Identify exact sections needing enhancement (rules, templates, anti-patterns)
           │
           ▼
[4. Direct Codification & Refactoring]
  ├── Update existing skill or scaffold a new modular skill
  └── Verify generic applicability, clear frontmatter, and non-contradiction
           │
           ▼
[5. Confirmation & Transparency]
  └── Inform the user how the skill was updated to honor their preference
```

---

## When to Trigger Skill Analysis & Evolution

The agent should invoke this skill and evaluate its skill library in the following scenarios:

1. **Immediate User Correction**:
   - The user corrects prompt syntax, cinematic staging, reference bus handling, or architectural rules (e.g., clarifying that an object is a plain prop rather than advanced tech, or that a camera angle must be static without on-screen figures).
2. **Preference Identification**:
   - The user expresses a strong stylistic, formatting, or organizational preference (e.g., favoring single-door rustic architecture over double doors, preference for explicit hard cuts to avoid morphing, or strict 9-image bus limits).
3. **Workflow Discovery & Tool Integration**:
   - A new tool, AI engine, rendering pipeline, or node graph (e.g., ComfyUI, Wan, Hunyuan, Blender, MiniMax) is integrated, requiring documented procedures.
4. **Direct Command / Request**:
   - The user triggers `/learn`, asks the agent to "remember this", or explicitly requests skill updates.
5. **Milestone Retrospective**:
   - At the conclusion of a sequence, chapter, or major production run, conducting a brief audit to capture lessons learned.

---

## Knowledge Routing: Skill vs. Project Notes vs. Rules

Before updating files, classify the learned information into its proper destination:

| Destination | Scope | Example Information |
| :--- | :--- | :--- |
| **Skill (`.agents/skills/<name>/SKILL.md`)** | **Generic, Reusable Procedures** | - Video prompt syntax and anti-hallucination techniques<br>- How to de-muddle high-action AI video shots<br>- Cinematic camera staging and 180° line rules<br>- Shot card schemas and transition timing |
| **Project Notes (`project_structure.md`)** | **Repository-Specific Facts** | - Directory paths for scripts, panels, and turnarounds<br>- Specific character names, lore ages, and canon props<br>- File naming and numbering schemes for the current comic |
| **Rules (`.agents/rules/*.md`)** | **Strict Global Constraints** | - "Never output placeholder images"<br>- "Always preserve existing comments in code"<br>- "Keep prompt suites strictly in 16:9 aspect ratio" |

> [!IMPORTANT]
> **Keep Skills Generic**:
> When updating a skill based on a user interaction, **abstract away story-specific details**. Formulate the lesson as a universal directorial, technical, or prompt-engineering best practice that works across any project.

---

## Skill Evolution Runbooks

### Runbook A: Codifying an Explicit Directorial / Prompt Correction

When the user points out a flaw in a prompt or shot design (e.g., "The shot is getting muddled; no characters should be on screen"):

1. **Identify Root Cause**:
   - Why did the prompt muddle the output? (e.g., Describing off-screen actions with active character tags causes diffusion models to hallucinate characters in frame).
2. **Locate Target Skill**:
   - Find the skill that governs this task (e.g., `minimax-h3-prompt-craft` or `comic-shot-breakdown`).
3. **Add Prescriptive Rules & Anti-Patterns**:
   - Add a concrete guideline to the skill under an appropriate section (e.g., "Clean Off-Screen Action Framing"):
     ```markdown
     > [!TIP]
     > **Preventing Hallucinations in Off-Screen Impact Shots**:
     > When an action occurs off-screen (e.g., a strike landing, blood splatter, dropped weapon):
     > - Explicitly declare that the frame is completely devoid of people: *"The frame is completely devoid of people; no characters are on screen."*
     > - Do not cite character subject tags (`<Subject N>`) in the detailed description of that shot, as generation models will attempt to render the subject in frame.
     > - Frame the environment statically and describe purely physical, environmental consequences arriving from off-screen.
     ```
4. **Update Rubric / Quality Checks**:
   - If applicable, update `cinematic-director-review` to ensure future pre-flight checks flag this specific issue before prompts are finalized.

---

### Runbook B: Updating Existing Skills with User Preferences

When the user shows a preference for a specific workflow format (e.g., unified master reference buses, strict shot durations, specific soundscape layering):

1. **Locate the Relevant Skill**:
   - View the skill's `SKILL.md` using `view_file`.
2. **Refine Guidelines & Templates**:
   - Update instructions, tables, or templates to incorporate the preferred pattern as the default recommended approach.
3. **Verify Clarity & Consistency**:
   - Ensure the new guidance does not conflict with existing sections.
   - Maintain clean markdown, clear section headers, and actionable checklists.

---

### Runbook C: Minting a New Specialized Skill

When a new domain or specialized procedure emerges that does not fit into existing skills:

1. **Check Naming & Directory Convention**:
   - Choose a concise, hyphenated lowercase identifier: `skills/<new-skill-name>/`.
2. **Draft the `SKILL.md` File**:
   - Include required YAML frontmatter:
     ```yaml
     ---
     name: new-skill-name
     description: Concise statement of what the skill accomplishes and exactly when the agent should activate it.
     ---
     ```
3. **Structure the Content**:
   - `# [Skill Title]`
   - `## Overview & Objectives`
   - `## Core Principles & When to Use`
   - `## Step-by-Step Execution Workflow`
   - `## Templates, Tables & Examples`
   - `## Common Pitfalls & Anti-Patterns`
4. **Register with Ecosystem**:
   - Add a cross-reference in `comic-to-animation` and `project_structure.md` so the new skill is discovered by all agents.

---

## Agent Learning Audit Checklist

When closing a task turn or reflecting on user interactions, verify:
- [ ] Did the user provide a correction that applies beyond this single file?
- [ ] Is that correction captured in the relevant skill's instructions?
- [ ] Is the skill guidance generic rather than tied to this specific story?
- [ ] If the correction was repository-specific, was `project_structure.md` updated?
- [ ] Did I communicate the updated skill capability clearly to the user?
