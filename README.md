# Yo! Noid ROM hacks

Small patches for **Yo! Noid (USA)** on the NES, plus Game Genie codes that do most of the same thing on an unmodified cartridge.

## Patches

| Patch | What it does |
|---|---|
| `yo-noid-debug-menu` | Restores the hidden debug menu and makes its stage select work |
| `yo-noid-no-pizza` | Skips the pizza-eating contests |
| `yo-noid-debug-menu-no-pizza` | Both of the above |

Each patch is in [patches/](patches/) as `.ips` and `.bps`. Apply one of them to an unmodified ROM with [Floating IPS](https://www.romhacking.net/utilities/1040/) or any other patcher. Do not stack them; use the combined patch if you want both.

- **`.ips`** works with any copy of the ROM.
- **`.bps`** checks the ROM first and expects a clean iNES header (file CRC32 `3D6260D2`). If your patcher says the ROM is wrong, use the `.ips`.

To check you have the right game, the ROM data without its 16-byte header has CRC32 `50D141FC`. No ROMs are included in this repository.

## Debug menu

The game shipped with a developer menu that the title screen skips. With the patch, press **Start** on the title screen to open it.

| Button | Effect |
|---|---|
| A / B | Raise / lower the stage number (0–15) |
| Up / Down | Turn invincibility on / off |
| Start | Begin the game |

- Stage `00` is a normal start, `01`–`14` start on that stage, and `15` goes to the ending.
- The two text labels in the menu are garbled. One means normal and the other means invincible.
- Pausing the game turns invincibility off from your next life onward.

The stage select was removed by the developers before release, so the patch adds a few bytes of new code to bring it back.

## No pizza contests

Stages 1, 3, 5, 11, 13 and 14 normally end in a pizza-eating contest. With the patch, reaching the end of those stages clears the stage straight away, the same as the stages that have no contest. Finishing stage 14 goes to the ending.

## Game Genie codes

| Effect | Codes |
|---|---|
| Debug menu | `SZUIUZVT` |
| No pizza contests | `NUNLKUPA` + `SUNLSUKU` |

- The debug menu code opens the menu and gives you the invincibility toggle, but **the stage number does nothing**. A working stage select needs the patch.
- The no-pizza effect needs both codes entered together.
