## QoL enhancements: analog controls for Armored Core PS2 series (AC2, AC2 Another Age, AC3, AC Silent Line).

*(THIS STILL NEEDS TESTING: if you finish any of these games with the enhancement on, please tell me so I have some feedback)*

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

## Dedicated 'Fire Inside Weapon' button for 'Type B' controller scheme (AC: Nine Breaker and AC: Last Raven)

This patch allows firing the Inside part/weapon on Type B (classic, non-analog) controls without having to switch to it. It uses "right analog UP" to fire (right analog stick is not otherwise used with Type B controls, and no other buttons are free). Basically it levels the field with Type A - analog-based - control scheme, who *DOES* have a dedicated button for firing the Inside part/weapon.

There is no *.pnach* file for AC Last Raven, only the *.ppf*, since the patch affects two files in the ISO image. Use **PPF-O-MATIC 3.0** with the *.ppf* file in order to patch the original AC: Last Raven (USA) ISO image.

