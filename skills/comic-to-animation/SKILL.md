---
name: comic-to-animation
description: Guides the adaptation of webcomic panels, graphic novels, and story scripts into animated sequences, including shot breakdown, asset referencing, prompt synthesis, and generation pipeline management.
---

# Comic-to-Animation Pipeline

This skill orchestrates the end-to-end workflow for transforming webcomic pages, graphic novel panels, and narrative scripts into cinematic animated video sequences.

## Pipeline Architecture

```text
1. Script-First Ingestion & Cinematic Breakdown
   ├── Review Script as the primary narrative & pacing driver
   ├── Reference Chapter/Scene Panels for visual styles, poses, character silhouettes, and environmental cues
   └── Check Project Lore / Character Bibles for designs, color palettes, and world rules

2. Asset Preparation & Conditioning
   ├── High-res Panel / Layer Isolation (from source artwork, flats, inks, panel cuts)
   ├── Character References & Model Turnarounds (expression sheets, key art)
   └── Clean inpainting / background separation where depth or multiplane motion is needed

3. Shot Sequencing & Prompt Engineering
   ├── Shot direction (camera angle, motion vectors, pacing, focal length)
   ├── Motion prompting (character action, atmospheric FX: fire, smoke, weather, particle dynamics)
   └── Configuration for generation engines (e.g., ComfyUI / MiniMax / Wan / Hunyuan)

4. Generation & Iteration
   ├── Execution of video generation runs
   ├── Directorial Quality Assessment (`cinematic-director-review`: character fidelity, anatomy, temporal stability, narrative resonance)
   └── Iteration tracking (logging seeds, prompts, and revisions)

5. Post-Assembly & Audio
   ├── Sequence assembly & timing
   ├── Audio / voiceover alignment (Reference Bus, sound FX, theme music)
   └── Final render packaging
```

## Project Configuration & Directory Resolution

> [!NOTE]
> **Dynamic Path Resolution via Local Project Structure Notes**:
> Different projects organize scripts, artwork, and generation folders differently.
> Before starting production on a scene, consult the project's local structure notes (e.g. `project_structure.md` created by `project-structure-analyzer`) to resolve paths for:
> - **Narrative Scripts & Lore Bibles**: Source scripts and character documentation.
> - **Comic Art & Panel Cuts**: High-resolution panels, layered artwork, and color palettes.
> - **Character Turnarounds & Prop Sheets**: Model anchors for image conditioning.
> - **Animation Staging & Output Directories**: The dedicated production folder where scene artifacts reside.
> - **AI Engine Workflows & Experiments**: Node graphs, pipelines, and test folders.

## Artifact & Output Storage Rules

> [!IMPORTANT]
> **Scene Artifact Storage Location**:
> All artifacts for an animated scene—including shot lists, prompt files, master subject definitions, reference plates, overview maps, rendered video clips, and audio tracks—**must** be saved directly inside that scene's designated animation directory as specified in the project structure notes. Do not leave production artifacts in temporary directories or scratch folders.

## Sub-Skills & Specialized Runbooks

As specialized procedures are refined during production, modular sub-skills provide targeted support:
- `project-structure-analyzer`: Analyzing project directory layout and maintaining the local `project_structure.md` notes file.
- `comic-shot-breakdown`: Translating narrative scripts and panels into cinematic shot lists and timing.
- `cinematic-set-reference`: Designing, enriching, and maintaining spatially consistent environment plates and overview maps.
- `minimax-h3-prompt-craft`: Structuring Minimax Hailuo (H3) ref2vid multi-subject prompts and retention schemas.
- `cinematic-director-review`: Directorial quality assessment, multi-dimensional evaluation rubric, and iterative review.
- `continuous-learning`: Reflecting on user preferences and feedback to continuously refine, adapt, and evolve agent skills.
