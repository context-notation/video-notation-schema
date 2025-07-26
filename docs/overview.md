## Core Fields and Typical Workflows

The Video Notation Schema mirrors a professional video production pipeline. Below is an overview of the key schema sections, their intended use, and practical guidance for integrating them into your workflow.

---

### 1. **Metadata (`metadata`)**

Establishes foundational information about the project.

**Key Fields:**

* `title`: Name of the project
* `duration_seconds`: Overall duration
* `video_type`: Format (e.g., `advertisement`, `short film`, `educational`)
* `aspect_ratio`, `frame_rate`, `resolution`: Technical specs
* `language`, `target_audience`, `keywords`: Contextual metadata
* `accessibility`: Includes captions, audio descriptions, flashing/motion warnings

**Tip:** Define early, as it governs the global frame for AI interpretation.

---

### 2. **Characters (`characters`)**

Defines consistent, reusable character profiles for appearance, voice, and behaviour.

**Key Fields (per character):**

* `character_id`, `name`, `appearance`, `wardrobe`
* `age_range`, `gender`, `ethnicity_descriptor`
* `personality_traits`, `vocal_description`, `accent`

**Overrides:** Scene-level details like `wardrobe_override`, `action_details`, or `behaviour` supplement or replace global character traits.

**Tip:** Define once, and reference throughout for consistent rendering.

---

### 3. **Global Elements**

Reusable definitions that simplify complex projects.

#### 3.1. **Props (`global_props`)**

Physical items used across scenes. Override with `prop_id_reference` in scenes.

#### 3.2. **Audio Elements (`global_audio_elements`)**

Reusable audio (ambient, sound effects, music loops). Reference with `audio_id_reference`.

#### 3.3. **Subjects (`global_subjects`)**

Non-character elements (e.g., animals, scenery). Referenced via `subject_id_reference`.

#### 3.4. **Motion Graphics (`global_motion_graphics`)**

Predefined motion graphics (e.g., `infographic`, `animated_logo`). Customise with overrides.

#### 3.5. **Lighting Presets (`global_lighting_presets`)**

Reusable lighting styles (e.g., `golden_hour_window`). Referenced with `preset_id_reference`.

#### 3.6. **Tone Presets (`global_tone_presets`)**

Reusable emotional tones (e.g., `calm_inviting_tone`). Also referenced via `preset_id_reference`.

---

### 4. **Global Style (`global_style`)**

Sets overarching artistic direction for the video.

**Key Subsections:**

* `shot`: Camera settings (angle, motion, focus, lens)
* `subject`: Styling for background or unnamed subjects
* `cinematography`: Lighting/tone (can reference presets)
* `audio`: Ambient, music, dialogue defaults
* `color_palette`: Defines visual tone (hex codes or themes)

**Tip:** Define after characters to unify visual/auditory tone across scenes.

---

### 5. **Scenes (`scenes`)**

Defines an ordered array of narrative or visual moments.

**Key Fields:**

* `scene_id`, `narrative_role`, `duration_seconds`
* `location`, `time_of_day`, `environment`
* `subjects`: Characters/objects present and their actions
* `visual_details`: Props, motion graphics, timing breakdowns
* `audio`: Dialogue, ambient overrides, sound effects
* `transition_to_next_scene`: Style and logic of scene cuts

**Overrides:** Use `shot_overrides`, `cinematography_overrides`, and scene-specific settings to adapt global styles.

**Tip:** Compose scene-by-scene using previous definitions as a base layer.

---

### 6. **Annotations (`annotations`)**

Enables human-readable production and post-production notes.

**Key Fields:**

* `direction_notes`: Director-style creative instructions
* `post_production`: VFX, editing, sound mixing
* `production_assets`: Linked image/audio references or concepts

**Tip:** Use for coordination across creative teams.

---

### AI Video Platforms

* The JSON can be use as prompt to any text-to-video AI model. 

---

## Schema Integration Tools

### Editors & Validators

* Visual Studio Code + JSON/YAML plugins
* Online JSON Schema Validators

### Libraries

* **Python**: `jsonschema`, `pydantic`
* **JavaScript/TypeScript**: `ajv`, `zod`, `joi`
* **Go**: `gojsonschema`

---

## Final Thoughts

The Video Notation Schema provides a structured, extensible way to craft AI video prompts with precision and reusability. From granular camera work to production notes, it enables creators to produce consistent, high-quality outputs at scale.
