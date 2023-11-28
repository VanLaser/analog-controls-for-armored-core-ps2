## QoL enhancements (WIP): analog controls for Armored Core 3 Portable - USA (PPPSSPP emulator)

Adds _dual analogs_ capability to the game, with actual analog processing for turning and looking up/down (right stick),  when run from PPSSPP.

(For more details about how these patches work, see PS1 and PS2 sections)

- feature complete, but there may be bugs
- 'cwcheat' format ('_.ini_' file)
- replays are (and will be) broken
- only tested on PPSSPP - should work on at least PPSSPP version 1.13.2 or newer

#### Install instructions (PPSSPP emulator)

In order for this mod to work, you will need to set the following PPSSPP settings: 

- the controller configuration needs to have mappings added for the in-game right analog (even if the real PSP didn't have a right analog pad), matching the axis of your controller (see picture below).
- cheats have to be enabled in the emulator settings
- with a recent version of PPSSPP, the '**_.ini_**' file that contains the cwcheat information has to be placed into the _'C:\Users\\<your user\>\Documents\PPSSPP\PSP\Cheats'_ folder
- for older PPSSPP versions, this path is _'\<PPSSPP-install-folder\>\memstick\PSP\Cheats'_ instead

To confirm, right click the game's icon, click the 'Cheats' option and you should see the patch name on the right, with an enabled checkbox:

![ppsspp-enable-cheat](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/595ffc0b-384e-42bc-8b33-531c73616dea)

#### Purging

Normally, to purge weapons/parts in this game one has to press a combination of five buttons, which works with the default in-game button keymap, but: changing the in-game button keymap has a large number of combinations that will simply disable purging completely.
When using dual analog controls, it is expected that the user will want to change the default keymap (for example moving boost to L1, right weapon to R1 etc.) 

The mod includes an extra 'Purge' modifier button, _functional with **any** custom keymap_ , by adding into the game the formally unused PSP MUSIC_NOTE button: pressing this modifier button will send the "_strafe left/strafe right/look up/look down_" combo (no matter how the buttons are mapped in-game), which means the user only needs an extra button pressed (_weapon change_, _toggle extension_ or _left weapon_ - again taking into account the in-game button mapping), in order to specify what weapon/part has to be purged. 

An extra key or controller button has to be mapped in the PPSSPP emulator to the PSP MUSIC_NOTE button, so that its value can be actually sent into the game, to act as 'Purge' modifier. For example (mapped to R2):

![purge-mod](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/d50d167e-fa8d-455a-ae84-8fbfda6f63c9)

#### Notes

The patch _might_ work with the Adrenaline, if that emulator is also able to map a right analog pad and send the data inside the game, as PPSSPP does. Otherwise, somebody has to write a plugin for that.

Even if it's a 'cwcheat' (that continuously writes in memory), the patched addresses actually contain all the needed relocation fixes for it to work by directly patching the main executable file. 
In other words, if one knows how to extract/convert the data from the cwcheat and map it to file offsets, then actually patches a decrypted EBOOT.BIN file and inserts it back into the original ISO (e.g. by using UMDGen),
it should work in PPSSPP (and maybe Adrenaline) without the need to enable cheats.

------

## QoL enhancements: analog controls for Armored Core PS1 series: AC1, AC: Project Phantasma and AC: Master of Arena

Supported versions: 

- **AC1:** USA (SCUS_941.82), USA (SLUS_013.23 - Reprint edition), Japan (SLPS_009.00), Europe (SCES_008.42)
- **AC: Project Phantasma:** USA (SLUS_006.70), Japan (SLPS_011.30), Japan (SLPS_911.10 - Playstation the Best) 
- **AC: Master of Arena:** USA 2CDs (SLUS_010.30 / SLUS_010.81), Japan (SLPS_018.55 / SLPS_018.56), Japan (SLPS_914.44 / SLPS_914.45 - PSone Books)

**_Each patch includes an "Inverted Look Up/Down" version in a separate folder._**

The patches work ONLY with these versions, and only work if the relevant _.bin_ files are clean, i.e. not already patched with something else (undubs etc.)

![AC-PS1](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/3ec27093-ebd7-4541-801f-669bbf0fb639)


Analog input processing inside these games was retro-fitted using algorithms from AC Nine Breaker.

*Left analog* sends the following commands: strafe left, strafe right, forward, backward.  
*Right analog* sends the following commands: turn left, turn right, look up, look down.

The analog controls keep working exactly the same ^, even if the user changes the control scheme for the digital buttons, so the buttons can be remapped in-game as you like.

Most importantly, the right analog movement uses the same algorithms as those from Armored Core: Nine Breaker, so it is not just a remapping: the movement is actually smoothed out, different areas of joystick displacement are treated differently based on the analog value received (not just 0 / 1). In other words, no more junky looking / turning around.

Note that even in these PS1 games, the control scheme is pretty much the same as "Type B" in later PS2 games (AC Nexus and after). Therefore implementing a kind of "Type A" control scheme (analog-based) should provide a big accesibility boost without adding an unfair advantage (i.e. the 'Fairness' paragraph in the PS2 section still applies). On the contrary, any old school AC player would tell you that "Type B" still has the advantage.

### AC1 Notes:

The original game only works with the controller in 'digital' mode.
Patched game only works with the controller in 'analog' mode.

Normally this can be configured in your PS1 emulator settings, or
**by pressing the controller 'digital/analog switching mode' button**,
if it has one.

Duckstation emulator knows that the game only works in digital mode,
therefore by default it won't allow switching to analog mode from the GUI.
BUT, you can still switch to analog mode by pressing your controller's analog button
(and this is the simple, recommended approach).

Optional: to default to analog mode when the game starts, edit 'Duckstation/resources/gamesdb.json'
with a text editor, search for 'SLUS-01323' and modify the "controller"
entry value from "DigitalController" to "AnalogController".

![duckstation-ac1-gamedb json](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/3111006f-2411-4049-add8-2124cd45ab05)

This is how you it should look like, after editing 'gamesdb.json':

![duckstation-ac1-patched](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/5fc1f568-425d-42ed-81f2-8abcb758e328)

Note that, if Duckstation automatic updates are on, you will lose
the modifications in 'gamesdb.json', so you have to either repeat
the steps above, disable the updates, maybe make the file read-only,
have a backup ready - or use the analog buton on the controller to switch to analog after game starts.

### AC: Project Phantasma notes

- Missions, garrage AC test and arena work, but 'Vs. (Splitscreen)' and 'ILINK' modes are not patched
- Since it's based on recording (digital) inputs only, the replaying system is broken
- The unpatched _Japan (SLPS_011.30)_ version also starts with controller set in 'digital' mode, similar to the first Armored Core game, see the **AC1 Notes** above
  
### AC: Master of Arena notes

- Missions, garrage AC test, arena and ex-arena work, but 'Vs. (Splitscreen)' and 'ILINK' modes are not patched
- Since it's based on recording (digital) inputs only, the replaying system is broken
- For some reason, the _PCSX-Redux_ emulator hangs when loading an Arena or Ex-Arena fight (at least for the USA edition), therefore I recommend using _Duckstation_ for this game.  

### Usage:

Use the relevant *.ppf* file with **PPF-O-MATIC 3.0** and the game's original *.bin* file to create a patched *.bin*.

OR, when using the Duckstation emulator: if you go at 'Settings->Console' in the menu, you can enable an option called "Apply Image Patches". Then, if you have the .bin/.cue pair files in their own folder, AND you place there the proper .ppf file and rename it so that it has the exact same name as the bin/cue pair (but still keep the extension .ppf), Duckstation will "see" the patch and use it on the game automatically, while still leaving the .bin file intact.

Feedback welcome.

------

## QoL enhancements: analog controls for Armored Core PS2 series (AC2, AC2: Another Age, AC3, AC: Silent Line).

Supported versions:

- **AC2:** USA (SLUS_200.14), Europe (SLES_500.79), Japan (SLPS_250.07) (including inverted look up/down _.ppf_ versions of each patch)
- **AC2: Another Age:** USA (SLUS_202.49), Europe (SLES_509.05), Japan (SLPS_250.40) (including inverted look up/down _.ppf_ versions of each patch)
- **AC3:** USA (SLUS_204.35), Europe (SLES_513.99), Japan (SLPS_251.12) (including inverted look up/down _.ppf_ versions of each patch)
- **AC: Silent Line:** USA (SLUS_206.44)

Analog input processing inside these games was retro-fitted using algorithms from AC Nine Breaker.

*Left analog* sends the following commands: strafe left, strafe right, forward, backward.  
*Right analog* sends the following commands: turn left, turn right, look up, look down.

The analog controls keep working exactly the same ^, even if the user changes the control scheme for the digital buttons, so the buttons can be remapped in-game as you like.

Most importantly, the right analog movement uses the same algorithms as those from Armored Core: Nine Breaker, so it is not just a remapping: the movement is actually smoothed out, different areas of joystick displacement are treated differently based on the analog value received (not just 0 / 1). In other words, no more junky looking / turning around.

For games that mirrored left joystick to D-PAD buttons, that operation was removed during fights, and replaced with the left analog functionality described above (in other words, left joystick in game does not depend at all of how user mapped the D-PAD buttons).

![AC-PS2](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/209a57a4-2a13-4af7-9521-9ffb74f308d6)

### Install instructions (emulator)

The _.pnach_ files need a recent PS2 emulator, **PCSX2-qt nightly** is highly recommended.  

- Copy the _.pnach_ files into the _'\<PCSX2 install dir\>/cheats/'_ folder. If there is no 'cheats' folder, use the 'patches' folder instead (you have an older version of PCSX2)
- Open PCSX2, don't start the game yet
- Select the Armored Core game you want to play from in the game list, right-click, click 'Properties' - this will open a 'Game Properties' window
- Select 'Cheats' entry on the left, make sure option 'Enable Cheats' is checked, then enable 'True Analogs' below
- You will need to restart the game every time you change the option (the patch modifies the game only once, when the game starts)

![pcsx2-cheats](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/a9258ffc-d265-4fa2-8308-e456de8e191e)

#### Notes

- if your PCSX2 is a bit older, there will be no 'Cheats' entry. In that case, use the 'Patches' entry instead
- if you see no 'True Analogs' entry, your PCSX2 may be too old to support the new _.pnach_ file format
- if you see the 'True Analogs' entry, but it's greyed out (can't enable it), your Armored Core game CRC is "wrong", which means you're playing a patched Armored Core, or a different version of the game

To modifiy a game ISO directly, use the _.ppf_ files instead. The _.ppf_ files can patch the right ISO using **PPF-O-MATIC 3.0**

### Technical details

The look up / look down analog displacement has three zones:

- inside deadzone, view speed converges to zero
- outside deadzone, view speed is proportional to joystick displacement (AC: Nine Breaker formulas)
- towards the edge (joystick pulled/pushed hard), movement is additionally accelerated using AC: Nine Breaker formulas.

The turn left / turn right analog displacement has two zones:

- inside deadzone, turn speed converges to zero
- outside deadzone, turn ~~speed~~ acceleration is proportional to joystick displacement (AC: Nine Breaker formulas)

Note that you won't be able to turn or look faster than before, just smoother.

The analog movement outside deadzone will also send the digital input mapped by the user in that direction, but the acceleration will be "intercepted" and computed using the above formulas instead of being based only on the digital button information.

### Fairness:

- The later PS2 AC games, starting with Nexus, implement two controller schemes: classic, digital (Type B) and analog-based (Type A).  
- The older games implement looking up/down and turning left/right in the same way as 'Type-B' in the later games.
- The patches retro-fit into the earlier games the 'Type-A' formulas for looking up/down and turning left/right from the later ones (namely, AC: Nine Breaker).

So: the advantages one has in playing with these patches should be the same as using 'Type A' instead of 'Type B' in the later games.

### Limitations:

- Since in-game replays are performed by re-running the same sequence of digital inputs recorded by the game during the actual fights in the arena, the analog-based movement breaks the replaying system.
- The patches are meant for single player, hooked to the 1st controller. This doesn't mean the game should "break" in any multiplayer scenario, just that the 2nd player will only have access to default, non-enhanced controls.

-------

## Dedicated 'Fire Inside Weapon' button for 'Type B' controller scheme (AC: Nexus disc 1 and 2, AC: Nine Breaker and AC: Last Raven)

This patch allows firing the Inside part/weapon on Type B (classic, non-analog) controls without having to switch to it. It uses "right analog UP" to fire (right analog stick is not otherwise used with Type B controls, and no other buttons are free). Basically it levels the field with Type A - analog-based - control scheme, who *DOES* have a dedicated button for firing the Inside part/weapon.

There is no *.pnach* file for AC Last Raven, only the *.ppf*, since the patch affects two files in the ISO image. Use **PPF-O-MATIC 3.0** with the *.ppf* file in order to patch the original AC: Last Raven (USA) ISO image.

