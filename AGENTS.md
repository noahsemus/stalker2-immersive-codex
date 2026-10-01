# ImmersiveCodex — mod context for the agent

**First read `harness/AGENTS.md`**: the shared rules, tester workflow, pipeline and game knowledge for every
Stalker 2 mod. They apply here. This file holds only what is specific to this mod.

Purpose: A Codex tab in Skif's PDA: a first-person diary entry, in Skif's own voice, for every character he meets.

Repo `noahsemus/stalker2-immersive-codex`, Zone Kit plugin `ImmersiveCodex` (`/ImmersiveCodex/`), asset prefix `ImmCodex`. Created from the
harness on 2026-10-01.

## Current state (one line per checkpoint / release: date, what changed, what the tester confirmed in game)
- 2026-10-01: repo created to record the idea; **not started** (Noah: "codify the idea for later"). Created with
  `new_mod.ps1 -NoKit`, so there is no Zone Kit plugin yet. The idea, open questions and research leads are in
  `PLAN.md`. When Noah says to start: answer the PLAN.md questions with him, do the kit research, then create the
  plugin (`CreatePlainMod.bat ImmersiveCodex`, uplugin fields as in `harness/tools/new_mod.ps1`) and have him pick it
  in the toolbar mod selector.

## Key facts (verified; cite file:line in the kit)
- _(fill in as research lands)_

## Assets this mod may override
- _(none yet; see harness/docs/compatibility.md before adding any)_

## Files
- `PLAN.md` plan and test matrix · `BUILD.md` every edit asset by asset · `zonekit/README.md` engineering log
  (what each test showed, dead ends) · `zonekit/ImmersiveCodex/` plugin mirror · `zonekit/tools/` mod-specific generators
  and classifier lists · `zonekit/builds/` checkpoint and release paks · `mod.json` names and pak suffixes.
- `CLAUDE.md` / `GEMINI.md` only import `harness/AGENTS.md` and this file, for tools that don't read `AGENTS.md`.

## Release (only when the tester says "cut a release")
Follow `harness/docs/pipeline.md` § Release. Nexus page: _(record the mod id here once it exists)_.
