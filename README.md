# Remnant Records Controller

An unofficial Windows/Steam mod for **Remnant Records**, with **F6 entity freeze** and a **PANICORE-style F5 item radar**.

**v0.2.0 is a first in-game test build.** Compilation and automated checks passed in the original build environment; gameplay, native Windows PowerShell 5.1, and the overlay still need verification on a player's PC.

## Download and install

Open [Releases](https://github.com/BoostedMage/Remnant-Records-Controller/releases) and download **Remnant_Records_Controller_v0.2.0.zip** from the v0.2.0 prerelease. This attached ZIP contains the installer, compiled mod, full source, build/test scripts, and bundled loader.

1. Close Remnant Records and extract the entire ZIP.
2. Run **INSTALL.bat**. Allow administrator access if needed to write to your Steam game folder.
3. Launch through Steam in **borderless or windowed mode** so the external radar remains visible.
4. Play solo or host a mission for the first test.

## Controls

| Key | Action |
| --- | --- |
| **F5** | Toggle radar on/off |
| **F6** | Freeze/resume the main entity |
| **Shift + Up** | Zoom out |
| **Shift + Down** | Zoom in |

Radar and freeze both start off.

## Radar

- Upper-right PANICORE radar layout, 620 x 690 at normal desktop sizes, with camera-heading rotation, directional arrows, altitude arrows, and spaced labels.
- Hollow **blue, red, and white circles** for mission value items, using the game's own item-value calculation and color gradient.
- **Solid red entities** labeled with their type and persistent network ID.
- A **blue snowflake** when freeze is actually applied; other living players are purple.
- Seven ranges from 15 to 250 meters; default 70 meters. Above/below arrows appear beyond 1.5 meters of vertical difference.

Equipment without a mission item value is excluded. Mirror and table items are labeled. Item colors are evaluated individually; the exorcism table can value duplicate item types differently when evaluating a complete offering.

## Freeze

Requires host authority, including solo hosted games. Targets both main entities in Double Ghost missions, but not summoned minions. Movement, animation, AI, and owned coroutines are paused while the rest of the game continues.

If a grab has already begun, freeze waits until it ends so a player is not left stuck in a capture. The marker remains red while pending. F6 cancels a pending freeze. Unfreeze before an exorcism phase that needs the entity to act. Freeze resets on map changes, controller shutdown, or loss of host authority.

## Compatibility and validation

Built against Steam app **1916310**, collected build **22908327**, Windows x64, Unity **2021.2.20f1 / Mono**. Includes BepInEx **5.4.23.3 x64**.

The packaged build record reports successful compilation and **61 automated checks** covering projection, protocol, installation, removal, rollback, and report ZIP handling. These checks do not establish in-game compatibility. See **Developer/BUILD_AND_VALIDATION.txt** inside the release ZIP for details and rebuilding instructions.

For a first test, enter a mission, check radar colors/heights and both zoom keys, then freeze and resume an entity before it grabs anyone. Run **COLLECT_REPORT.bat** if troubleshooting is needed. It creates a local report ZIP without uploading it; review logs before sharing them publicly.

## Uninstall

Close the game and run **UNINSTALL.bat**. It removes unchanged files this installer owns, preserves changed files, and keeps a shared loader when other plugins are installed. Original game assemblies and save files are not edited.

## Source and third-party components

The attached release ZIP includes **Source/**, **Developer/**, the radar renderer, installer scripts, third-party licenses, and UnityDoorstop's corresponding source. Rebuilding requires your own game's Managed assemblies and the .NET 8 SDK. Original game binaries and decompiled game source are not distributed.

The radar is adapted from PANICORE Host Controller v0.11.6.2. See **THIRD_PARTY_NOTICES.txt** and **Licenses/** inside the ZIP for BepInEx, Harmony, MonoMod, Mono.Cecil, UnityDoorstop, and radar attribution.

Release ZIP SHA-256:

```text
ea20ba29b6ecef7b9ece76daa569fb0c19b27a3dbb78c522eb8e76b2f869f717
```

Remnant Records and its assets belong to their respective owners. This mod is not affiliated with the game's developers.
