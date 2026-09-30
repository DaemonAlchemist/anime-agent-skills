---
name: cinematic-director-review
description: Evaluates animation assets, shot lists, set references, prompts, and generated footage against an exacting, multi-dimensional directorial quality rubric with actionable improvement recommendations.
---

# Cinematic Director Review Skill

This skill embodies the role of a **Cinematic Movie Director** and **Executive Animation Supervisor**. It provides a rigorous, standardized quality evaluation rubric across all phases of the webcomic-to-animation adaptation pipeline: shot lists, set concept art, prompt engineering, and generated video sequences.

Whenever evaluating existing content or creating new production assets, this skill must be invoked to ensure visual excellence, narrative punch, spatial continuity, and technical feasibility for AI video generation.

---

## Directorial Philosophy

A cinematic adaptation is not an automated slideshow of comic panels; it is a dramatic motion picture.
1. **Dramatic Subtext Drives Every Frame**: Every camera push, angle, and lighting shift must amplify the emotional stakes and character motivations established in the narrative script and project lore bible.
2. **Spatial Integrity is Sacred**: Viewers must never feel disoriented by arbitrary cuts or contradictory set geography. Master set references and overview maps are the film's physical soundstage.
3. **No Compromise on Cinematic Grammar**: Camera movements must serve a purpose (e.g., crane drift to isolate vulnerability, Dutch angle to signal imminent dread, crash zoom for sudden shock).
4. **Ruthless Quality Gating**: No prompt or shot moves to render without passing the rubric. Flaws in pre-production compound exponentially during AI video generation.

---

## Directorial Quality Rubric

The evaluation rubric assesses four core pre-production and production pillars. Each category is scored on a scale of **1 to 10**, with specific criteria for each rating level.

```text
Overall Directorial Score = Average of Applicable Categories
- 9.0 - 10.0 : MASTER (Greenlit for Production Lock)
- 7.5 - 8.9  : PRODUCTION-READY (Minor Directorial Notes / Polish)
- 5.0 - 7.4  : REVISION REQUIRED (Directorial Retakes Needed Before Generation)
- Below 5.0  : REJECT / RESHOOT (Fundamental Flaws; Redo from Narrative Core)
```

---

### Rubric 1: Shot List & Cinematic Staging

| Score | Criteria & Directorial Standard |
| :--- | :--- |
| **9–10 (Master)** | **Flawless Narrative Pacing & Grammar**: Shot durations match emotional beats (fast 1.5–2.5s for frantic panic/attacks, deliberate 3.0–4.0s for eerie establishing/lingering dread). Camera choreography (angles, vectors, focal lengths) dynamically enhances tension. Spatial blocking strictly respects the 180° line and character vectors. Lore-critical beats (e.g., character weaknesses, tragic misconceptions) are visually emphasized. Transitions are purposeful (match cuts, whip pans, hard shock cuts). |
| **7–8 (Good)** | **Solid Cinematic Staging**: Clear camera angles, appropriate durations, coherent spatial blocking. Minor missed opportunities for dynamic camera movement or subtle emotional subtext. Transitions are functional but conventional. |
| **5–6 (Weak)** | **Comic Gutter Thinking**: Feels like static comic panels chopped into arbitrary video clips. Durations are mismatched with action complexity (e.g., complex choreography squeezed into 1.5s, or static faces lingering too long). Disjointed spatial progression across cuts. |
| **1–4 (Fail)** | **Spatial Chaos & Pacing Collapse**: 180° line violations, contradictory character positions, lack of camera direction, pacing that numbs emotional impact. |

**Key Review Questions**:
- Does the shot sequence honor the narrative script as primary authority while leveraging comic panels for style?
- Are camera movements motivated by subject action or psychological state?
- Is there a clear rhythm of tension building, breathers, and visceral climax?
- Are action vectors (direction of running, looking, striking) consistent across cuts?

---

### Rubric 2: Concept Images & Set References

| Score | Criteria & Directorial Standard |
| :--- | :--- |
| **9–10 (Master)** | **Immersive Worldbuilding & Flawless Spatial Alignment**: Minimalist webcomic backgrounds are elevated into rich, painterly, lived-in anime environments (weathered textures, chipping plaster, volumetric lighting, particulate smoke/embers). Every plate aligns 100% with the bird's-eye Scene Overview Map. Lighting direction, color temperature, and horizon heights remain strictly cohesive across reverse angles. Clean plates have zero unwanted character artifacts or perspective distortion. |
| **7–8 (Good)** | **Strong Atmospheric Fidelity**: High-quality painterly aesthetic with good texture and lighting. Minor spatial ambiguities between different sets or slight inconsistencies in ambient light bounce. |
| **5–6 (Weak)** | **Sparse or Disconnected Sets**: Backgrounds appear empty, sterile, or flatly lit. Significant discrepancies between exterior and interior views (e.g., doorway perspective doesn't match exterior establishing plate). |
| **1–4 (Fail)** | **Style Clashes & Geographic Incoherence**: Mismatched art styles (e.g., photo-real vs anime flat), contradictory architecture, missing key landmarks, unusable perspective distortion. |

**Key Review Questions**:
- Does the set plate look like a high-budget theatrical anime production background?
- Does looking out a doorway reveal the exact exterior set established earlier?
- Are environmental physics (wind direction, smoke drift, ember density) unified across sets?
- Is there a master layout map anchoring camera trajectories and set placements?

---

### Rubric 3: Prompt Craft & AI Video Feasibility

| Score | Criteria & Directorial Standard |
| :--- | :--- |
| **9–10 (Master)** | **Engine-Optimized Precision & Zero Hallucination Risk**: Adheres strictly to the generator's native specification (e.g., MiniMax-H3 6-section schema: `subject_definitions`, `summary`, `retention_analysis`, `detailed_description`, `overall_soundscape`, `non_diegetic_music`). Asset conditioning tags (`<Subject N>`, `<Picture N>`, `<Audio N>`) are correctly bound and preserved. Physical actions use concrete kinetic verbs; camera vectors are unambiguously defined. No ambiguous metaphors or buzzword spam. Word budget respects attention limits. |
| **7–8 (Good)** | **Compliant & Clear**: Complete required sections, correct reference labeling, clear physical descriptions. Minor wordiness or slight redundancy between sections. Feasible motion trajectories with low morphing risk. |
| **5–6 (Weak)** | **Vague or Over-Dense**: Contains ambiguous descriptors that confuse diffusion models (e.g., "she feels an ocean of sorrow"). Over-crammed simultaneous actions causing morphing risks. Mismatched retention analysis markers. |
| **1–4 (Fail)** | **Broken Syntax & Infeasible Prompts**: Missing mandatory sections, invalid tag syntax, impossible simultaneous camera acrobatics, high likelihood of nightmare anatomy or melted frames. |

**Key Review Questions**:
- Are character and environmental anchors explicitly defined and tracked in `retention_analysis`?
- For continuous flythroughs or oners, are spatial transitions seamless without cut tags?
- For multi-shot sequences, are cut timestamps (`[Shot N] At MM:SS.mmm`) mathematically accurate?
- Are diegetic Foley and non-diegetic music layered with proper acoustic separation?

---

### Rubric 4: Character Fidelity & Performance (Video & Concept)

| Score | Criteria & Directorial Standard |
| :--- | :--- |
| **9–10 (Master)** | **Authentic Character Life & Flawless Consistency**: Character designs, silhouettes, costumes, and color palettes faithfully match the project lore bible and reference turnarounds. Micro-acting (pupil dilation, quivering lip, tensed jaw, ragged breathing) brings emotional weight. Kinetic physics (weight, inertia, footing, hair/cloth dynamics in wind) feel physically grounded. Zero identity drift or anatomical distortion. |
| **7–8 (Good)** | **Solid Performance & Resemblance**: Recognizable character likeness, consistent costume, believable motion. Minor stiffness in micro-expressions or slight secondary animation smoothing needed. |
| **5–6 (Weak)** | **Noticeable Drift & Uncanny Valley**: Facial features drift between shots, clothing colors fluctuate, or movement exhibits "floaty" weightlessness and unnatural limb bending. |
| **1–4 (Fail)** | **Character Collapse**: Severe anatomy meltdown (extra limbs, melting fingers), radical identity changes, emotion completely detached from the dramatic situation. |

**Key Review Questions**:
- Does the character's physical size, stature, and proportions match their canonical age and model sheet (e.g., child scale relative to adult doorframes or furniture)?
- Does the acting convey the true subtext (e.g., naive, false courage masking raw terror)?
- Are costume details (boots, tunics, headbands, weapon props) consistent from shot to shot?

---

## Standard Directorial Review Report Template

When conducting a directorial review on any scene artifact, format the evaluation as follows:

```markdown
# Director's Cut Review: [Scene Name / Asset Name]

**Director's Assessment Verdict**: [MASTER / PRODUCTION-READY / REVISION REQUIRED / REJECT]  
**Overall Directorial Score**: [X.X / 10]  
**Reviewed Artifacts**:
- [Artifact 1 Name](file:///path/to/artifact1)
- [Artifact 2 Name](file:///path/to/artifact2)

---

## 1. Executive Directorial Summary
[A concise 2-3 paragraph director's statement analyzing the scene's emotional trajectory, cinematic strengths, narrative resonance, and overarching vision.]

---

## 2. Detailed Rubric Scorecard

| Directorial Pillar | Score | Directorial Analysis & Findings |
| :--- | :---: | :--- |
| **1. Shot List & Staging** | [X]/10 | [Evaluation of pacing, camera vectors, transitions, and dramatic subtext] |
| **2. Concept & Set References** | [X]/10 | [Evaluation of environmental depth, spatial coherence, and lighting continuity] |
| **3. Prompt Craft & Feasibility**| [X]/10 | [Evaluation of prompt syntax, reference binding, kinetic verbs, and model safety] |
| **4. Character & Performance** | [X]/10 | [Evaluation of model consistency, emotional acting, and physical weight] |

---

## 3. Critical Directorial Notes & Script Discrepancies
- **[Note 1 Headline]**: [Deep-dive into specific narrative, spatial, or physical incongruities (e.g. script lore vs shot blocking).]
- **[Note 2 Headline]**: [Specific technical or visual deficiencies that risk generation failure.]

---

## 4. Prescriptive Action Directives (The "Fix-It" List)
1. **Priority 1 (Mandatory Polish)**: [Immediate correction required before progressing.]
2. **Priority 2 (Asset Generation)**: [Missing set plates, character turnarounds, or sound layers to create.]
3. **Priority 3 (Prompt Optimization)**: [Refinements to generation prompts to maximize model yield.]
```

---

## Ongoing Integration Workflow

To ensure quality across all tasks:
1. **Pre-Flight Critique**: Before any prompt file or set reference is marked complete, evaluate it against the Director's Rubric.
2. **Post-Generation Review**: Evaluate rendered video clips against Character Fidelity and Directorial Staging before assembling into final scene edits.
3. **Living Skill Maintenance**: Continuously update this rubric and adjacent production skills as new AI models, prompt techniques, and rendering workflows are introduced.
