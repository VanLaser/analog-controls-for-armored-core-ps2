## QoL enhancements: analog controls for Armored Core PS1 series: AC1, AC: Project Phantasma and AC: Master of Arena

Supported versions: 

- AC1: USA (SCUS_941.82), USA (SLUS_013.23 - Reprint edition), Japan (SLPS_009.00), Eu (SCES_008.42)
- AC: Project Phantasma: USA (SLUS_006.70), Japan (SLPS_011.30), Japan (SLPS_911.10 - Playstation the Best) 
- AC: Master of Arena: USA 2CDs (SLUS_010.30 / SLUS_010.81), Japan (SLPS_018.55 / SLPS_018.56), Japan (SLPS_914.44 / SLPS_914.45 - PSone Books)

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
- The unpatched _Japan (SLPS_011.30)_ version only works with controller in 'digital' mode, see the **AC1 Notes** above
  
### AC: Master of Arena notes

- Missions, garrage AC test, arena and ex-arena work, but 'Vs. (Splitscreen)' and 'ILINK' modes are not patched
- Since it's based on recording (digital) inputs only, the replaying system is broken
- For some reason, the _PCSX-Redux_ emulator hangs when loading an Arena or Ex-Arena fight (at least for the USA edition), therefore I recommend using _Duckstation_ for this game.  

### Usage:

Use the relevant *.ppf* file with **PPF-O-MATIC 3.0** and the game's original *.bin* file to create a patched *.bin*.

Feedback welcome.

## QoL enhancements: analog controls for Armored Core PS2 series (AC2, AC2: Another Age, AC3, AC: Silent Line - USA edition).

Analog input processing inside these games was retro-fitted using algorithms from AC Nine Breaker.

*Left analog* sends the following commands: strafe left, strafe right, forward, backward.  
*Right analog* sends the following commands: turn left, turn right, look up, look down.

The analog controls keep working exactly the same ^, even if the user changes the control scheme for the digital buttons, so the buttons can be remapped in-game as you like.

Most importantly, the right analog movement uses the same algorithms as those from Armored Core: Nine Breaker, so it is not just a remapping: the movement is actually smoothed out, different areas of joystick displacement are treated differently based on the analog value received (not just 0 / 1). In other words, no more junky looking / turning around.

For games that mirrored left joystick to D-PAD buttons, that operation was removed during fights, and replaced with the left analog functionality described above (in other words, left joystick in game does not depend at all of how user mapped the D-PAD buttons).

![AC-PS2](https://github.com/VanLaser/analog-controls-for-armored-core-ps2/assets/8756008/209a57a4-2a13-4af7-9521-9ffb74f308d6)

The _.pnach_ files need a recent PS2 emulator, **PCSX2-qt nightly** is highly recommended.  
The _.ppf_ files can patch the right ISO using **PPF-O-MATIC 3.0**

### Technical details

The look up / look down analog displacement has three zones:

- inside deadzone, view speed converges to zero
- outside deadzone, view speed is proportional to joystick displacement (AC: Nine Breaker formulas)
- towards the edge (joystick pulled/pushed hard), movement is additionally accelerated using AC: Nine Breaker formulas.

The turn left / turn right analog displacement has two zones:

- inside deadzone, turn speed converges to zero
- outside deadzone, turn speed is proportional to joystick displacement (AC: Nine Breaker formulas)

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

