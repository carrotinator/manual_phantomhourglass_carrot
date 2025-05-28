# Checks

Most checks are kept as vanilla as possible, and almost always directly correlate to getting something. Some checks however don’t exist due to flag shenanigans, some have unintuitive logic requirements and some hard glitch logic things are kinda obscure. Also those pesky items that don’t work immediately. So I’ll go island by island and say what to do and what to expect, and if there are silly softlocks, what to avoid.

## Mercay Island

- The intro is skipped, the bridge is repaired.
- The sword chest will put a fully functional sword on link when you open it, but it will disappear with a save and quit. If starting from a fresh save file you might as well check the sword chest before save and quitting for file stability
- Clearing the rocks from the cuckoo guy is a check
- Bonking trees with guaranteed rupees are checks
- Oshus is kinda buggy at the moment. Certain events can put him in a state where he will give a force gem. The only one i confirmed so far is getting the phantom blade from Zauz. So for now that is Oshus’ logic.
- Setting out to sea logically requires the SW sea chart, but you can just go if you want to. Those water are untested.
- Opening the shipyard requires beating Temple of Flames.
- Opening the treasure teller requires getting the Courage Crest from TotOK B6
- Freedle gives an item. In vanilla it’s after getting the SE sea chart, but it’s actually tied to opening it’s chest in TotOK, and it felt better to have freedle open from the start.

## TotOK

- **There are softlocks in TotOK, save before entering**
- Phantom Hourglass is a check. If you don’t get it and use the warp from bellum, **it softlocks**.
- See the item description of the Phantom Hourglass and sand of hours for more details.
- Sand and hearts are not considered in logic, and can create interesting challenges.
- Heart pots respawn infinitely on changing floor. Abuse it.
- Swift phantoms spawn immediately.
- Killing phantoms is in logic if you can stun them and there is a hole to push them into. Grappling hook is also enough.
- Key logic for the temple assumes you start with however many keys you’ve gotten
  - The midway does not reset keys, like time, you lose as many as it took to get there.
  - The door on 1F permanently uses a key
- F1
  - Linebeck will respawn and give you a free key (that is a check!) until you grab the SW sea chart chest.
  - The locked door eats a key, and that is forever gone from your keycount
  - The empty chest is a check even if you get its contents from linebeck
- B1
  - **Entering B1 without all 3 fairies in inventory softlocks the cutscene of the phantoms spawning.**
  - My best fix is to quickly set fairy count 0x021BA606 to 112dec before setting back to what it should be
  - This would be fixed by setting up a save file.
  - This is a good place to practice killing phantoms with weird equipment.
  - Also a nice floor to get used to starting with keys, and running straight to the end.
- B2
  - Hammer can hit bombchu switch
  - The red phantom will pick up the key if it chases you to the safe zone opposite, and will drop the key if a pot is thrown at it.
  - There are creative ways to get past the second fire
- B3
  - Force gems are randomized, their chests are checks. Don’t use the gems without finding them first.
  - The key door here is interesting logically
- B4
  - You can hit the switch through the gust with a pot.
  - Hammer can hit bombchu switch, and key spike switch
- B5
  - Both paths can be done on the same key logically since keys respawn and you can do multiple runs
  - There are interesting ways to kill the bubbles.
- B6
  - Both Crests are open from the start. If you can reach B6 you can activate the midpoint.
  - Since the SW sea chart is bugged, you can’t do the courage crest puzzle. Set 0x021B554C to 221dec (US) to artificially give it to you, and let you out.
- B7
  - Killing phantoms on a tight time limit on this floor is fun
  - Crystals are like force gems, you need ‘em to use ‘em.
- B13
  - Phantoms don’t spawn by default. If you want that set the 64 bit of 0x021B5553 (US).
  - See Metals, Phantom Door and Goal under items for more.
- Bellum
  - See Metals, Phantom Door and Goal under items for more.
