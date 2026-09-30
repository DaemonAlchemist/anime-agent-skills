---
name: minimax-h3-prompt-craft
description: Formats, structures, and optimizes Minimax Hailuo (H3) full-reference mode (ref2vid) video prompts following the official MiniMax-H3 specification, including subject definitions, retention analysis, detailed shot descriptions, and audio layers.
---

# Minimax H3 Full-Reference Mode Prompt Craft

This skill provides the comprehensive specification and authoring standards for Minimax Hailuo (H3) full-reference mode (ref2vid) video prompts, based on the official [MiniMax-H3 Prompt Writing Guide](https://github.com/MiniMax-AI/MiniMax-H3).

## Core Structure Overview

A complete H3 full-reference rewrite consists of exactly six sections in the following strict order:

| Section | Purpose |
| :--- | :--- |
| `subject_definitions` | Defines referenced entities, visual assets, frame anchors, and audio signals |
| `summary` | Concise 1-paragraph summary with square-bracketed task type prefix |
| `retention_analysis` | Explicit tracking of how each reference is preserved or transferred |
| `detailed_description` | Shot-by-shot visual, camera, action, dialogue, and sound descriptions in playback order |
| `overall_soundscape` | Continuous diegetic ambient sound and physical Foley |
| `non_diegetic_music` | Score audible only to the audience (or `N/A`) |

---

## 1. Reference Labels & Definitions (`subject_definitions`)

Four standardized label types identify referenced content:

- **`<Subject N>`**: Reusable visible content (characters, environments/sets, props, clothing, visual styles, or poses).
  - *Example*: `<Subject 1> is the young woman in <Picture 1>, with long dark hair, a blue cardigan, and a thin silver necklace.`
  - If a subject comes from multiple assets, state what each provides (e.g., appearance from `<Picture 1>` and motion from `<Video 1>`).
  - *Environment Layout Reference Pattern*: When an unbroken flythrough or layout video (e.g. `<Video 1>`) establishes the macro spatial geography and set placements, define it as: `<Subject N> is the overall environment layout in <Video 1>, the ground-level flythrough video establishing the spatial continuity, terrain topography, and camera trajectory across [landmarks].` In `retention_analysis`, track it as `weak_reference` preserving the spatial transitions and geography.
- **`<Picture N>`**: Used standalone *only* when the image serves as a concrete frame anchor (first frame, keyframe, last frame) or storyboard/shot-planning reference.
  - *Example*: `<Picture 2> is the first frame of [Shot 1], showing a woman seated beside a café window.`
  - *Rule*: If an image only defines a subject/environment without anchoring a specific frame, cite it inside `<Subject N>` instead of creating a standalone picture entry.
- **`<Video N>`**: Reserved for whole-video relationships (source video being edited, continued, or providing temporal/camera structure).
- **`<Audio N>`**: Standalone audio asset or synchronized audio track from a video.
  - When bound to a speaker, reuse their global speaker ID: `<Audio 1> is the voice-timbre reference for <Subject 1> (S1).`

---

## 2. Summary & Task Types (`summary`)

The summary begins with a square-bracketed task type prefix, followed by a single English paragraph summarizing the scene and reference relationships:

```text
[reference generation] The target video shows...
[video editing + reference generation + audio reuse] The target video is an edited version of <Video 1>...
```

### Valid Task Types (combined with ` + `):
- `keyframe completion`: An image serves as first/last frame or concrete frame anchor.
- `reference generation`: Image/video/audio provides guidance for character, scene, style, action, or camera without serving as a fixed frame anchor.
- `video editing`: Source video is directly modified.
- `video continuation`: New video continues or extends from an existing video.
- `audio reuse`: Audio signal is copied 1:1 in full or part.
- `audio reference`: Audio signal is referenced for timbre, music style, dialogue, or rhythm without copying the raw waveform.

---

## 3. Retention Analysis (`retention_analysis`)

Every reference label defined in `subject_definitions` must have an entry detailing its preservation status:

### Visible Content Markers (`<Subject N>`, `<Picture N>`, `<Video N>`):
- `fully_preserved`: The defined role of referenced content is fully preserved.
- `partially_preserved`: Used, but some defined characteristics are modified or partially omitted.
- `attribute_transfer`: Referenced characteristics transferred to another identifiable subject.
- `weak_reference`: Only broad similarity in atmosphere, style, or category is maintained.

*Format*:
```text
<Subject 1> (appears in [Shot 1], [Shot 2]): fully_preserved - [Explicit visual anchors retained].
<Picture 2> ([Shot 1] first frame): fully_preserved - [Composition retained].
```
> [!TIP]
> **Unified Reference Bus & Master Subjects Protocol**:
> 1. **Master Reference Bus File (`master_subjects.txt`)**: Store all global scene assets, picture/video reference slot mappings (`<Picture 1..9>`, `<Video 1>`), global subject IDs (`<Subject 1..N>`), and a Prompt Reference Bus Usage Matrix in `master_subjects.txt` inside the scene's designated animation directory.
> 2. **Global Numbering Consistency**: Never re-index subjects per prompt (e.g. do not renumber Subject 6 to Subject 1). All prompts must maintain the identical global `<Subject N>` and `<Picture N>` identifiers established in `master_subjects.txt`.
> 3. **Per-Prompt Subject Filtering**: In individual prompt files, include in **both** `subject_definitions:` and `retention_analysis:` **only the subjects actively appearing or utilized in that specific prompt**. Omit all unused subjects to eliminate token bloat and prevent model attention bleed across unreferenced assets.

### Audio Markers (`<Audio N>`):
- `fully_copy`: Raw audio signal reused 1:1 as complete target audio.
- `partially_copy`: Audio timeline/layers partially copied, or elements mixed.
- `reference`: Audio timbre, rhythm, or delivery referenced without copying raw signal.
- `weak_reference`: Broad atmospheric similarity.

*Format*:
```text
<Audio 1>: reference - vocal timbre guides the delivery of <Subject 1> (S1) without copying signal.
```

---

## 4. Detailed Description (`detailed_description`)

The main body of the prompt (typically 350–500 English words for generation tasks):

### Critical Formatting Rules:
1. **Style Opening Sentence**: Established in 1–2 English sentences *before* `[Shot 1]`.
   - *Example*: `The target video is in a cinematic, 2D anime fantasy action style with high-contrast twilight lighting.`
2. **Shot Headers & Timestamps**:
   - `[Shot 1]` marks the opening shot (**never has a timestamp**).
   - Subsequent shots specify exact cut timestamps: `[Shot N] At MM:SS.mmm, the shot cuts to...`
3. **Reference Injection**:
   - Insert `<Subject N>`, `<Picture N>`, `<Video N>`, and `<Audio N>` at their first clear appearance and where active.
   - Describe current composition, subject position, camera motion, and action clearly.
4. **Speaker IDs & Dialogue**:
   - Assign global speaker IDs in order of first vocalization: `(S1)`, `(S2)`.
   - When a referenced subject speaks: `<Subject N> (Sx)`.
   - Enclose dialogue in `<d>[Language] Text.</d>`. Complete sentences must end with proper punctuation (`.`, `?`, `!`) before `</d>`.
   - Use `<scenetrans>` for dialogue continuing across a cut, and `<cutoff>` for dialogue truncated by video end.
5. **Continuous Single-Take Prompts (No Cuts / Oners)**:
   - For unbroken flythroughs or single-take sequences, **omit all subsequent `[Shot N]` cut headers**.
   - Encapsulate the entire video movement within a single `[Shot 1]` block.
   - Explicitly specify continuous spatial camera transitions (e.g., *"glides forward...", "banks smoothly around...", "transitioning without a cut directly into...", "decelerating smoothly to a resting stop..."*).
   - In `retention_analysis`, list all active subjects as `(appears in [Shot 1])`.

---

## 5. Soundscape & Music

- **`overall_soundscape`**: Continuous diegetic background audio and physical Foley (wind, fire roar, rain, footfalls, wood groans). Do not repeat dialogue or music here. If audio is copied/referenced, state: `The copied ambience layer from <Audio 1> continues throughout...`
- **`non_diegetic_music`**: Score audible only to the audience. Describe genre, instrumentation, tempo, and dynamic progression. If no music, write `N/A`.

---

## Complete Standard Template

```text
subject_definitions:
<Subject 1> is the [character/environment/object] in <Picture 1>, with [detailed visual features].
<Subject 2> is the [character/environment/object] in <Picture 2>, with [detailed visual features].
<Picture 3> is the [first frame / storyboard reference] of [Shot 1], showing [composition].
<Audio 1> is the voice-timbre reference for <Subject 1> (S1).

summary:
[reference generation + audio reference] The target video shows [narrative summary of action, camera moves, and reference roles].

retention_analysis:
<Subject 1> (appears in [Shot 1], [Shot 2]): fully_preserved - [retained features].
<Subject 2> (appears in [Shot 2]): fully_preserved - [retained features].
<Picture 3> ([Shot 1] first frame): fully_preserved - [retained framing].
<Audio 1>: reference - [retained vocal traits].

detailed_description:
The target video uses a [cinematic visual style, lighting, and palette].
[Shot 1] [Framing and camera movement establishing <Subject 1>]. [Action, lighting, sound effects]. <Subject 1> (S1) says, <d>[English] Spoken line here.</d>
[Shot 2] At 00:03.500, the shot cuts to [framing and camera movement showing <Subject 2>]. [Action, motion, physical impact].

overall_soundscape:
[Continuous diegetic background ambience and Foley sounds].

non_diegetic_music:
[Score instrumentation, tempo, emotional tone, or N/A].
```

## Storage Location
All prompt files for an animated scene must be saved inside that scene's designated animation directory as identified in the project structure notes:  
`<scene_output_dir>/prompt_<index>_<name>.txt`
