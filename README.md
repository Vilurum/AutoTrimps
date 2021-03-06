# AutoTrimps + genBTC
Automation script for the idle incremental game Trimps, based on the zininzinin script and modified by genBTC (genr8_ on discord)

## Discussion / Discord Channel
Discord is a chat program. Come to talk about AutoTrimps, for help, or suggestions for new features : https://discord.gg/0VbWe0dxB9kIfV2C (same one as zininzinin)

## Script Installation
**Please backup your game via export before and during use to prevent losing your save due to corruption!**

Option 1: Install Tampermonkey (Chrome) or Greasemonkey (Firefox)

Chrome/TamperMonkey Instructions:
- Open the Tampermonkey dashboard and go to utilities – in the URL box paste https://raw.githubusercontent.com/genbtc/AutoTrimps/gh-pages/user.js and import
- Alternatively, paste the contents of `user.js` into a user scrip
- The script should automatically load everytime you go to https://trimps.github.io or the game on Kongregate
- You will know you have the script loaded if you see the Automation and Graphs buttons in the game menu at the bottom

FireFox/GreaseMonkey instructions not available, please write some for us.

Option 2: Via a Bookmark (does not work with Kongregate)
- Create new bookmark and set its target to:
```js
javascript:with(document)(head.appendChild(createElement('script')).src='https://genbtc.github.io/AutoTrimps/AutoTrimps2.js')._
```
- This bookmark button has to be clicked manually after you go to https://trimps.github.io

Option 3: Paste into console

Chrome Instructions
- You can copy and paste the entire contents of AutoTrimps2.js into the Dev Console (F12 in chrome) of the page. (make sure the dropdown box to the left of "Preserve Log" is set to "top" - or "mainFrame (indexKong.html)" for kongregate.

Firefox Instructions
- Push Ctrl+Shift+K to go into console and look for the "Select an iframe" icon, and choose http://trimps.github.io/indexKong.html

Notes:
If you would like to use only the graphs module, replace `AutoTrimps2.js` with `Graphs.js` in the bookmark or your userscript.
Feel free to submit any bugs/suggestions as issues here on github.

## Most recent feature changes by genBTC (up to date as of 8/5/2016): 
- Minutes to Farm Before Spire - force some time to be spent so you can for sure complete Spire (recommended: 3-10 minutes)
- Auto Upgrade Heirlooms - spends ALL your nullifium on the recommended upgrades
- Auto Golden Upgrades = Buys all the Golden Helium, Battle, or Voids when available.
- Always Runs 10 maps for 200% map bonus before attempting Spire (happens after the first death if you don't select "Map At Spire" in regular Trimps settings)
- AutoHeirlooms2 - new algorithm to sort/carry/recycle the Heirlooms (the original had a bug)
- Cap Trainers to a % of Tributes - Only buy a trainer when its cost is less than X% of the cost of a tribute. Prevents from competing with food resources, if you care.
- Run Bionic Before Spire - meant as a one time function (like max tox is) to farm the Bionic Wonderland maps for a LONG time(2 hours-ish) before entering Spire. (not HE/hr efficient)
- Dynamic Prestige: Skip prestiges at the beginning of the run which saves time, and delay them until the end when you need them most and can provide resources from farming too)
- Helium per Hour Portal "Buffer" - now you can customize how much He/Hr is allowed to drop before portaling
- Auto Robo Trimp - activate the MagnetoShriek ability on the bosses every 5 levels starting from the level you specify. (recommended set to 60)

## Feature changes added by genBTC since before 4/27/2016 and Trimps version 3.22:
- Change Genetecist Timer to 10 sec instead of 11sec. (was commonly showing 11.4s because it rounds. that is too much)
- 'Farm on >7 NomStacks': During Nom, take precautions not to get too many stacks. (On Improbability(cell 100). Meant to be used with DisableFarming (otherwise farming would take care of this, but its slower). If Improbability already has 5 NomStacks, stack 30 Anticipation. If the Improbability has >7 NomStacks on it, get +200% dmg from MapBonus. If we still cant kill it, enter Farming mode at 30 stacks, Even with DisableFarming On!')
- Dynamic Siphonology - only when needed based on (Enemyhealth / baseDamage)
Created a new setting in the advanced options. "Dynamic Siphonology".
It will switch to the proper Map-level as soon as the current map is completed.
So you can choose original behavior of always using the lowest level map, 
or the modified behavior, which increases the map level based on your damage.
The old behavior of "no siphonology at all when using DisableFarming" is no longer applied, under any circumstance.
- Skip Gear Level 58&59: Dont Buy Gear during level 58 and 59, wait till level 60, when cost drops down to 10%.
- Cap Equip to 10: Do not level equipment past 10. Similar to LimitEquipment, Helps for early game when the script wants to level your tier2s to 40+, but unlike LimitEquipment, should not impact Zone 60+.
- Delay Armor When needed: Delay buying armor prestige upgrades during Want More Damage or Farming automap-modes.
- Add console debug messages to the map selection/buying/running section.
- Put a numerical status on the "Farming"&"Want more Damage" UI indicator.
This way you can see things progressing, instead of wondering what is going on.
The number pertains to Enemy Health / Base Damage(non-stance). Above 16 means farm. Below 10 means stop farming.
- Farm @ cell 61 (megamining) not 82 (megafarming).
- Farm if enemyHealth divided by baseDamage (in X stance) is between 10 and 16. (Used to be 10 and 15). 
Means it will farm very slightly less.
- Take Map Bonus +%Damage into account for farming decisions. (so you can farm less.)
- Stop from firing all scientists when it reaches the threshhold. (250k farmers)
Farmers will be maintained at the current level, not fired entirely. I
- Add WarpStation Cap (deltaGiga+baseWarp) feature.
Stop making warpstations if we are past the deltagiga + base
warpstations (and no giga upgrade is available). Will also remove the
green highlight around the icon. This will save you metal to use on
weapons,armor, etc.
NOTE: (the cap will ONLY work on incremental buys, it will not come into
effect when the game uses a gigastation and immediately BULK-buys as
many warpstations as it can afford. In this way it can buy over the cap. I think this is actually preferrable.)
- Add an Export/Import/Reset AutoTrimps settings buttons.
- Add a seperate "genBTC's settings UI" button,
- Better Tooltip Help

**Voidmaps and Toxicity changes:**

- Voidmaps: Do voids @ cell 96 Instead of 98. (to prevent overkill). Before, it only applied to Tox runs.
- Voidmap + Max-Tox runs: If we need to do a voidmap and have already more than 1415 stacks, (smallest voidmap is 85 cells)  consider tox-stack finished.
- For normal-tox: Instead of starting the voidmap at 1400 stacks, start at (1500-theVoidmap.size) in case its an 85 cell voidmap.
- Regular Tox-Run:  Avoid another non-unique map cycle due to having the amount of tox stacks we need.
- Max-Tox Run: During a Toxicity + Max Tox run AutoPortal, unset the MaxTox setting from the settings page, so we dont' run 2 Max-Tox's in a row (will go back to normal Tox run).

## Original Version's Previous Recent changes
See changelog at the original version's github page: https://github.com/zininzinin/AutoTrimps


## Colors for upgrades highlights

- Red text on Equip - it's best in its category in terms of stat per resource. This also compares Gyms with Shields.
- Orange text - Upgrade is avaliable and improving this will make the upgrade actually reduce stat in question and it's best in its category in terms of stat per resource.
- Yellow text - Upgrade is avaliable and improving this will make the upgrade actually reduce stat in question
- White border - upgrade is not yet available
- Yellow border - upgrade is available, but not affordable
- Orange border - upgrade is available, affordable, but will actually reduce stat in question
- Red border - you have enough resources to level equip after upgrade to surpass it's current stats.
- Green border on buildings - Best for gems 


## Detailed Code Documentation:

Since javascript is easily human readable, Much can be learned by reading the source code, starting with this knowledge:

The mainLoop() consists of the following subroutine functions, all of which are enable-able/disable-able by their buttons.:
-     workerRatios();         //"Auto Worker Ratios"
-     buyUpgrades();          //"Buy Upgrades"
-     autoGoldenUpgrades();   //"AutoGoldenUpgrades" (genBTC settings area)
-     buyStorage();           //"Buy Storage"
-     buyBuildings();         //"Buy Buildings"
-     buyJobs();              //"Buy Jobs"    
-     manualLabor();          //"Auto Gather/Build"
-     autoMap();              //"Auto Maps"    
-     manageGenes();          //"Genetecist Timer" / "Manage Breed Timer"
-     autoPortal();           //"Auto Portal" (hidden until level 60)
-     autoHeirlooms2();  or  autoHeirlooms(); //"Auto Heirlooms 2" (genBTC settings area) or //"Auto Heirlooms"
-     toggleAutoTrap();       //"Trap Trimps"
-     autoRoboTrimp();        //"AutoRoboTrimp" (genBTC settings area)
-     autoNull();             //"Auto Upgrade Heirlooms" (genBTC settings area)
-     autoLevelEquipment();   //"Buy Armor", "Buy Armor Upgrades", "Buy Weapons","Buy Weapons Upgrades"
-     autoStance();           //"Auto Stance"
-     betterAutoFight();      //"Better Auto Fight"
-     prestigeChanging2();    //"Dynamic Prestige" (genBTC settings area)
-     userscripts();          //Runs any user provided scripts - by copying and pasting a function named userscripts() into the Chrome Dev console. (F12)

Once you have determined the function you wish to examine, CTRL+F to find it and read its code. There are lots of comments. In this way you can determine why AutoTrimps is acting a certain way.