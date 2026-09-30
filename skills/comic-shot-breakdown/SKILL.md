---
name: comic-shot-breakdown
description: Translates webcomic pages, panel art, and narrative scripts into cinematic shot lists and storyboards optimized for AI video generation pipelines.
---

# Comic Shot Breakdown Skill

This skill provides a standardized procedure for decomposing webcomic layouts and narrative scripts into cinematic shot lists formatted for AI video generation (e.g., ComfyUI, MiniMax, Wan, Hunyuan).

## When to Use

Use this skill whenever:
- Adapting a new chapter, scene, or page sequence from comic panels into video shots.
- Reconciling scripted action with comic panel illustrations.
- Preparing shot cards, timing, camera vectors, and conditioning asset references for video prompts.

## Core Principle: Script-First Cinematic Adaptation

> [!IMPORTANT]
> **Script Takes Precedence Over Comic Panels**:
> Comic pages and panels are **visual, stylistic, and asset references**—they are **not an authoritative 1:1 shot list**. 
> - The narrative **script dictates the scene's emotional rhythm, pacing, spatial blocking, and dramatic tension**.
> - An animated sequence should be designed cinematically: leveraging camera motion (dolly, tracking, crane, crash zooms), depth of field, environmental atmosphere (embers, smoke, lighting shifts), and immersive pacing that may expand or reconceptualize static comic panels.
> - Comic panels should be used to ground character designs, costumes, color palettes, key poses, and direct image conditioning.

## Procedure

### 1. Script-First Narrative Breakdown
- **Extract the Core Narrative Arc**: Identify the emotional beats, tempo shifts, physical obstacles, and character objectives directly from the script.
- **Cinematic Framing & Staging**: Design shots for maximum cinematic impact (e.g., establishing quiet tension before sudden chaos, utilizing POVs, tracking runs, Dutch angles for peril).
- **Cross-Reference Comic Assets**: Map the cinematic shots back to the comic panels and layered PSDs to harvest visual references, starting frames, and color palettes.
- **Expand Static Gaps**: Add connecting and atmospheric shots that comic pages skip between gutters (e.g., footsteps, environmental destruction, lingering dread).

### 2. Shot Card Specification
Each shot must define the following core parameters:

| Parameter | Description |
| :--- | :--- |
| **Shot ID** | Sequence & shot index (e.g., `SH-001`, `SH-002`) |
| **Comic Source** | Page number, panel coordinates, or cut asset filename |
| **Framing & Angle** | EWS / WS / MS / CU / ECU; Eye-level / Low-angle / Dutch / High-angle |
| **Camera Movement** | Static, Dolly In/Out, Tracking, Pan, Whip Pan, Crane |
| **Duration (Sec)** | Target generation duration (typically 2.0s – 5.0s for AI video generators) |
| **Subject Action** | Explicit physical movement, speed, and emotional beat |
| **Atmosphere & FX** | Lighting, smoke, fire, particle sparks, magic energy glyphs |
| **Audio / Dialogue** | Spoken lines, Foley effects, ambient soundscape |
| **Conditioning Asset**| Panel image / Character turnaround / Background plate to feed image-to-video |

### 3. Pacing & Transition Logic
- **Action Escalation**: Tighten shot durations during conflict (e.g., 1.5s - 2.5s for strikes/reactions).
- **Emotional Breathers**: Extend establishing or reaction beats (3.0s - 4.5s) to let atmosphere and dread sink in.
- **Transition Types**: Match cuts, whip pans, lighting flashes, or hard cuts on action.

### 4. Generation Prompt Translation
- Convert the visual direction into clear, descriptive prompts without ambiguous metaphors.
- Emphasize temporal motion cues (e.g., *"camera dollies forward smoothly as..."*, *"cape billows violently in heat waves..."*).

### 5. Output Artifact Storage
- **Dedicated Scene Directory**: Save the completed shot list and all associated scene artifacts directly into that scene's designated animation directory as identified in the project structure notes:
  `<scene_output_dir>/<scene>_shot_list.md`
- Never save scene artifacts exclusively in temporary or system scratch locations.
