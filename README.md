# Steam Deck Emulation Ultimate Guide

## Getting Started

Boot over into Desktop mode (Hold the power button)


First things first, make clicking on Desktop mode not awful
- Desktop Mode
- Right click on the Steam app in the task bar
- Settings > Controller > Desktop Configuration
- Navigate with d-pad and game buttons; set Right Trigger to Left Mouse and Right Trigger to Left Mouse (or whatever works for your brain)
- Exit menu by pushing B. 
- Now you have easy mouse access with just the Deck in Desktop Mode, so long as Steam is running in the background. (More on this in a bit)

Quick aside: If you care about achievements in old games, sign up for an account at [RetroAchievements](https://retroachievements.org/). Make the password something you can easily type*

## Install Emulators

There's a ton of different ways to get emulators on your Steam Deck. Some you can install as Flatpaks, or directly from Valve, or manually compiling from source, etc.... but I've found Emu Deck to be the easiest. It is an install script that manages several different emulators for you with sensible defaults. 

https://www.emudeck.com/

Choose custom installation so you can set up options to your liking. I recommend installing to your SD card, and you can also select options such as bezels in very old 4:3 games and linking your RetroAchievements account.

## Install Syncthing
(optional but recommended) 

Now you've got emulators installed, but you need roms to make them worthwhile! You can get ROMs on to your Steam Deck any way you like, but I've found Syncthing to be incredibly helpful for seamlessly managing ROMs, HD packs, saves, etc. (Also I use Syncthing for Steam games that don't have Cloud Save enabled, like Dark Souls 2). 

- On Windows: https://syncthing.net/downloads/
- On Steam Deck: From the Discover software center, install Syncthing GTK (or `flatpak install flathub me.kozec.syncthingtk` )

- On your Steam Deck, launch Syncthing GTK and in the upper right corner click on the Cog > Show ID. 

- On Windows, Cog > Add Device > paste the ID in. Save.
- On your Deck you will get a notification about your PC being added; click Add. 

At this point you can simply add synced folders and they will appear on the other device. But we've got some hacking to do to make this a bit better. 

At this point I'd recommend connecting a keyboard to your Steam Deck and follow the [instructions written on this Reddit post](https://www.reddit.com/r/SteamDeck/comments/vocyi5/start_syncthing_automatically_on_steamdeck_even/). 

Emu Deck is configured to look for ROMs in `/run/media/mmcblk0p1/Emulation/` -- this folder I have synced across devices, so as I rip games on my Desktop, I can just drag them into `.../Emulation/roms/3ds/` and they will instanteously sync over to my Deck.

## Proof of Concept

Let's try running a game in Desktop Mode make sure everything works.

Copy a ROM over to your deck. Any supported system is fine (some require BIOS, etc; things like Dolphin (Gamecube, WII) or anything with a RetroArch core (SNES etc) will be easy. 

For the remainder of this test I will be using Super Metroid for the SNES as an example. However you got your ROM file over to your Deck, it should be located in `/run/media/mmcblk0p1/Emulation/roms/snes/Super Metroid.sfc`

Launch your SNES emulator, **RetroArch**, by going to Start > Games > RetroArch. Load the game in to RetroArch by going to `Main Menu > Load Content > Playlists > Import Content > Scan Directory > <Scan this Directory>` (it should already be pointed at the right place, namely, `/run/media/mmcblk0p1/Emulation/roms`.

From the main RetroArch screen, scroll down to the bottom of the left menu to the Super Nintendo Entertainment System, select Super Metroid, pick an appropriate core, and hit Run. The game should load and also give you notifications about your achievement progress if you entered your RetroAchievements credentials during the Emu Deck install. Nice!!! Ok, hold `Start + Select` simultaneously to close out of the game.

## Further Setup

Ok we have our emulators installed, we have Syncthing set up to easily manage ROMs (etc), and we got our first ROM to load. Awesome progress. 

Emu Deck comes with a program that will detect your ROMs and add them as "non-Steam games" to Steam for you. **I HIGHLY HIGHLY HIGHLY HIGLY RECOMMEND DOING THIS. ** Launching your emulated games within Steam is not only a lot easier than going to Desktop mode, but also allows you to manage custom keybindings a lot easier. 

In order to do this, first things first:
- Be in Desktop Mode
- Close out of Steam (on the task bar, right click > Exit Steam)
- Launch the EmuDeck program from your Desktop
- At the bottom, click the 'Tools & Stuff' button
- Select `SteamRomManager`, click Yes on the warning
- Once `SteamRomManager` launches, maximize this window
- On the left menu, click 'Preview' -- this screen will be empty. At the very bottom click 'Generate app list' and wait a moment for the parsers to run
- Once the app list is complete, click 'Save app list' at the bottom. 
- Close out of `SteamRomManager`

At this point, all ROMs you have located in the correct directory will now have proper Steam entries. Let's verify this works. Click the `Return to Gaming Mode` button on your Desktop.

Go to your Library. Scroll to the right with R1 until you're at Collections or Non-Steam games. Here you'll find all of your emulators and also all of your ROMs, each with custom art. Launch Super Metroid to make sure it works. Achievements should be working too. Hell yeah! 


# General Steam Deck setup stuff

## Miscellaneous important setup stuff

set sudo with `passwd`
increase swap + TRIM + vram: https://www.youtube.com/watch?v=od9_a1QQQns


OR DON'T DO THIS MANUALLY AND USE CYRO TOOLS. MUCH EASIER! https://github.com/CryoByte33/steam-deck-utilities


## Other important Steam Deck performance stuff

- install ProtonUp-Qt from Discover
- use ProtonUp to install ProtonGE
- install ProtonTricks from Discover
- install PowerTools + Decky

## Install 1Pass

[JUST INSTALL THE FLATPAK](https://support.1password.com/install-linux/#flatpak)


# DOWN HERE IS ALL WORK IN PROGRESS STUFF / PERSONAL NOTES / ETC 

# Specific emulator setup

Remember to set your Steam controller options to use an EmuDeck preset in order to get the most out of the [EmuDeck hotkeys](https://github.com/dragoonDorise/EmuDeck/wiki/Hotkeys) !!

## Citra

You can use Citra handheld mode with no problems. After loading a 3DS game in to Steam Rom Manager, go back into gaming mode and launch the 3DS game. Once it launches, hit the Steam Button, select Controller Settings, and choose `EmuDeck - Citra 3DS` template. It binds the back buttons to swap between the two screens and a couple built in screen sharing options! 

### External monitor

Plug in your desired screen. Extend it to the right.

Set monitor as primary screen.

### Configure citra

This is the only tricky part of the whole thing. 

- DISABLE VSYNC
- DISABLE HARDWARE SHADERS
- TODO write explanation

- Or not, this guy already did the same thing:
https://overkill.wtf/how-to-play-nintendo-zelda-ocarina-of-time-and-majoras-mask-in-4k-on-steam-deck/

```
cd ~/.var/app/org.citra_emu.citra/config/citra-emu
cp qt-config.ini qt-config.old
vim qt-config.ini
Go to [Layout] section: <Esc> :257

```

citra: view -> uncheck single window mode


## Game mods working on citra


```
/home/deck/.var/app/org.citra_emu.citra/data/citra-emu/load/textures/
```

### Majora's Mask enhancement packs

Here are some suggestions:

* [Project Restoration](https://github.com/leoetlino/project-restoration)
* [HD textures](https://github.com/DeathWrench/MM3DHD)
* [MM3D Remastered Soundtrack](https://github.com/sygemdev/Majora-s-Mask-3D-Remastered-OST)

### Running Citra on the Deck while docked to a monitor for primary output

plug in hdmi to the usb-c hub
extend to the right?
set monitor as primary screen

i was gonna write this but somebody else did already https://www.sportskeeda.com/gaming-tech/how-play-3ds-games-dual-screen-format-steam-deck-using-citra-emulator

```
cd ~/.var/app/org.citra_emu.citra/config/citra-emu
cp qt-config.ini qt-config.old
vim qt-config.ini
Go to [Layout] section: <Esc> :257
```

citra: view -> uncheck single window mode

hide task bar
hide top bar

https://www.sportskeeda.com/gaming-tech/how-play-3ds-games-dual-screen-format-steam-deck-using-citra-emulator
https://www.youtube.com/watch?v=AgNvCFbeGpc


## xbox cloud gaming
https://support.microsoft.com/en-us/topic/xbox-cloud-gaming-in-microsoft-edge-with-steam-deck-43dd011b-0ce8-4810-8302-965be6d53296

