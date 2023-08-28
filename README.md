# Baldurs Gate 3 - Progressions Compatibility Patches

A character progressions file compatibility fixes across mods. The aim is for each patch to ship compatibility changes per mod and omit all other changes. Files changed should only be related to Progressions/progressions.lsx file and this mod will most likely need to be loaded __LAST__ or below the related mods..

Noting that there could be more mods that may be inconflict and loading this patch file last will be the safest way to confirm things are working as expected between the patch target mods.

## About

These patches are for [Baldurs Gate 3](https://baldursgate3.game/) mods. Go to https://www.nexusmods.com/baldursgate3/mods/ to see all the available mods.

The built patches are hosted here [nexusmods.com - progressions compatibility patches
](https://www.nexusmods.com/baldursgate3/mods/1572)

## Supported Patches

- FeatsEvery2Levels + Sorcerer2xSpells

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

### Getting Started

1. This is a PC tutorial...there's probably a linux option somewhere if needed. Google it an add a link to this README.md if you find one.
2. Download the latest exporttool Baldurs Gate 3 pak tool. It uses LZ4 or zlib to create .pak files. Go to this repo [Norbyte/lslib/releases](https://github.com/Norbyte/lslib/releases)
3. In the exporttool download folder Launch ConverterApp.exe
4. Click on the tab for PAK/LSV tools and make sure you are on Baldur's Gate 3 (64 Bit) for Game (above the tabs).
6. Extract the mods that are conflicting by providing the path or using the explorer.
7. Open the conflicting file in VSCode. https://code.visualstudio.com/ if you do not have VSCode download it.
8. Reference the other mod's `Progressions/Progressions.lsx` file. FYI Theses files are XML, and the overwrite procedure looks like anything with a conflicting level will overwrite all values inside it. IE it will not merge the values but directly overwrite. Your patch will need to combine any level reference that contains different data and export only those values
9. Once you created a patch for the Progressions.lsx file, you will want to create a new mod patch.


### New Mod Patches

#### Requirements
- Folder name should be `PCP_<Mod1>_<Mod2>_<Mod3>`
- Each patch should contain a `Mods/ProgressionsCompatibilityPatch/meta.lsx` and a `Public/ProgressionsCompatibilityPatch/Progressions.lsx`
- Under meta.lsx please make sure to add the related mods as dependencies, not doing so will make it hard to track down the specific mod that this patch targets.
   - the dependencies should be only the mods related to this patch.
- Make sure the meta is separate UUID, it's possible a few patches will be used together and listed as compatible.
- Meta UUID format should be `ed539163-bb70-prog-patc-<12 alphanumeric name of mods being patched for>`
- Archives and .pak is a manual process for now. It should be automated on a github pipeline

#### Steps

1. Point the ConverterApp.exe PAK/LSV Tool path to the new mod. Example we hava two mods named 2xSpells and 2xFeats
2. The folder would be `<BASE_PATH>/PCP_2xSpells_2xFeats`
3. The output then should also match the folder name, just add a .pak at the end IE `<BASE_PATH>/PCP_2xSpells_2xFeats.pak`
4. To test this .pak you can now install it directly with vortex and select "Create new mod folder with this pak". It should be a pop-up.
5. If this works congrats!
6. HELP OTHERS OUT - submit a pull request with your changes and I'll publish it.

### Future Features / Plans

1. Automate pak and archive file creation
    - Add a installer for LZ4 and compress the files to a .pak format
    - Add a zip archiver for that .pak file.
2. Add a compatibility tester tool, that iterates through .lsx and detects duplicate child keys and flags them as potentially incompatible.
    - add a way to parse all the injected .pak files from the mods folder and run the extractor on the pak files to detect overrides and conflicts in xml keys.
    - Needs to support windows...but linux would be much easier to write it in.
