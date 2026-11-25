# Vox Director — Agent Guide（豆包适配版）

This repository is an **agent skill**: a self-contained Vox-style paper-collage
workflow (script → collage keyframes → motion → voice-over → music → captions).
This edition preserves the original standalone pipeline and adds a minimal
Doubao Work Agent compatibility layer.

## Doubao Work Agent

1. Read **`SKILL.md`**, especially **“Doubao Work Agent adaptation”** at the top.
   (`SKILL.zh.md` contains the same workflow in Chinese.)
2. Load the applicable built-in host Skill before image generation, video
   generation or media processing. This repository supplies the Vox creative
   layer; current host rules control authorization, execution and delivery.
3. Default to Doubao's native image, video and audio generation; no Atlas key is
   needed. Run Atlas scripts only when the user explicitly selects that external
   backend for the current task. In that optional case, prefix every invocation
   with `VOX_DIRECTOR_DOUBAO=1` so automatic resubmission and A-roll model
   fallback stay disabled.
4. Always pass an absolute project directory under the user's main project. Do
   not rely on the scripts' default `out/` inside the installed Skill.
5. Route formal post-processing and all media delivery through the host. The
   local ffmpeg assembly scripts are for standalone use or an explicitly
   requested local preview, not a substitute formal-delivery path.

## Standalone agents

1. Read **`SKILL.md`** and the original workflow below the Doubao adaptation.
2. Before writing any prompt, read **`references/`** (prompt structures, the
   vocabulary/theme bank and the narrative-beat library).
3. Work one project at a time under `out/<project>/`, driven by a single
   `beats.json`. Run the stages in **`scripts/`** in order:
   `style_bakeoff.py → keyframes.py → clips.py → audio.py → assemble.py`.

## Standalone requirements

- `ATLASCLOUD_API_KEY` in the environment — https://www.atlascloud.ai/console/api-keys
- `ffmpeg` + `ffprobe` + `curl` on `PATH`
- Python 3 with `pillow`

Claude Code can auto-load this folder from `SKILL.md`'s frontmatter. Codex and
other agents can use this `AGENTS.md` as their entry point. Original project:
https://github.com/Alisa0808/vox-director
