# GroupCombatToolKit

This package is a robust group combat assistant for Mudlet that should makes organizing or following group combat much easier. It follows and switched targets, can call targets and target orders, add/remove/set target orders, designate leaders and additional target callers, report afflictions given, and more. 

# Installation

To install the system: 

1. Download the zip.
2. Unzip it somewhere permanent. Don't delete the unzipped files.
3. Make sure that you're connected to Achaea and logged in.
4. Install `Raid Assist Aliases.xml`, `Raid Assist Scripts.xml`, `Raid Assist Triggers.xml` in the Package Manager.
5. QQ and Restart Mudlet. System is ready to use!

# Basic Setup

These steps are the quick way to set up the system to follow party target calls.

1. `zOn` - Turns the system on.
2. `zL <player>` - Designate group leader. You will follow their targets, auto add their target list if they call it.
3. `zA` - Toggle on 'auto' target switching.
4. `zSTAT` - Shows the the system status and what is toggled on/off.
5.  Optional: `zADD <enemy>` - Will add enemy to target list and auto enemy them.
6.  Optional: `zTC <player> <player2>` - Designate up to two other players who will call targets that you will follow.
7.  Optional: `zREPORT` - Will report targets movement and call afflictions you give.
8.  Optional: `zLOUD` - Will echo your target switches to the party if not leading or a designated caller.

`zR` - Switches to first target in the list that is in the room
`zN` - Switch to next target in list
`zF` - Switch to first target in order
`zT` - Switch to last party target called (by leader or callers)

# To Lead

To set up the system to lead. Follow the above steps, plus:

1. `zL <ME>` - Sets you as the group leader. You will echo all target switches to the party. (`zLOUD` is does not need to be toggled on.)
2. `zBW <city name or first letter>` - Auto adds everyone from a city to target list
3. `zCITY <city name of first letter>` - Sets primary target city.
4. `zADD <enemy> / zMULTI <enemy> <enemy> <enemy>` - Adds enemy/enemies to target list.
5. `zORDER` - Show target list and set target order.
6. `zGROUP` - Reports information from `zSTAT` to party.

## Aliases

List of aliases to toggle things on and set up the system. `zHELP` or `zHELP2` will give the full and up to date list in game.

-`zON/OFF` - Raid system all on or off
-`zSTAT` - Raid system info
-`zL <name or 'Me'>` - Set leader
-`zORDER` - List target order for reordering
-`zCALL(F)` - Call target order, F forces announce
-`zC(F)` - Call current target, F forces announce
-`zTC <name> <name, if needed>` - Option to set specific target callers (1 or 2) in addition to leader
-`zGROUP` - Report leaders, target, target list, callers, and more to party
-`zADD <name (#)>` - Add enemy to list at end or into a spot
-`zMULTI <name>, <name>, <name>, etc` - Add several enemies at once
-`zREMOVE <name>` - Remove enemy from list
-`zSWAP <name> <#>` - Manual reordering person to a position
-`zENEMY` - Enemies the target list
-`zAUTO` - Enable setting enemies automatically
-`zA` - Turn on target switching if your target dies!
-`zN,zF,z#` - Next, First, Position target
-`zT <partial name>` - Target with only first few letters
-`zP,zPAUTO/MANUAL` - Setting for party leader target switching
-`zT` - Manual target last leader target call
-`zR` - Check the room for the highest ordered target and target them
-`zLOUD` - Make yourself call as if you were leader but not set to lead
-`zBW <city letter>` - Add complete city to target order
-`zAR (h|m|t|a|c|e|r|all)` - Adds new people in room from that city to list
-`zRESET` - Empty target list
-`zREPORT` - Toggle highlighting target leaving and affliction calling
-`zCITY` - Change default city to add room targets from
-`zLIST` - Display saved lists to use
-`zDELETE <name>` - Delete a preset
-`zSAVE <name>` - Save target order for future
-`zLOAD <name>` - Load only those in realms into order
-`zSET <name>` - Replicate saved target order
-`zSS` - Force save settings
-`zLS` - Force load settings
-`zRE` - Reset QL room gag without clearing target order
