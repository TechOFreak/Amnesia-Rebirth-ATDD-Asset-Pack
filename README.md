# Amnesia-Rebirth-ATDD-Asset-Pack
Assets from the Amnesia The Dark Descent ported over to Amnesia: Rebirth (HPL3). Assets come from a combination of sources, the TDD base game, SOMA TDD asset pack and Amnesia: Remasted mod. These core assets were then tested, ported and modified as required to work with Amnesia Rebirth's HPL3 game engine.

<b>Anyone can use these assets in their custom story as long as you credit us.</b>

# Setup

Included is a sample custom story which contains all the Amnesia The Dark Descent assets. A trailer of the sample maps can be found here https://youtu.be/2b56oXE6iAA. An installation video of these assets can be found here https://youtu.be/f-6NBhL2k5E.

1) [Skip if you have an existing custom story] If you do not have an existing project you can use this custom story as a template custom story for your new custom story that will be using these assets. Create a new folder in your Amnesia Rebirth/mods directory and give your custom story a name, then copy all the contents into that folder (assets, config, editor, etc.). Pretty much as if you were installing/creating a custom story.

2) If you have an existing custom story you should only copy over the /assets folder, the /script folder and the /editor folder into your custom story folder. As a note, you may already have the files /script/custom/modules/ItemHandler.hps or /script/custom/player/ItemCallbacks.hps, as of v0.1.0a the changes to these script files are soley for the ATDD Lantern assuming that you have it added to your inventory.cfg file as item type ATDDLantern. If you already have your own version of these script files I would recommend copying over your changes to this script. If you do not want to mess with your script file then I would recommend replacing the Amnesia: Rebirth lantern with the one from TDD, this is the way I did it in the sample custom story and it will not require the use of those 2 script files.

3) If you plan to keep the main menu from the sample custom story then you should open config/main_init.cfg and change the line Folder="ATDD_Asset_Pack/maps/" and replace "ATDD_Asset_Pack" with the name of your custom story folder.

4) Navigate to your Documents folder and locate the HPL3 folder (should be created automatically if you've started the level editor for the first time). Create a new file inside the HPL3 folder with the name WIPMod it should be a .cfg file. Inside of the file you should have the following, where *FULL_PATH_TO_REBIRTH_FOLDER* is the full path to the Amnesia Rebirth (Ex. C:\Program Files (x86)\Steam\steamapps\common\Amnesia Rebirth) and where *YOUR_MOD_NAME* is the name of your custom story folder as it appears in your Amnesia Rebirth /mods folder.

```
<WIPmod Path="*FULL_PATH_TO_REBIRTH_FOLDER*\Amnesia Rebirth\mods\*YOUR_MOD_NAME*\entry.hpc" />
```

5) Open your HPL3 level editor and check to see if you can see the entities and static objects.

6) If you start a new mod with these assets be sure to update the WIPMod with the new directory.

7) In the future, when new versions for this asset pack are available, you should read the change log before updating the assets on an existing custom story. Some assets you are using may be affected by the new versions.

# Usages

<b>Grunts, Brutes and Suitors</b>

Custom script files were created for these 3 enemies (located under script\custom\agents) to handle there AI. The ghoul's AI script was modified to work with these 3 enemies. This means that these 3 enemies will use the Agent_ and Ghoul_ helper functions and technically identify as a ghoul to the game engine. Compared to the Amnesia Rebirth ghoul, these enemies have very few animation, for that reason I recommend using these enemies as they were used in TDD (that means no climbing, no grabbing, no crawling, etc.). You should be able to use them as if they were a ghoul but I recommend running the following functions prior to spawning one of these enemies in your map.

```
//First variable is the name you assigned your enemy in the level editor.
Ghoul_SetAllowPlayerThrow("grunt", false); 
Ghoul_SetSmellingActive("grunt", false);
```

Note: If you make one of these enemies perform an action that they do not have an animation for (like grabbing/throwing the player) the AI will break and the enemy will freeze. Aside from the basic TDD actions these enemies have not been fully tested, feel free to play around with them.

Future Changes: I have 2 ideas in mind for these enemies. I would like to re-create the AI from scratch and create a set of helper functions for each of these enemies or if someone with more knowledge on creating animations is willing to contribute then I can do a full port of these enemies and pretty much turn them into ghouls (yup, that means you would see a grunt climbing up the walls).

<b>Waterlurker</b>

The frictional game developers removed an enemy called a Sandlurker from the Amnesia Rebirth final game, it didn't seem completed. The AI for the sandlurker was taken, completed and ported into a waterlurker. The waterlurker will identity as a sandlurker to the game engine, this means you can use the Sandlurker_ helper functions. To use the water lurker you should first place down a liquid area in your map, now place a trigger area inside of your liquid area to specify the waterlurkers hunt area, give it a name Ex. "waterlurker_hunt_area". Now place an entity somewhere in the hunt area or liquid area to identify the waterlurkers home (give it a name), you can set it to not be active if you do not want the player to see it. Now place down the waterlurker somewhere in the liquid or hunt area, under the waterlurker's entity tab find "SandLurker" and then enter the names of the HomeEntity and HuntArea that you just created. That's it, you can spawn it in using the following function:

```
//First variable is the name you assigned your waterlurker in the level editor.
Entity_SetActive("waterlurker", true);
```

The waterlurker will be attracted to any entity that has a body material that contains the word "organic". You can check/change this by opening up the entity in the model editor, clicking the main body and navigating to the "body" tab.

Future Changes: Similar to the enemies I would like to recreate the AI from scratch and create helper functions specifically for the waterlurker.

# Inventory Items

Any of the inventory items from TDD located under assets/entities/item can be added to the Amnesia: Rebirth game. The items could be added just like any other item in rebirth. Some inventory items had special uses that may require you to create your own script file (Ex. Tinderbox). It is also recommended that you specify the file extension when specifying the inventory icon in the inventory.cfg (Ex. "lantern.tga"). If you do not know how to add custom items check out episode 24, 25 and 49 of TechOFreak's Amenesia Rebirth tutorial series.

* Episode 24 Item Titles & Descriptions: https://youtu.be/3dkX7JsBWOM
* Episode 25 Keys! Unlocking Doors!: https://youtu.be/pBXM3Xu5IVA
* Episode 49 Custom Inventory Items: https://youtu.be/O3Yd_T7WBr0

# Report Bugs

One of the main reasons this asset pack is releasing in an alpha state is because more users would help to identify bugs. You can post bugs wherever you'd like but I would prefer that bugs be reported on the discord channel https://discord.gg/deuVwxFV44 under the #atdd-bug-report channel. If not there, then I would prefer that you create a new issue on the github repository https://github.com/TechOFreak/Amnesia-Rebirth-ATDD-Asset-Pack/issues. I will also take notes of any comments placed on other sites where this asset pack has been uploaded but the primary ones that will be looked at are the discord and github issue reports.

# Known Bugs

As of version 0.1.0a these are the known bugs:

* Cisternbase broken bridges have messed up collision.
* Cellar door hinge body collision has to be disabled or re-worked.
* Dungeonbase heightmap is flat. Needs full re-creation.
* Pig guy entity needs animation re-work.
* Some doors sound very loud. Might need audio re-work.

# Future Plans

* Get better quality images for inventory icons (64x64 to 256x256).
* Create an inventory.cfg for all inventory item assets.
* Create custom lantern script (instead of using the Rebirth script).
* Touch up the heightmaps of some of the static objects.
* Create enemies scripts from scratch or do a full blown port.

# Community & Help

Join our community in the discord link below. Also below are links to other things you might find useful. If you would like to contribute to this project please join the discord and ask to join the team.

* TechOFreak's Amnesia Hub Discord: https://discord.gg/deuVwxFV44
* TechOFreak's Amnesia Rebirth Tutorial Series: https://www.youtube.com/playlist?list=PL4KkjlmOwLwwMVqedCNpi6caUxhgyf8Qr
* Github Repository Issue Report: https://github.com/TechOFreak/Amnesia-Rebirth-ATDD-Asset-Pack/issues
* Amnesia Rebirth ATDD Asset Pack Trailer: https://youtu.be/2b56oXE6iAA
* Steam Workshop Link: https://steamcommunity.com/sharedfiles/filedetails/?id=2606335924

# Featured Custom Stories

Below are some of the custom stories that feature these assets:

* Amnesia: Reminiscence - Patrisiogames - https://www.moddb.com/mods/amnesia-reminiscence

# Credits

TechOFreak & Patrisiogames are the primary workers on this project, all if this work is done soley as a contribution to the Amnesia Rebirth community and never for financial reasons. Thanks to florian. the creator the Amnesia: Remastered assets, these versions of the assets were used for their high quality. Thanks to frictional games for the amazing Amnesia franchise, also for the SOMA TDD Asset pack which contained some of the assets already ported over to the HPL3 engine.

* TechOFreak - Asset Porter & Tester
* Patrisiogames - Asset Porter & Tester
* florian. - Amnesia: Remastered - https://www.moddb.com/mods/amnesia-the-dark-descent-remastered
* Frictional Games - Amnesia: Rebirth & Amnesia The Dark Decent & SOMA TDD Asset Pack
