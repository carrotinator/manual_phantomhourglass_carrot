# Archipelago Manual for The Legend of Zelda: Phantom Hourglass

## Is it functional?

It is playable, and only *slightly* more annoying than playing a randomizer with a manual tracker. It relies on the DeSmuMe cheat list to freeze and change your inventory directly in memory. To set the right values, I've got a [spreadsheet](https://docs.google.com/spreadsheets/d/1vmAcfJQFSD-9Eqkp-Lbiaa-RWCv5VpM21hLvvyDSgFg/edit?usp=sharing) that can calculate what to copy paste in for each memory address. There is kinda a lot of setup involved, but once that’s done it’s not so bad.  It could probably be streamlined with a bit of lua scripting, but I haven’t looked into that yet.

## Settings

Currently, it is hard glitched logic and keysanity; chests and most item acquisitions as checks as well as tree bonks and dig patches that give 20 rupees or more.  
Shops, fishing and salvaging are currently not implemented. Neither are treasure, treasure charts or ship parts (although full ship sets are!). But probably will be soon.
Settings are currently not supported in the yaml, to be added soon.

## Setup

1. Get the game running on an emulator with memory editing tools and set up archipelago with manual.
   - I’m using DeSmuMe 0.9.13, Archipelago Launcher 0.6.1 and manual_stable_20241119.apworld. The rest of the  instructions will be for those.
2. In DeSmuMe, set a hotkey for the Cheats List, and open it.
   - This will be where you do all your inventory editing when you get items and set introductory flags. It will also prevent picking up pesky vanilla items when you get them. You’ll be in here after almost every progression item.
3. Set up individual, **internal cheat codes** for the inventory, and name them appropriately. Note that they are different sizes. Click the enable button for each, they can stay on the rest of the game.
   - These will be what you edit every time you get progression. The starting value is an integer. By keeping them enabled, it prevents vanilla items from being picked up.

| **Address (hex)** | **Starting Value (dec)**     | **Description**                                | **Size** |
|-------------|------------------------------|------------------------------------------------|----------|
| 21BA604     | 4                            | Items                                          | 2 bytes  |
| 021BA606    | 0                            | Spirits and Upgrades                           | 2 bytes  |
| 021BA608    | 0                            | Collection Screen and Sea Charts               | 2 bytes  |
| 021BA348    | 12                           | Max Health, Heart containers * 4               | 2 bytes  |
| 021BA4E8    | 36000                        | Phantom Hourglass max timer (1 minute is 3600) | 4 bytes  |
| 021BA590    | 0                            | Quiver Upgrades                                | 2 bytes  |
| 021BA592    | 0                            | Bomb Bag Upgrades                              | 2 bytes  |
| 021BA594    | 0                            | Bombchu Bag Upgrades                           | 2 bytes  |
| 021BA501    | 0                            | Power Gem Count                                | 1 byte   |
| 021BA502    | 0                            | Wisdom Gem Count                               | 1 byte   |
| 021BA500    | 0                            | Courage Gem Count                              | 1 byte   |
| 021BA4FE    | 0                            | Rupee Count                                    | 2 bytes  |

4. For starting flags, add the following, version dependent (i’ve done most of my testing on US) action replay code. Do not enable yet.
    - This tries to remove as many cutscenes as possible, allows for sequence breaks without softlocking and opens up islands a bit. It’s not perfect, and it doesn’t affect scene flags. A planned future part of the project is to create a starting save file that has already warped around the world and triggered a bunch of scene flag dialogue, but the codes will work from a fresh savefile. For more details on what it includes, see the section on checks.

**US:**
```
620EE3EC 00000000
021B553C 033E3CEF
021B5540 AB4090E7
021B5544 FC27FFFF
021B5548 0204003B
021B554C 04124FD9
021B5550 EA45FE02
021B5554 03080047
021B5558 E010E034
021B555C 050FD94E
021B5560 1FA00031
021B5564 4800CC26
021B5568 4018001F
021B556C 00000070
021BA67C 00010001
021BA684 000A0001
021BA688 00000001
021BA680 0014000A
D2000000 00000000
```
**EU:**
```
620EE3EC 00000000
021B557C 033E3CEF
021B5580 AB40B0E7
021B5584 FC27FFFF
021B5588 0204003B
021B558C 04124FD9
021B5590 EA05FE02
021B5594 03080047
021B5598 E010E034
021B559C 050FF94E
021B55A0 1FA00031
021B55A4 4800CC26
021B55A8 4018001F
021B55AC 00000070
021BA67C 00010001
021BA684 000A0001
021BA688 00000001
021BA680 0014000A
D2000000 00000000
```
5. Add a few more flags as Internal cheat codes. These are for items stored amongst the regular flags, like trade quest items. They do not want to stay enabled, only toggled at the appropriate moment. Also version dependant

| **Address US** | **Address EU** | **Value (to toggle)**                                             | **Description**                                                              | **Size** |
|----------------|----------------|-------------------------------------------------------------------|------------------------------------------------------------------------------|----------|
| 021B5542       | 021B5582       | varies                                                            | Cannon and Regal Necklace                                                    | 1 Byte   |
| 021B554A       | 021B558A       | varies                                                            | Beedle vouchers (not implemented)                                            | 1 Byte   |
| 021B554B       | 021B558B       | 6                                                                 | Courage Crest (and metals i guess but they don’t matter in game, just in AP) | 1 Byte   |
| 021B554F       | 021B558C       | 12                                                                | Prize Postcard (not implemented)                                             | 1 Byte   |
| 021B5550       | 021B5590       | varies                                                            | Trade quest items                                                            | 1 Byte   |
| 021B5552       | 021B5592       | varies                                                            | Spawn phantoms on TotOK B13, remove ice from IoF, Phantom sword blade        | 1 Byte   |
| 021B5562       | 021B55A2       | Varies, currently the action replay code makes you start with all | Cyclone Slate Glyphs                                                         | 2 bytes  |
| 021FA064       | 021FA064       | 512                                                               | Boat Speed                                                                   | 2 bytes  |

6. Now you are ready to start the game. Enter a new save file and skip the opening cutscene (or load one of my nice savefiles once i make it)
7. Open the cheat menu, and toggle the action replay code. You have to save in the cheat list with it on for it to take effect, which will cause lag, and then save again with it off.
8. Save and quit. There is a chance that the save file gets corrupted. If so try again, it usually works 2nd try for me.
    - This seems to be the only point of save instability, I’ve never had files corrupt during testing at other points
9. Check that you can access the item menu! Set items (0x21BA604) to 0 and you’re ready to play!
    - Item menu enables after a save and quit with boomerang, so to enable it i made you start with boomerang. From here on out you can toggle on and off all items at any time. With 3 exceptions...
10. Place manual_phantomhourglass_carrot.apworld in custom_worlds, generate your archipelago, host a server and connect to it with the manual client. You are now ready to play!

## Calculating item values
I made a [spreadsheet](https://docs.google.com/spreadsheets/d/1vmAcfJQFSD-9Eqkp-Lbiaa-RWCv5VpM21hLvvyDSgFg/edit?usp=sharing) for calculating the value for each item address, copy it and you can use it! Set the count column under input to as many of the item you’ve gotten, and copy the decimal value in output to its corresponding address in the cheat list menu.

## Further resources

The [github wiki](https://github.com/carrotinator/manual_phantomhourglass_carrot.wiki.git) for this repository has a bunch of info on basically every item and check. Go there if you're stuck or just want to be prepared.  
There's a [development spreadsheet](https://docs.google.com/spreadsheets/d/1_4Bo1IxLDtaytXj7SQFIAtt9QbPfYDTGZ-CDNf0DXJA/edit?gid=0#gid=0) listing a bunch of internal game values. This has been the foundation for all the memory editing and a huge help.
The proper [phantom hourglass randomizer](https://github.com/phst-randomizer/ph-randomizer/tree/main) in development. Currently not functional
The [Phantom Hourglass decomp project](https://github.com/zeldaret/ph)
The [Phantom Hourglass and Spirit tracks Speedrunner discord](https://discord.gg/T44RaUBFP9)
The [Archipelago manual discord](https://discord.gg/T5bcsVHByx)
[Archipelago](https://archipelago.gg/)
