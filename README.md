# Baldurs Gate 3 - Progressions Compatibility Patches

A character progressions file compatibility fixes across mods. The aim is for each patch to ship compatibility changes per mod and omit all other changes. Files changed should only be related to Progressions/progressions.lsx file and this mod will most likely need to be loaded __LAST__ or below the related mods..

Noting that there could be more mods that may be inconflict and loading this patch file last will be the safest way to confirm things are working as expected between the patch target mods.

## About

These patches are for [Baldurs Gate 3](https://baldursgate3.game/) mods. Go to https://www.nexusmods.com/baldursgate3/mods/ to see all the available mods.

## Description

This is a simple collection of mods aimed towards fixing some cross mod compatibility issues.

Example: With feats every 2 levels + sorcerer 2x spells per level

feats per 2 levels overrides the level 2 6 10 of sorcerer
sorcerer 2x spells overrides every level. It does not contain a feat per level 2,6,10 so it breaks sorcerer compatibility with feats every 2 levels.

Solution:
Only update the incompatible items
Require the mods to be loaded before

This kind of pattern will happen with other mods that adjust Progressions/progressions.lsx. This mod will hopefully fix a few of these mods until mod authors directly decide to support external mod use cases.


## Contributing

### New Mod Patches

- Folder name should be `PCP_<Mod1>_<Mod2>_<Mod3>`
- Make sure the meta is separate UUID, it's possible a few patches will be used together and listed as compatible.
- Meta UUID format should be `ed539163-bb70-prog-patc-<12 alphanumeric name of mods being patched for>`
- Archives and .pak is a manual process for now. It should be automated on a github pipeline

### Future Features / Plans

1. Automate pak and archive file creation
    - Add a installer for LZ4 and compress the files to a .pak format
    - Add a zip archiver for that .pak file.
2. Add a compatibility tester tool, that iterates through .lsx and detects duplicate child keys and flags them as potentially incompatible.
    - add a way to parse all the injected .pak files from the mods folder and run the extractor on the pak files to detect overrides and conflicts in xml keys.
    - Needs to support windows...but linux would be much easier to write it in.
