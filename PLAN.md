# ImmersiveCodex — plan (idea brief, not started)

**Status 2026-10-01: idea parked for later at Noah's request. Nothing is researched or built yet.** Everything under
"Leads" is a hypothesis to verify in the Zone Kit first (`harness/docs/zonekit.md`), not a fact.

## The idea (Noah, 2026-10-01)
Skif's PDA gets a **Codex** tab that works like his diary. Whenever he meets a character, an entry for that character
is added. Each entry is written **in the first person, as Skif**: what he thinks of them, not an encyclopedia
article.

> *Example of the tone (draft, not canon-checked):* "Richter. Talks like every word costs him a coupon. Gave me work
> without asking my name, which tells me he doesn't expect me to live long enough to need one."

## What it should feel like
- An entry appears the first time Skif actually meets the character (first conversation, or the first story scene
  with them), never before, so nothing is spoiled.
- Skif's voice: terse, dry, a little tired, Zone slang where natural, no game-mechanics talk. He only knows what he
  has seen and heard so far.
- A small notification when an entry is added (like the game's own journal updates), optional.
- Works on an existing save: characters already met should get their entries too, if the game remembers who was met.

## Possible later extensions (not scope yet)
- Entries that grow: an extra paragraph after key story moments with that character (betrayal, rescue, death).
- Entries for factions and places, in the same voice.
- Other languages.

## Open questions for Noah (when we start)
1. Who counts: only named story / trader / quest characters, or every named stalker (much larger)?
2. One fixed entry per character, or entries that update with the story (spoiler handling)?
3. Codex as its own PDA tab, or inside the game's existing encyclopedia-style section if that turns out to be
   much less conflict-prone?
4. How long should entries be (two or three sentences vs a paragraph)?

## Leads to research first (unverified)
- **The game may already have an encyclopedia system**: `InfotopicPrototypes.cfg` exists in GameData. If infotopics
  are PDA entries that quests unlock, the codex could be pure data: new infotopic prototypes in
  `ModGameData/ImmersiveCodex/` plus a way to unlock them, with no UI override at all. Check what infotopics are,
  where the PDA shows them, and what unlocks them (quest nodes? `harness/docs/game-facts.md` lists
  `CppMediator.start_quest_node`).
- **Detecting "met"**: the first dialogue with a character (`PC.IsInStaticDialog` plus the interlocutor's identity),
  dialogue / quest node data in `DialogPrototypes`, `DialogChainPrototypes`, `QuestNodePrototypes`, or global
  variables the game already sets. A runtime host (`harness/docs/runtime-host.md`) can watch for it without overriding
  anything.
- **The PDA UI**: where its tabs are defined (`/Game/GameLite/FPS_Game/UIRemaster/...`, PDA widgets, data assets that
  list tabs). Adding a tab may mean overriding a PDA widget: a conflict risk with UI mods; prefer the infotopic route
  if it exists.
- **Character list and canon**: named NPC prototypes (`ObjPrototypes.cfg` and related, e.g. those with their own
  dialogue distances), their display names (localization tables) and the in-game dialogue text, so entries stay
  true to what Skif has seen. Entries are written ahead of time and shipped as data; nothing is generated at runtime.
- **Text storage and localization**: how the game stores localized strings for PDA text (string tables / cfg
  `Text = ...` keys), so entries can be English first and translatable later.

## When we start
1. Noah answers the open questions; the agent does the kit research above and rewrites this plan with evidence.
2. Noah restarts the Zone Kit editor; the agent creates the plugin (`CreatePlainMod.bat ImmersiveCodex`, see
   `harness/docs/pipeline.md` § 1; this repo was created with `-NoKit`), Noah picks it in the toolbar mod selector once.
3. Smallest proof first: one hard-coded entry for one early character appears in the PDA when you meet them.
4. Then the character list, the writing (Noah reviews the voice on a handful of entries before the rest), and the
   full test matrix (new game, existing save, every entry unlocks once, no spoilers, works with other UI mods).
