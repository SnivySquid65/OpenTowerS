# Open TowerS(nivy)
Build another tower using self obtained source from your copy!

# Contributing
You can contribute to this repository in many ways! Help by:
- Creating well written, and helpful issues
- Making a discussion page on a new, more efficient script or a page on porting the game to a different platform (ex. Linux, MacOS, Android, etc.), for example.
- Making a pull request, by far the most helpful, add and subtract from scripts, and other things!

# Credits
This repository is currently maintained by:
- SnivySquid65 (OpenTowerS, original commits to OpenTowerS and revised instructions)

Previously contributed to by:
- Lila / @femloy (Original OpenTower)
- @crystallizedsparkle (Original OpenTower)
- DogMatt / @doggywatty (Original OpenTower)
- Carl Barahona / @cccarl (Original OpenTower)

# A foreword
I refuse to involve myself in any drama regarding Lila, Pizza Tower, or anything else. This project intends to further document and make minor updates to Open Tower.

For more info on my stance and the state of this continuation, read [NOTICE.md](https://snivysquid65.github.io/OpenTowerS/NOTICE.html).

# Attribution
OpenTower is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt (modify), but you must give the appropriate credit. Read for more info.

# Requirements
- [Pizza Tower on Steam](https://store.steampowered.com/app/2231450/Pizza_Tower/)
- [GameMaker 2023.1.1.62](https://gms.yoyogames.com/GameMaker-Installer-2023.1.1.62.exe)
- [Steamworks SDK v1.55](https://partner.steamgames.com/downloads/steamworks_sdk_155.zip)
- [Undertale Mod Tool Version 0.5.1.0 or Newer](https://github.com/underminersteam/undertalemodtool/releases/tag/0.5.1.0/)

This repository doesn't include any of the datafiles (FMOD, langs) or sprites. An [UndertaleModTool](https://github.com/UnderminersTeam/UndertaleModTool/releases/tag/0.5.1.0) script is included to extract everything needed from the `data.win`, and port the required files to the decomp folder.

# The Script

1. Make sure Pizza Tower is up to date, and open its `data.win` file in UndertaleModTool. Open the "Scripts" tab at the top of the window, and select "Run other script..."

<img src="github/guide1.png">

2. Go to the decomp's folder, and select the `PTdecompiler - old UTMT.csx` file. (the new script doesn't work with any versions I can find, you can also run the old script on newer UTMT versions no problem.)

<img src="github/guide2.png">

3. The script will ask you to select a folder. Select the decomp folder.

<img src="github/guide3.png">

4. It takes a while to dump every frame of every sprite. Give it about 15 minutes... Make sure it dumps this to the same folder the YYP file is located.
5. Run the `PizzaTower_GM2.yyp` in the *right version of GameMaker*. Open Extensions > Steamworks and change the "Steam SDK" location to wherever you put your Steamworks SDK. If that doesn't work, try going INTO the Steamworks folder and make that the path instead. 

**If you try building the game with Steamworks, it will just run the unmodded game.** You can always just remove the extension though. Look through all Steam related code, and comment out any use of the `steam_` functions. I think you can also just delete the `steam_api64.dll` file from the build.

# Upgrading GameMaker

If you want to move to a future GameMaker version you'll need to make some changes.

1. Remove Steamworks and all code associated with it, unless you're gonna do some weird Pizza Oven stuff.
2. New IDE versions tend to re-order and move things around, making stuff run in a different order. This breaks warps, parallax, the camera, menus... Make a controller object that runs object's step events in the correct order.
3. Whenever text is drawn to the screen, offset it by the font's sprite origin, as horrible as that might sound. You can hook into the `draw_text` functions with some macro shenanigans.
4. Rename the `string_split` function to something else, it's reserved now. CTRL+SHIFT+F to mass replace.
5. Probably more. I forgot. If you got this far you can figure out the rest anyway.

# Issues
### Empty GameMaker
If you normally use a newer GameMaker version, opening the old one will lead to the IDE getting stuck in a dark gray screen. To fix this, delete the `%programdata%/GameMakerStudio2` folder while the IDE is closed and then reopen it.

### ImageMagick error when opening .csx
You have the wrong UndertaleModTool version, or are using the wrong script. Make sure you're using the `PTdecompiler - old UTMT.csx` script instead. Get [a version of UTMT that is version 0.5.1.0 or newer as well, if you haven't already.](https://github.com/underminersteam/undertalemodtool/releases/tag/0.5.1.0)

**DO NOT USE BLEEDING EDGE!! IT IS CONSTANTLY IN DEVELOPMENT AND MAY NOT BE A GOOD IDEA TO USE JUST IN CASE SUPPORT FOR THE SCRIPT BREAKS!**
