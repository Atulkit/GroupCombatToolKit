# GroupCombatToolKit

This package is a robust group combat assistant for Mudlet that should makes organizing or following group combat much easier. It follows and switched targets, can call targets and target orders, add/remove/set target orders, designate leaders and additional target callers, report afflictions given, and more. 

Note - Affliction reporting requires AK to use. NDB functions require svof NBD or Legacy NDB.

# Installation

To install the system: 

1. Download the zip.
2. Unzip it somewhere permanent. Don't delete the unzipped files.
3. Make sure that you're connected to Achaea and logged in.
4. Install `Group Combat Aliases.mpackage`, `Group Combat Scripts.mpackage`, `Group Combat Triggers.mpackage` in the Package Manager.
5. QQ and Restart Mudlet. System is ready to use!

# Basic Setup

## Targeting Alias and Functions
### NOTE: This package comes with a target alias and target function script. If you have your own be sure to disable your own or replace the ones in this package**
Disable/Replace:
- `targeting alias` in aliases folder
- `targeting funtion` in scripts folder
- Search for 'targeting(target)' and replace with your own target function or alias

## Affliction Calling Setup
This requires the AK package to run. `Group Combat Scripts` should now automatically update the `ocscore edit functions` in the AK scripts. If it is doesn't then:
- Navigate to `oscore edit functions` in Scripts > AK > AK Opponent Tracking > Multiuse Functions > `oscore edit functions`
- Immediately under the beginning of the function `function OppGainedAff(aff,source)` paste the following code
```
  -- Party Aff Tracking for Group Combat (needs tweaking)
  if isActive("Group Combat", "trigger") == 1 then
  local do_not_report = {
    -- "paralysis",
    "",
    " "
  }

  if gmcp.Char.Status.class ~= "Alchemist" then
    table.insert(do_not_report, "impatience")
  end
  
  local raff = aff:lower()
  raff = string.split(raff, " ")
  for _, v in ipairs(raff) do
    if (not table.contains(do_not_report, v) and not table.contains(gc.affs_to_report, v)) then
      table.insert(gc.affs_to_report, v)
    end
  end
 end
  --normal OppGainedAff script below
```
- Save the changes and you are ready to call afflictions to the party.
### NOTE: Double check to see that there are not TWO `oscore edit functions` in your scripts. There should only be one, but if there are two then the one with this code  is only one you need with this update.



## Setting up to follow party targets
These steps are the quick way to set up the system to follow party target calls.

1. `zOn` - Turns the system on.
2. `zL <player>` - Designate group leader. You will follow their targets, auto add their target list if they call it.
3. `zA` - Toggle on 'auto' target switching.
4. `zP` - Toggle on 'auto' target switching to follow leaders targets.
5. `zSTAT` - Shows the the system status and what is toggled on/off. Toggles are clickable.
6.  Optional: `zADD <enemy>` - Will add enemy to target list and auto enemy them.
7.  Optional: `zREPORT` - Will toggle on/off target movement, afflictions, and wall callouts.
8.  Optional: `zLOUD` - Will echo your target switches to the party if not leading (ONLY USE TO AID IN TARGET CALLING).

- `zR` - Switches to first target in the target order [THAT IS IN THE ROOM].
- `zN` - Switch to next target in the order.
- `zF` - Switch to first target in order.
- `zT` - Switch to last party target called.


# To Lead Groups

To set up the system to lead. Follow the above steps, plus:

1. `zL <ME>` - Sets you as the group leader. You will echo all target switches to the party. (`zLOUD` is does not need to be toggled on.)
2. `zBW <city name or first letter>` - Auto adds everyone from a city to target list.
3. `zCITY <city name of first letter>` - Sets primary target city.
4. `zADD <enemy> / zMULTI <enemy> <enemy> <enemy>` - Manually adds enemy/enemies to target list.
   (Alternative) `zBW <city>` - Adds all online members of the target city to the target list.
6. `zENEMY` - Enemies everyone in the target list (if not done automatically).
7. `zORDER` - Show target list and set target order.
8. `zF` - Set and call first target to party.
9. `zREPORT` - Toggle on reporting movement, afflictions, and walls to party.
10. `zGROUP` - Reports information from `zSTAT` to party.





## All Aliases

List of aliases to toggle things on and set up the system. `zHELP` or `zHELP2` will give the full and up to date list in game.

- `zON/OFF`           - Raid system all on or off
- `zSTAT`             - Raid system info
- `zHELPS`            - Display all commands
- `zL <name or 'Me'>` - Set leader
- `zORDER`            - List target order for reordering
- `zCALL(F)`          - Call target order, F forces announce
- `zC(F)`             - Call current target, F forces announce
- `zGROUP`            - Report leaders, target, target list, callers, and more to party
- `zADD <name (#)>`   - Add enemy to list at end or into a spot
- `zMULTI <name>, <name>, <name>, etc` - Add several enemies at once
- `zREMOVE <name>`    - Remove enemy from list
- `zSWAP <name> <#>`  - Manual reordering person to a position
- `zENEMY`            - Enemies the target list
- `zAUTO`             - Enable setting enemies automatically
- `zA`                - Turn on target switching. If your target dies it will auto switch for you!
- `zN,zF,z#`          - Next, First, Position target
- `zT <partial name>` - Target with only first few letters
- `zP,zPAUTO/MANUAL`  - Setting for party leader target switching. Will swap to leaders targets as they call them.
- `zT`                - Manual target last leader target call
- `zR`                - Check the room for the highest ordered target and target them
- `zLOUD`             - Make yourself call as if you were leader but not set to lead
- `zBW <city letter>` - Add complete city to target order
- `zAR (h|m|t|a|c|e|r|all)` - Adds new people in room from that city to list
- `zRESET`            - Empty target list
- `zREPORT`           - Toggle on/off reporting target movement, affliction, and wall callouts all at once
- `zMOVE`             - Toggle reporting target movement
- `zAFFS`             - Toggle reporting afflictions
- `zWALLS`            - Toggle highlighting walls
- `zCITY`             - Change default city to add room targets from
- `zLIST`             - Display saved lists to use
- `zDELETE <name>`    - Delete a preset
- `zSAVE <name>`      - Save target order for future
- `zLOAD <name>`      - Load only those in realms into order
- `zSET <name>`       - Replicate saved target order
- `zSS`               - Force save settings
- `zLS`               - Force load settings
- `zRE`               - Reset QL room gag without clearing target order

# Miscellaneous

## Bombs
Added a basic alias for throwing bombs - `^b(c|w|d|b|o) (.+)$`
The folder is locked by default and must be activated manually to use.

The alias will get/wield/throwing bombs (or orbsigils) and triggers to report when you successfully or unsuccessfully (hit a wall) throw a bomb in a direction. If you wield weapons/shields please tailor the alias to fit your combat kit.

## Walls
When active (`zWALLS`) it will call out all walls you encounter to the party.

## Lyre and Shields

Folder in triggers. When enabled it will announce when your target has shielded or used the lyre defense.
- Olivebranch to be added soon.

## Instant Kills Reporting

Folder in Triggers. When enabled it will announce when your target has activated an instant kill.
- Only Incandescence and Deliverance have been added so far.


