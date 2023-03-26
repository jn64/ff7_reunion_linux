# Final Fantasy VII (Steam) + The Reunion Linux Install Guide

## Requirements

- [Final Fantasy VII (Steam version)](https://store.steampowered.com/app/39140/FINAL_FANTASY_VII/)
- protontricks — [install via your distro package manager, or flatpak if using Steam flatpak](https://github.com/Matoking/protontricks#installation)
- [The Reunion](https://ff7.live/index.html) mod installer — latest download as of this writing is `The_Reunion_R06z_march_01_2023.exe`
- [ff7_steam.reg](https://raw.githubusercontent.com/jn64/ff7_reunion_linux/69b6a85810852ec49c2a09f5c3c0aacfb0563942/ff7_steam.reg)
## Installation

1. Install FF7 in Steam.

2. Run the game once, to create the wineprefix and ensure it works.

   It may take a few minutes; don't force quit it from Steam early if you don't see any window appear. Once you see the FF7 launcher, the game itself should start quickly.

   Quit the game _and_ launcher before the next step.

3. Install The Reunion:

   - Run the following command in terminal:

     ```sh
     protontricks 39140 uninstaller
     ```

   - Click _Install_, browse to your download of `The_Reunion_R06z_march_01_2023.exe`. You may need to change the drop-down in the file browser to show exe's.
   - When asked for the install location, browse to `Z:/home/$USER/.local/share/Steam/steamapps/common/FINAL FANTASY VII/`

4. Install the FF7 Windows registry entries (required by The Reunion):

   - Run the following command in terminal:

     ```sh
     protontricks 39140 regedit
     ```

   - Click _Registry > Import Registry File_ and browse to your download of `ff7_steam.reg`

4. In Steam, set the launch options for FF7 like this:

   ```sh
   WINEDLLOVERRIDES='ddraw=n,b' %command%
   ```

   If you use [GameMode](https://github.com/FeralInteractive/gamemode) and/or [MangoHud](https://github.com/flightlessmango/MangoHud), you can add them as usual:

   ```sh
   gamemoderun mangohud WINEDLLOVERRIDES='ddraw=n,b' %command%
   ```

## Notes

- Please read The Reunion's help files and edit the `Options.ini` before playing.
- To check if The Reunion is working, press `Backspace + L` (keyboard) or `Select + Circle/A` (controller) to skip movie cutscenes.


### File locations

- The Reunion and related mod files will be inside the FF7 install folder at:

  ```
  ~/.local/share/Steam/steamapps/common/FINAL FANTASY VII/The Reunion/
  ```

- FF7 config files are in the wineprefix at:

  ```
  ~/.local/share/Steam/steamapps/compatdata/39140/pfx/drive_c/users/steamuser/My Documents/Square Enix/FINAL FANTASY VII Steam/
  ```

### Other mods

[See here for The Reunion compatible mods](https://ff7.live/reunion-mods.html), like SYW v4 (upscaled textures) and Field Icons (for Xbox controller icons).
