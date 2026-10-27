# Baseline (Phase 1, partial — gate reached)

## What this repository is (verified from files)
- A **distribution of the closed-source game Street Legal Racing: Redline** (SL2 build 606, 7 Feb 2005, v2.2.1; per `diag.log`) plus mods. No engine source is in the repo.
- Engine: proprietary native Win32 x86 DirectX 9 binary (`StreetLegal_Redline.exe`, PE32 GUI, Intel 80386). Also `Slrr_GI.exe`, `StreetLegalDevKit.exe`, resource tools under `ResourceConverter/`.
- Language of the editable part: game scripts in a Java-like dialect (`*.java` under `src/`, `parts/**/src`, `sl/Scripts`, `system/Scripts`; 138 source files, 1692 compiled `.class`), plus `.cfg` (1182), `.scx` meshes, `.dds`/`.png` textures, `.rpk` resource packs (87).
- Build system: none. Scripts are compiled by the game/dev tools at load time; assets are packed with `RPK_Creator.exe`. No Makefile/CMake/CI.
- Launch: run `StreetLegal_Redline.exe` (or `Slrr_GI.exe`) on Windows. Graphics hooks: `d3d9.dll`, `dxgi.dll`, ENB/SweetFX/injFX, `enbshader.asi`, `lensflare.asi`.
- Remotes: only `origin` = antomys/SLRR-LE2MWM-MethanolFuel-Edition. No `upstream` remote is configured, so I cannot tell which is "fork" vs "upstream".

## Build / run on this machine: NOT POSSIBLE (UNVERIFIED)
- Linux sandbox; no Wine, no Windows, no GPU/DirectX. The engine cannot be built (no source) and not launched. Startup time, crash reproduction, memory and performance profiling: **unverified**.
- Tooling present: java/javac (not applicable to the game's script dialect).

## Evidence available in the repo (logs shipped from a prior run, dated 2020-09-26)
- `error.log`: 76 lines. 37x "Package conflict: multiple packages placed at the same location" (Nissan_Engine_Pack RB26 parts, Mitsubishi_4g63); 19x "syntax error" in `parts/engines/Toyota_2JZ_by_BB93/scripts/src/Toyota_2JZ_Block.java` lines 88–99.
- `res_ban.log`: resource-pack load list (97 KB).
- `diag.log`: build string above; "Exited." (no crash trace).
- README admits: Valo City hangs on load; too many RPKs crash the game.

## Mods (from README; load order not stored in repo — determined by RPK/folder scan inside the exe)
ExhaustiveBits/Slrr_GI, RevPhysicsAlpha + MrSir Running Gear/Suspension, CMS Brakes, Adjustable Fuel, Headlight control, Option Dialogue, Lisanity part-position scripts, MWM Resolution Changer, LE catalog menus, SweetFX/ENB, plus car/engine/map packs (Nissan_Engine_Pack, Toyota_2JZ_by_BB93, Mitsubishi_4g63, Drag_Track, Valo City, ...).
