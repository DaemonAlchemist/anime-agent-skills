---
name: project-structure-analyzer
description: Analyzes repository layout, discovers narrative scripts, comic assets, character references, and output paths, and records the project organization in a local project_structure.md notes file.
---

# Project Structure Analyzer Skill

This skill provides a systematic methodology for inspecting any comic, animation, or multimedia creative repository, discovering how its assets and workflows are organized, and recording the complete project architecture in a persistent, standardized local notes file (`project_structure.md`).

By maintaining this local notes file, all creative and generation skills (such as `comic-to-animation`, `comic-shot-breakdown`, `cinematic-set-reference`, and `minimax-h3-prompt-craft`) remain completely generic while dynamically resolving exact project paths and naming conventions without hardcoded assumptions.

---

## When to Use

- **Project Onboarding**: Running the initial audit when opening or beginning work on any new creative project or repository.
- **Pre-Production Pre-Flight**: Resolving where scripts, character models, source panels, and output folders are located before generating shot lists or video prompts.
- **Structure Updates & Reorganizations**: Updating the local notes file whenever new chapters, volumes, scenes, or art pipeline folders are created or moved.

---

## Analysis Methodology

Follow this 6-step procedure to analyze any project and compile its structure notes:

```text
1. Workspace Hierarchy Scan
   └── List root and primary subdirectories to determine overall repository layout.

2. Narrative & Script Discovery
   └── Locate story scripts, screenplays, world lore, character bibles, and synopses.
   └── Map narrative hierarchy (e.g., Saga > Book > Chapter/Episode > Scene > Page).

3. Visual Artwork & Source Asset Mapping
   └── Locate comic pages, panels, layered files (pencils, inks, flats, colors), and crops.
   └── Identify file types (.psd, .clip, .kra, .png, .jpg) and naming conventions.

4. Character Turnarounds, Palettes & Reference Anchors
   └── Locate character model sheets, turnarounds, expression sheets, and color palettes.
   └── Identify designated image-to-video / ref2vid conditioning assets.

5. Animation Output & Staging Conventions
   └── Determine where animated scene packages belong (e.g., dedicated scene `Anime/` folders).
   └── Identify standard naming for shot lists, prompt files, master subject files, and renders.

6. Compile / Update Local Notes File (`project_structure.md`)
   └── Write or refresh `project_structure.md` in the project root with the findings.
```

---

## Step-by-Step Execution Guide

### Step 1: Workspace Hierarchy Scan
- Inspect top-level folders using directory listing tools.
- Identify the project's root naming pattern and high-level categorization (e.g., assets, documentation, production, experiments).

### Step 2: Narrative & Script Discovery
- Search for `.txt`, `.md`, `.doc`, or `.pdf` files containing scripts, dialogue, scene treatments, and world bibles.
- Determine the canonical source of truth for narrative pacing and dialogue.
- Document the narrative division hierarchy (e.g., `Story Bible/Stories/<Story>/...` or `Scripts/<Episode>/...`).

### Step 3: Visual Artwork & Source Asset Mapping
- Search for completed pages and production art files.
- Determine whether pages are stored flattened (`.png`, `.jpg`) or layered (`.psd`, `.clip`, `.kra`).
- Identify if panel cutouts or isolated elements are already organized in subfolders (e.g., `panel images/`, `crops/`).
- Document page and panel numbering schemes (e.g., `Page_01`, `01_panel_02.png`).

### Step 4: Character Turnarounds, Palettes & Reference Anchors
- Locate reference images used for model consistency.
- Identify:
  - Canonical character turnaround sheets (front, 3/4, side, back).
  - Costume variations and age states.
  - Official color palettes and hex/RGB swatches.
  - Prop and technology design sheets.

### Step 5: Animation Output & Staging Conventions
- Determine where scene-level animation assets must be created and stored.
- Establish the folder structure for each animated sequence:
  - Master scene directory: e.g., `<scene_path>/Anime/` or `<project_output>/<scene_name>/`
  - Master reference bus: e.g., `master_subjects.txt`
  - Shot lists: e.g., `<scene>_shot_list.md`
  - Set plates: e.g., `sets/set_XX_<name>.jpg`
  - Overview maps: e.g., `sets/scene_<num>_<name>_overview_map.png`
  - Generation prompts: e.g., `prompt_<index>_<shots>_<name>.txt`
  - Rendered footage: e.g., `renders/`, `clips/`

### Step 6: Compilation of `project_structure.md`
- Save the structured notes file in the workspace root:
  `project_structure.md`
- Use the standardized schema detailed below.

---

## Standardized `project_structure.md` Schema

The compiled notes file must adhere to this standardized markdown structure:

```markdown
# Project Structure Notes: [Project Name]

*Last Analyzed: [YYYY-MM-DD]*  
*Analyzed By: project-structure-analyzer*

---

## 1. Project Overview & Scope
- **Project Title**: [Title of the comic / animated series / film]
- **Narrative Scope**: [Brief 1-2 sentence summary of story and world]
- **Current Production Focus**: [Active chapter, scene, or sequence being developed]
- **Narrative Hierarchy**: [e.g., Series > Volume > Chapter > Scene > Page > Panel]

---

## 2. Directory & Path Mapping Table

| Asset Role | Resolved Path in Workspace | Description & File Types |
| :--- | :--- | :--- |
| **Narrative Scripts & Stories** | `[path/to/scripts]` | Canonical narrative scripts (.txt, .md) |
| **Lore Bibles & World Docs** | `[path/to/lore]` | World rules, locations, magic systems |
| **Finished Comic Pages** | `[path/to/pages]` | Final flattened and lettered pages (.png, .jpg) |
| **Layered Art Sources** | `[path/to/layers]` | Pencils, inks, flats, colors (.psd, .clip) |
| **Isolated Panel Cuts** | `[path/to/panels]` | High-res panel crops for video conditioning |
| **Character Model Sheets** | `[path/to/characters]` | Turnarounds, facial expressions, model anchors |
| **Color Palettes & Swatches** | `[path/to/palettes]` | Official swatch files, reference color cards |
| **Scene Animation Hubs** | `[path/to/scene_hubs]` | Scene-level production staging folders |
| **AI Workflows & Experiments** | `[path/to/workflows]` | ComfyUI graphs, test scripts, local runs |

---

## 3. Naming & Numbering Conventions

- **Pages & Panels**: [e.g., `01 - Scene Name/Page 01.png`, `01_panel_03.png`]
- **Shots & Prompts**: [e.g., `SH-01` through `SH-NN`, `prompt_01_sh01_sh02_<slug>.txt`]
- **Master Reference Slots**: [e.g., `<Picture 1..9>`, `<Audio 1..N>`]
- **Sets & Environments**: [e.g., `set_01_<slug>.jpg`, `scene_00_<slug>_overview_map.png`]

---

## 4. Scene-Level Animation Staging Rules

For each animated scene in this project:
1. **Scene Hub Location**: `[Exact convention, e.g. <Scene_Folder>/Anime/]`
2. **Master Subject Bus**: Store global reference definitions in `master_subjects.txt` inside the scene hub.
3. **Set Plates Folder**: Store background plates in `sets/` under the scene hub.
4. **Prompt Files**: Store individual generation prompt files directly inside the scene hub.
5. **Directorial Reviews**: Store directorial review scorecards (`<scene>_directorial_review.md`) inside the scene hub.

---

## 5. Active Target Models & Engine Environments

- **Primary Video Generator**: [e.g., MiniMax Hailuo H3 (ref2vid), Wan 2.1, Hunyuan Video, CogVideoX]
- **Workflow Orchestration**: [e.g., ComfyUI local node tree, cloud API, batch scripts]
- **Image Synthesis Engine**: [e.g., SDXL, Flux, Midjourney, generate_image tool]
- **Audio & Foley Pipeline**: [e.g., ElevenLabs, native prompt soundscapes, DAW assembly]

---

## 6. Active Production Inventory & Status

| Scene / Sequence | Scene Hub Path | Status | Key Artifacts Present |
| :--- | :--- | :---: | :--- |
| **[Scene 00 / Prologue]** | `[path]` | [Ready/In Progress] | [Shot list, sets, prompts, reviews] |
```

---

## Integration with Downstream Skills

Downstream skills should consume `project_structure.md` as follows:
- `comic-to-animation`: Reads the directory map to locate source panels and character model anchors without asking the user for paths.
- `comic-shot-breakdown`: Writes shot lists to the designated scene hub path recorded in Section 4.
- `cinematic-set-reference`: Saves set plates and overview maps to the scene hub's `sets/` folder.
- `minimax-h3-prompt-craft`: Saves prompt files to the scene hub and adheres to the naming conventions in Section 3.
- `cinematic-director-review`: Locates review targets in the scene hub and validates compliance against project naming and asset standards.
