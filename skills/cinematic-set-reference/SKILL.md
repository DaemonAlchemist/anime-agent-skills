---
name: cinematic-set-reference
description: Guides the design, enrichment, and spatial consistency of environment and set reference plates when adapting minimalist or sparse webcomic backgrounds into cinematic animation sets.
---

# Cinematic Set Reference Skill

This skill defines the methodology for transforming sparse, low-budget webcomic backgrounds into fully detailed, cinematic anime production sets while maintaining spatial consistency and architectural fidelity.

## Core Principles

### 1. Elevating Sparse Panels to Cinematic Art
Webcomic backgrounds are often simplified or minimalist due to production deadlines (e.g., flat single-color walls, simple geometric boxes, untextured roads).
When adapting to animation:
- **Rich Surface Textures**: Introduce realistic material rendering—weathered wood grain, stone masonry foundations, peeling or cracked clay plaster, iron nails, settled dust, and ash.
- **Volumetric Lighting & Atmosphere**: Add light shafts, warm fire glows, cool twilight bounce, airborne embers, and smoke plumes that establish mood and physical depth.
- **Set Dressing & Lived-in Details**: Add thematic props that serve the lore (e.g., tool-cluttered workbenches for weapon craft, overturned stools, broken pottery, scattered sketches).

### 2. Spatial Consistency & Set Mapping
Group the shots of a scene into a small number of **reusable master sets** (typically 3 to 5 per scene).
- **Shared Horizon & Geography**: Ensure background landmarks (like a burning village on the horizon, winding roads, or mountains) remain in consistent compass headings across wide and medium shots.
- **Light Continuity**: Maintain unified key light and ambient color temperatures across all angles (e.g., twilight blue from outdoors meeting warm orange firelight inside).
- **Reverse Angle Logic**: When looking from inside a doorway outward, the exterior view must match the exterior establishing wide shot.

## Set Reference Workflow

```text
1. Shot-to-Set Clustering
   └── Audit the shot list and group shots into master environment zones.

2. Architecture & Lore Grounding
   └── Pull reference panels from the comic and check project lore / style guides for world rules.

3. Detailed Plate Synthesis
   └── Prompt for empty background plates (16:9 widescreen, no characters)
   └── Specify cinematic anime background aesthetic (painterly, high dynamic range).

4. Bird's-Eye Scene Overview Map
   └── Synthesize a master 16:9 aerial layout plate showing the complete terrain topography.
   └── Peg the relative locations of all master sets (Set 01 through Set N).
   └── Trace character movement trajectories, action corridors, and camera vectors.
   └── Include inset preview cards of the master plates and architectural diagrams.
   └── Save as `scene_<num>_<name>_overview_map.png` in the scene's designated `sets/` folder.

5. Storage & Asset Naming
   └── Save all plates and maps directly into the scene's dedicated set folder:
       `<scene_output_dir>/sets/set_XX_<name>.jpg`
       `<scene_output_dir>/sets/scene_XX_<name>_overview_map.png`
```

## Sample Master Set Matrix Template

| Set ID | Set Name | Coverage | Key Spatial Anchors |
| :--- | :--- | :--- | :--- |
| **Set 01** | `set_01_<outdoor_corridor>.jpg` | SH-01, SH-02 | Low-angle path, dominant foliage/terrain, atmospheric particles, horizon lighting |
| **Set 02** | `set_02_<settlement_or_hazard>.jpg` | SH-03 – SH-06 | Architectural facades, structural obstacles, smoke/weather FX, key intersection |
| **Set 03** | `set_03_<structure_exterior>.jpg` | SH-07, SH-08 | Establishing wide angle, terrain path approach, building exterior, distant backdrop |
| **Set 04** | `set_04_<threshold_or_doorway>.jpg` | SH-09, SH-10 | Doorway threshold looking out; reverse-angle matching Set 03 exterior |
| **Set 05** | `set_05_<room_interior>.jpg` | SH-11 – SH-16 | Key furniture anchors, thematic props, wall textures, interior chiaroscuro lighting |
