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

## Install Emudeck

There's a ton of different ways to get emulators on your Steam Deck. Some you can install as Flatpaks, or directly from Valve, or manually compiling from source, etc.... but I've found Emu Deck to be the easiest. It is an install script that manages several different emulators for you with sensible defaults. 

https://www.emudeck.com/


### External monitor

Plug in your desired screen. Extend it to the right.

Set monitor as primary screen.

### Copy your stuff over

ROMs go in `/run/media/<sd card name>/Emulation/roms/` 

Mod information will come below. 

## Configure citra

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

## Miscellaneous important setup stuff

set sudo with ```passwd```

Increase swap on the Steam Deck

```
passwd # Create a root password for example "deck"
sudo steamos-readonly disable # Disable the read only FS
cd /home # There is a "swapfile" located here we'll reuse it
sudo swapoff -a # Stop swap process
sudo dd if=/dev/zero of=swapfile bs=1G count=8 # Increase swap to 8gb
sudo mkswap swapfile # swap ready file again
sudo swapon swapfile # Activate swap
```



```
sudo pacman-key —init
sudo pacman-key --refresh-keys
```

This applies to Desktop Mode.
If you have not already, use passwd to create a password for the deck user.
Disable read-only mode: sudo btrfs property set -ts / ro false
Initialize the pacman keyring: sudo pacman-key --init
Populate the pacman keyring with the default Arch Linux keys: sudo pacman-key --populate archlinux
Try installing a package: sudo pacman -S vi
https://www.reddit.com/r/SteamDeck/comments/t8al0i/install_arch_packages_on_your_steam_deck/

```
sudo pacman -S base-devel
install 1password 
```

https://support.1password.com/install-linux/#arch-linux


```
sudo pacman -S unzip
```
install ProtonUp-Qt from Discover
use ProtonUp to install ProtonGE

install ProtonTricks from Discover

https://github.com/mikeroyal/Steam-Deck-Guide


network -> smb://litterbox

plug in hdmi to the usb-c hub
extend to the right?
set monitor as primary screen

cd ~/.var/app/org.citra_emu.citra/config/citra-emu
cp qt-config.ini qt-config.old
vim qt-config.ini
Go to [Layout] section: <Esc> :257

citra: view -> uncheck single window mode

hide task bar
hide top bar

https://www.sportskeeda.com/gaming-tech/how-play-3ds-games-dual-screen-format-steam-deck-using-citra-emulator
https://www.youtube.com/watch?v=AgNvCFbeGpc

TODO figure out how to resize without a mouse
TODO mods?




xbox cloud gaming
https://support.microsoft.com/en-us/topic/xbox-cloud-gaming-in-microsoft-edge-with-steam-deck-43dd011b-0ce8-4810-8302-965be6d53296

——
install emudeck

other games working on emudeck in steamos interface 
https://www.youtube.com/watch?v=ylErPAL2cj0

general tips and tricks
https://www.youtube.com/watch?v=5uQcEyPzia4

https://www.sportskeeda.com/gaming-tech/how-play-3ds-games-dual-screen-format-steam-deck-using-citra-emulator

---
swap + TRIM + vram
https://www.youtube.com/watch?v=od9_a1QQQns

syncthing
https://www.reddit.com/r/SteamDeck/comments/vocyi5/start_syncthing_automatically_on_steamdeck_even/
  
## Majora's Mask enhancement packs

Here are some suggestions:

* [Project Restoration](https://github.com/leoetlino/project-restoration)
* [HD textures](https://github.com/DeathWrench/MM3DHD)
* [MM3D Remastered Soundtrack](https://github.com/sygemdev/Majora-s-Mask-3D-Remastered-OST)
