# Tactics (Godot turn-based tactics game) — project notes

Last updated: 2026-10-18. Side project; Pete finds it "quite fun" to play.
Repo: https://gitea.bacon-forge.com:8443/pete/tactics (branch main), local
`/Users/pete/code/games/tactics`. Godot 4.7, GDScript, Lua scenarios.
Reference sources: XCOM 2 (ideas only), Battle for Wesnoth
(`/Users/pete/code/games/wesnoth`). Old prototype code is archived in the repo's
`refactor/` folder; assets were kept.

## Why it exists
Earlier attempts failed because the engine got muddied by quick fixes. This one
is a deliberate pure architecture: one owner per responsibility.

## Architecture (dependencies point inward)
- `sim/` pure simulation, no nodes: Command -> `Game.apply` -> events. Seeded
  RNG, replays are deterministic. Terrain levels, ramps, ladders (cost 2/level),
  3D line of sight, directional cover, props (doors, crates, chests), weapons
  and effects (heal, give weapon).
- `scenario/` + `scenarios/*.lua` data-driven maps (`highground.lua` is the
  default). Lua declares levels, units, weapons, prop types, rules.
- `ai/` team AI driver (team 1). Chests are not opened by the AI yet.
- `view/` Godot scenes only replay events. Catalogs map id -> scene
  (Unit, Prop, Weapon). Components talk by signals wired in scenes.
- Fail-fast `problems()` validation at match start; no runtime fallbacks.

## Rules Pete set (keep following these)
- Nodes, cameras, HUD, materials live in `.tscn` with `%UniqueName`; no
  `Node.new()` for things that are in the finished game.
- Root `Match` only wires. One owner per responsibility.
- Left click selects/moves. Right click acts (attack, open, shoot a prop);
  Shift picks the alternative verb.
- Hit/hurt boxes never carry damage. The sim decides, the view replays.
- Tests must not fake input: push real viewport events, and list anything
  unverifiable as `MANUAL:` (printed by `scripts/test.sh`).
- Check the exit status of `./scripts/test.sh` (not piped through head).

## Done so far
Sim, RNG/attack, AI, terrain height/ramps/ladders, hit chance + cover preview,
"out of range" messages, orbit/pan camera, real Synty props and characters,
chests (heal or give a weapon), weapons carried on rig bones (right and left
hand), weapon-driven attack animations, druid replaces the wizard, archers
start with bows (`Bow_Shoot`, bows held upright in the left hand).
Last commits: c05c9cae, d5e7f01f. All 7 suites green.

## Asset pipeline
Synty packs go through Blender (5.2) with `tools/import_synty_pack.py` and
`tools/blender_compat_shim.py`; see `docs/importing-synty-packs.md`. Pete's own
converter: `/Users/pete/code/games/synty-godot-converter`. It breaks on Blender
5.2 (`shadow_method` removed); the shim works around it and a fix in the
converter was offered but not answered.

## Next ideas (none started)
1. Arrow projectile flying to the target; hitbox contact timing.
2. AI opens chests.
3. Pull the bow string / use the pack's rigged bow animation.
4. Fix `shadow_method` in the converter repo.
5. Untrack `.DS_Store` files in the tactics repo.
6. Pete to check by hand (see the MANUAL list): real window clicks, feel and
   timing, editor view of hand-written scenes, how bows look in motion.
