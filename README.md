# Baldurs Gate 3 - Progress Compatibility Patches

A character progressions file compatibility fixes across mods. The aim is for each patch ship compatibility changes per mod and omit all other changes. Files changed should only be related to Progressions/progressions.lsx and this mod will most likely need to be loaded LAST.

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