# ReadMe For Arknights Custom Voices
<!-- File is formmated for markdown, I recommend VSCode (see resource section) -->
## Credit to KMission for the CustomVoices mod and everyone involved in the development of ModTek
#
## Table of Contents
1. [Resources](#resources-used)
1. [Overview](#overview)
1. [Installation](#modetek-installation)
1. [Dependencies](#mod-dependencies)
1. [Adding Custom Voices](#custom-voice-template)
    1. [Wwise Tutorial](#wwise-instructions)
    1. [Custom Voices Tutorial](#custom-voices-instructions)
# 
### Resources used
<!-- If you're reading this in VSCode press ctrl + shift + v for the MarkDown preview (formatted text) -->
* VSCode for easy json editing https://code.visualstudio.com/
* Arknights Data Source: https://aceship.github.io/AN-EN-Tags/
* KMission Custom Voice Tutorial https://www.youtube.com/watch?v=Q89cneezcAo
* Wwise for creating soundbanks https://www.audiokinetic.com/download/
* MusicBee for audio converting https://getmusicbee.com/

### Mod Dependencies
* CustomVoices mod https://github.com/BattletechModders/CustomBundle/tree/master/CustomVoices
* Commander Portrait Loader https://www.nexusmods.com/battletech/mods/84
* ModTek for Installation https://github.com/BattletechModders/ModTek/tree/master/ModTek
#

## Overview
Replaces the campaign start with custom pilots from Arknights, and sets the starting faction emblem as the Rhodes Island logo

Starting lance will be:
* Amiya
* Kroos
* Melantha

2 additional pilots to start
* Jessica
* Exusiai

Currently implemented additional pilots for hire
* Blemishine
* Flamebringer
* Gumi
* Hoshiguma
* Mostima
* Phantom
* Ptilopsis
* Rosa
* Rosmontis
* Schwarz
* Sesa
* SilverAsh
* Spot
* Swire
* W

***Kal'tsit portrait and voices are added but pilot is not configured (Can set up as commander unit)*

#
## ModTek Installation
The main ArknightsMod contains all the core modified files and depends on CustomVoices and CommanderPortraitLoader to function correctly

This mod is separated into the following folders 
* ArknightsMod 
    * core files for the mod to function
* CommanderPortraitLoader 
    * Copy into your mod directory to add Arknight operator custom portraits
* CustomVoices
    * Copy into your mod directory or manually add the files to the CustomVoices mod
        * The mod.json file is preset to work with this directory structure, but if you are already using CustomVoices you should be able to just drag in the appropriate soundbank and voicepack files

Optional additions
* DisablePilots
    * Removes ronin tags from default pilots and sets ronin spawn chance in story to 1, forcing only custom pilots with the ronin tag to appear in hiring
    * If you still want the backer/ronin pilots in the base game, delete the 'pilot' folder from the mod to only force ronin pilots to spawn (should get rid of the 3d generated pilots, if you don't see the change try jumping to another system)
#
## Adding Custom Voices
### Step by step text version for KMissions' custom voice tutorial
#
### Wwise Instructions
* Make sure to install the 2016 version of Wwise for Battletech compatibility
* Create a standard new project
* Right click Actor-Mixer Hierarchy and create a new child work unit (Your new character) 
    * (Might not matter if it is in Actor-Mixer or not)
* Right click new work unit and import audio files (wave files can be used)
    * Optional - add effects by selecting the audio file and using the effect tab
        * Use Wwise plugins to play around with different effects without a liscence
            * I used these three effects with some slight tweaks
                * Wwise parametric EQ Dual Filters Radio Comm (lowered peaking gain to 5, raised output gain to 5)
                * Wwise guitar distortion (added distortion - fuzz @25%, wet dry mix @60, output gain @5)
                * Wwise compressor dialog leveler hard (default)
        * Creating a shareset (left side viewer) can make it easier to apply the effect to everything in your project 
            * Highlight audio files and use 'show in multi editor'
            * Right click the box to add effects near effect 0, effect 1, etc
* Highlight all audio files for the unit and right click
    * Create play event for each individual
    * Create single stop event for all
* Switch 'Layouts' (at the top) to 'SoundBank'
* Create a new SoundBank (Your character name)
* At the lower left, highlight and drag all events tied to that character into the SoundBank Editor (bottom center/right)
* Right click the SoundBank you created and generate for the current platform (Maybe all should be work? Haven't tried it)
* Right click the SoundBank and open the containing folder (NAME.bnk)
### Custom Voices Instructions
* Move/Copy the generated .txt and .bnk files into the CustomVoices mod folder
* Use the included 'VoicePackDefCreator' to generate json files from the .txt provided
* Assign audio cues from the soundbank json to the voicepack json
    * For Arknights I included a template voicepack since all the audio files I'd use going forward would be numerically the same (ex. 031 and 032 are 'bad result' lines so I tried to tie them to negative voice lines)
* Move the voicepack.json file to the voices/voicepacks folder and the soundbank.json and .bnk files to the voices/soundbanks folder
### Tips
* Always double check for spelling/json errors
* **Always double check for spelling/json errors** (It's important so I'm adding it twice)
* Make sure these directories are included in the mod.json file
* Try deleting the '.modtek' folder and letting it regenerate if you have issues. The DB doesn't always get fully cleaned so if you've removed something before it might have left some references that are no longer valid
