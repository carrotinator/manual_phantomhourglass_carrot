# Items

Some items are a bit quirky, so here are the details to look up when you run into problems.

## Sword and shield

- The sword and shield requires a save and quit after adding to your inventory for their models to load and be usable. Same goes for unloading, after opening the sword chest for example. 
- The sword is considered progressive, and has 2 stages, 2nd one being the phantom sword. Setting the sword value in the spreadsheet will calculate the values for you. The starting sword is in the items address and the phantom sword in the collection screen address.
- I’ve found 1 (1) place in logic where the shield can be required progression. Hope someone has to figure it out~

## Usable Items

- The items menu won’t show up until you’ve saved and quit with boomerang in your inventory. After that you can remove the boomerang and everything will work.
- When picking up capacity upgrades, they won’t auto refill. If you want to go the distance, bomb count is 0x021BA680, arrow count 0x021BA682 and bombchu count 0x021BA686, all 2 bytes. The flag setting action replay code sets your ammo count to their default.
- The capacity upgrade memory values are just the number of upgrades, starting at 0.
- I have a graphical issue with digging, it’s not updating the tiles. Not related to the manual.
- This manual is glitched logic, and a lot of that is hammer clips. If you see a switch on the other side of a wall, your hammer can hit it.

## Sea Charts

- The SW sea chart is bugged and can’t be opened from the inventory for getting the courage crest on TotOK B6 there is a fix thingy
- The game crashes or softlocks if you click on an island map in the SW quadrant, and then click back.
- You can leave Mercay without the SW sea chart, but logic expects you to find it first
- A bunch of checks that in the vanilla game are tied to getting sea charts are actually tied to opening their chests in TotOK. Most of these flags are set at the beginning.
  - The item from Freedle and the 3rd and 4th map on Harrow island are examples.

## Heart Containers

- Maximum health is set as a multiple of 4
- If you decide to start with lower health than 3 containers (12) the first hit will put link at that value, cause link spawns with 3 health
- Setting max health does not refill your hearts.

## The Phantom Hourglass and Sand of Hours

- The phantom hourglass is a starting item. This is because if you pick up a time refill without the hourglass, you get infinite time, and that’s no fun.
  - Sure this does require getting to at least B2 (the pot by the bombchu switch) without curse protection, which is a challenge on 3 hearts, but still broken.
- To compensate, you can set your starting time and sand increment to whatever you wish. I like to start with 30 seconds and make every upgrade add whole minutes. 
- This is a manual, decide what works best for you!

## Fairies and Gems

- Fairies are progressive, and one of each are in the boss item pool. Each progressive stage levels them up, and you can switch between them as usual in the collection screen.
- Fairy upgrades are considered in logic, and I’m looking for more places where they’re useful to add to logic.
- Gems only matter for the checks at spirit island, which are bugged anyway at the moment. Therefore I don't usually bother updating my gems in game.

## Rupees, Treasure, Shops, Money

- Shops have yet to be made into checks, and rupees are not in logic in any capacity.
- I haven’t figured out a non-tedious way to both allow for passive rupee drops and getting rupees as checks, while also blocking rupees picked up from vanilla locations.
- Treasure is likewise not an item archipelago knows about.

## Cannon and Regal Necklace

- Being able to shoot the cannon has nothing to do with the inventory item, it has to do with setting the flag of having bought the cannon.
- That means that buying the cannon check adds a cannon to your ship that you want to remove.
- The cannon shares its address with a bunch of really important story flags, like lowering the water on isle of ruins or removing the fog and despawning the ghost ship. 
  - The cannon is also the 1 bit of its address, so it’s not too bad if you know what the current value is.
  - DeSmuMe has a ram watch function that’s good for this. 
  - Then add one to gain 1 cannon, and subtract 1 to remove pesky vanilla cannon.
- The regal necklace also shares this byte. It is the 8 bit, so add 8 to gain, subtract 8 to remove.
- The regal necklace is also the third item that doesn’t work without a save and quit.
  - However, it’s impossible to have access to Isle of Ruins without also having access to vanilla regal necklace. You can make a stop at Isle of the dead first and let the vanilla game set up everything for you.

## Courage Crest and Salvage

- Salvaging is not implemented nor are treasure maps
- Getting the crest of courage on your map in TotOK B6 is, and it unlocks a bunch of checks in other ways
  - Buying Salvage arm from Eddo and buying map from yellow guy on Mercay are examples.

## Trade Quest Items

—do some more testing—

## Frogs and Glyphs

- Glyphs are items and are logically accounted for.
- However, during testing it is real nice QoL to use them from the start, and as of version alpha 0.1.2, Cyclone Slate is a default starting item.
- Glyphs are therefore included in the flag-setting action replay code. It is up to you whether you use them before you unlock their items or not.
  - You can also manually disable them, see the spreadsheet for their memory locations.
- Frogs are also checks, they only require cannon.

## Pure Metals, Phantom Door and Goal

- The goal is, in logic, to collect the three pure metals that are random dungeon rewards, which then allow you access up Bellum’s staircase.
- This is purely a manual restriction, nothing will stop you in game.
- Metals do have a slot in memory and on the collection screen, but are overwritten by the phantom sword and blade. Therefore I prefer to let archipelago track them.
- Spawning the phantoms on B13 to open the door requires setting the 64 bit of 0x021B5553 (US), or talking to Oshus with the phantom blade in your inventory (that’s what sets it). Setting this bit blocks the check from Zauz (who vanilla gives you the phantom blade).
  - Phantom blade is, for the record, not an item in the rando yet.
- Some ways of doing the endgame:
  - Phantom door is always available, and as soon as you can reach B13 you can activate the warp point for use once you have the metals
  - Spawning the phantoms require the metals, and you end with a victory stomp down to the depths of the dungeon
  - Getting the metals spawns the warp to bellum (0x021B5559 bit 4 US) and you don’t need any of this nonsense.
  - Getting the metals spawns ghost ship wreckage in overworld and you can skip straight to bellumbeck (i haven’t found the address yet though)
- Also I should add that ghost ship ghost key and the TotOK B12 NE Sea Chart Chest are eligable locations for the metals along with beating the 6 regular dungeons.

## Ship variants

- I added the full complete ship designs as items to the pool! The fancier the ship, the more health your ship has.
- You choose where you get 1 free ship switch when found, or if you need to unlock the shipyard first. These are purely for fun.
- To set your ship, toggle the following action replay code, where the first bits (in example all set to 5) are set to the ship id you got. The ids are included in the item name in archipelago!
```
620EE3EC 00000000
021BA504 00000005
021BA508 00000005
021BA50C 00000005
021BA510 00000005
021BA514 00000005
021BA518 00000005
021BA51C 00000005
021BA520 00000005
D2000000 00000000
```
- Might add random starting ship soon~
- Also. Boat speed is a thing you can set. It is fun. You never stop when it’s on. 0x021FA064. Any value you like

## Keys and key logic

- Currently keysanity is the only option. This includes small keys, boss keys, force gems and shaped crystals.
- I play as if I can’t use them unless I have their item in archipelago.
- As with most key logic, you need as many small keys as doors you can reach before any of them are in logic.
- You can save scum keys i guess, still not in logic.
- If you need to get a key you can’t get the vanilla way, there are action replay codes for the various dungeons [here](https://web.archive.org/web/20071019214730/http://kodewerx.net/forum/viewtopic.php?f=19&t=4440).
- If you need to enter a room requiring a throwable key, I usually edit my floor and room id to put me through the appropriate entrance. In TotOK every room down adds 1 to the floor value
  - Stage: 0x021B2E54 (4 bytes)
  - Room: 0x021B2E58 (4 bytes)
  - Floor: 0x021B2E66 (1 byte)
  - Entrance: 0x021B2E67 (1 byte)
- TotOK is special cause all  keys respawn except the first. I (and logic) treat the key counter as starting keys, that save after the midway point. A key that has been used on 1F is gone forever.
