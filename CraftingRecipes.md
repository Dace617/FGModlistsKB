
# Crafting Recipes, Armour/Weapon Stats and You

This will be a brief walkthrough of how to edit Crafting Recipes, and Weapon and Armour stats in Xedit for Skyrim SE. It will assume some basic understanding of Xedit. Hopefully a more indepth Xedit guide will be written in the future

---

## Weapon Stats

Once you have found the mod which contains the weapon you'd like to edit expand the plugin records and find the `Weapon` heading, expanding this will give a list of every weapon that is contained in the mod, be they edits, or brand new items.

![image](https://user-images.githubusercontent.com/38520983/157177824-6a228fce-f4c8-4b32-8c5d-7476beff37e0.png)

For an explanation of the colours used for the records here (They may look slightly different for you depending on your Xedit theme being used) click the legend button in the top right of Xedit, you can leave this legend open while you work to remind yourself if you need to.

**NOTE - Red does not equal bad. Don't panic by the colours you see. check the legend and make sure what you want to happen is happening**

![image](https://user-images.githubusercontent.com/38520983/157177979-2625562e-c680-4b6e-b5c6-f9e63d2c9f20.png)

![image](https://user-images.githubusercontent.com/38520983/157364460-2ea50260-d262-4c20-a207-fa30a9838fad.png)

In this example these Weapon records are 'Masters' noted by the purple text, but are being overrided by a later plugin, noted by the brownish yellow background.

![image](https://user-images.githubusercontent.com/38520983/157178309-5c7621a2-7911-4ada-b9b6-602570d7cfc0.png)

Clicking on a particular record will show you which plugins are affecting the record. In this case it is JSwords.esm (The master mod file, as it's furthest to the left) and [Syn] Engarde Patch.esp, which is a plugin for a Synthesis patcher for Engarde. The Engarde patch is currently winning all conflicts since it is the plugin to the furthest right of the screen here, whatever is listed in the records for this plugin will be what shows in game.

---

#### Making a Plugin

In order to make your patch you'll want to find all the records that you want to change, and add them to your own plugin. Editing the Original plugin file can lead to issues and is generally a bad idea, but it can be done.

![image](https://user-images.githubusercontent.com/38520983/157180378-d1b93a10-4355-4bc7-8ac1-2fd19df51437.png)

As an example we'll be adding the record for `JSwordsDagger` to a plugin and changing it in various ways. You can add as many records to a plugin at once as you like so select all the records you want before hand or do them in groups.

Once you've selected the records, right click on one of your highlighted records and click on `Copy as override (with overwriting) into...`

![image](https://user-images.githubusercontent.com/38520983/157183182-b6f5ec93-2f60-403f-8f89-16dbb7389400.png)

You will then see a dialogue box like this. You'll want to scroll all the way to the bottom of the list and select `<new file>.esp` make sure you select the option with ESL in the ESL column. (There are times you won't want to use an ESL flagged ESP but for this example it's what we will be using)

![image](https://user-images.githubusercontent.com/38520983/157183367-6cb16faf-2d9f-4b7c-b6af-d4a371ea1272.png)

Place a checkmark in the box to the left of it as shown, then click OK.

![image](https://user-images.githubusercontent.com/38520983/157183965-b14829c1-064f-4731-890a-d35638968b66.png)

Next you'll need to give your plugin a name, anything will be fine, I try and be at least a little descriptive about it though

![image](https://user-images.githubusercontent.com/38520983/157184138-a8cfec3e-865a-4871-ae12-a10c944c262d.png)

Your patch will be created at the bottom of your plugin list, with the categories and records you selected. To add more records just select them in Xedit and follow the steps previously noted, except when you get to the step of creating a new plugin, you will want to select your existing patch instead.

![image](https://user-images.githubusercontent.com/38520983/157185602-d61d6839-407d-4385-aeb5-785401264e5b.png)

So now you'll see that your new patch is furthest to the right, so anything you do in the patch will be what wins conflicts (moving the plugins load order can change this so make sure you come back after you move things around and check)

#### Doing the editing

![image](https://user-images.githubusercontent.com/38520983/157185798-680e4b1d-ebd5-433c-9bdd-e670ae302ed8.png)

I'll keep the explanations simple in this write up. We'll focus on a couple of important parts. First is Keywords, these are massively important to a lot of mods and in this case you can see there's a few we need to move `MCT_WeakAgainstArmored` and `MCT_CanCritHigh` are in the Engarde patch but not in our patch. this is because we copied the records from the base mod. not the patch. so we can just drag these from the column they're in over to our patch keeping them in line to add the keywords to our patch.

![image](https://user-images.githubusercontent.com/38520983/157186149-899a02a6-ebbd-4f4f-8dfb-8e7c3a10efda.png)

Depending on where the records you're copying come from you may get a warning like this. in this case we see these Keywords come from Engarde.esp so it needs to be a Master file for our patch to function with these Keywords. so we'll say yes. You won't always get this notification, but if you do you likely want to say yes.

![image](https://user-images.githubusercontent.com/38520983/157186412-9237cff5-48ef-4290-b8d3-fbf49b2a7e65.png)

There we go, now we have the proper keywords winning conflicts and applying in game.

Other important Keywords to check might be the `WeapMaterialxxx` keyword. you'll want to make sure this matches up with the crafting materials and/or the damage range you require for the weapon.

![image](https://user-images.githubusercontent.com/38520983/157347618-a2449b14-4d72-4346-bd86-6c1b1efa64de.png)

Something that may or may not be useful is the Record Flags section. you can see the list of available flags here. these will change depending on what type of record you're editing. For weapons there aren't too many options, the most important will likely be the `Non-Playable` flag. Setting this flag on an item will make it unlootable and invisible in the players inventory, unable to be equipped, useful if there's a super powerful weapon added and you don't want the player using it.

![image](https://user-images.githubusercontent.com/38520983/157348029-d55cfc14-e269-41d5-abbf-da51a49406f9.png)

Next is the meat of editing a weapon record. The `DATA - Game Data` That covers the Value, Weight and Damage of a weapon. Keep in mind the value here is a base amount and will be modified by a lot of other factors in game, so make sure you check in game to make sure it lines up with what you want. It may take a bit of guess work to get this where you want it. 

Weight and Damage should be self explanatory, but you can see here that we have a Synthesis patcher for Engarde that is adjusting the damage, Modifying it after the patcher is doable but you'll need to make sure it doesn't have any adverse effects on the way the mod using the patcher functions, alternatively you can set a sufficient base value and have the patcher edit it again later.

Next is the `DNAM - Data` This covers deeper engine effects such as the animation types used, their speed, the weapons reach. etc. Generally you'll want to leave these alone, but some notable things you can do is change the skill that using the weapon gives experience in, or change how much the weapon staggers enemies.

Lastly you'll see the `CRDT - Critical Data` This covers damage amounts for critical hits, again you'll probably want to leave these alone, but some mods may adjust them, for example if they give a dagger a hefty critical damage multiplier for good sneak attacks.

![image](https://user-images.githubusercontent.com/38520983/157348860-407b448d-3a81-4461-b5ea-5587ae8b3e75.png)

While not relevant in this example this field for `EITM - Object Effect` would be where enchantments are applied to a weapon, if you wanted to change the effect a weapon has or even add one you could do it here. Experiment and see what you can make it do.

---

## Armour Stats

I will work on the assumption you've read the Weapon Stats section and understand the basics of making a patch plugin so I will jump straight in to adjusting armour values, they're very similar to the weapon stats above.

---

#### Editing the Armour Stats

![image](https://user-images.githubusercontent.com/38520983/157349356-0b0dc11b-538f-4d5c-81f5-f3b9e577243b.png)

We'll be editing this CrimsonDarkElfMask armour piece for this example, I've made a patch like I did for the weapon example above and we'll go through the subtle differences for them now.

![image](https://user-images.githubusercontent.com/38520983/157349526-2a51a18b-7c2a-4a05-8a2c-c43850135e6d.png)

You can see the Record Flags are mostly the same as the Weapon Flags

![image](https://user-images.githubusercontent.com/38520983/157349695-c9dc75e4-2f9a-4032-940c-fc53f8935a98.png)

The first unique section for armour is the `BOD2 - Biped Body Template` this section sets Flags for which body slot the armour piece occupies, in this case it's slot 42, the Circlet slot. generally you can leave this alone, but if you're dealing with a lot of modular armour sets you may need to check this to prevent conflicts. It is also possible to select multiple Flags to have an item use multiple slots. For example you could set a helmet to use Slot 30, for the Head slot *and* slot 42, the Circlet slot which would mean you could *only* equip that helmet on it's own, and not wear a circlet at the same time.

Next is the Armor Type, should be straight forward, you can select between Clothing, Light or Heavy armour types.

![image](https://user-images.githubusercontent.com/38520983/157350216-c6b6d371-a6b6-4a4e-9e5a-04eb4038154a.png)

Again we have a Keyword section. Very similar to the weapon keywords but there are a few specific to the armour records. In this case we've got a material keyword, and 3 Jewelery keywords that makes mods looking for these keywords think this item is jewelry, from the ArmorJewlery Keyword, and the VendorItemJewelery keyword, which means vendors that buy and sell jewelery would accept this item. and the JeweleryExpensive keyword, which means it's... well expensive. This last keyword would be important if you were raising or reducing the value of the item. you may want to add or remove this keyword as necessary.

And lastly we have the ClothingCirclet keyword, for a circlet this is fine, if you were modifying the armour type for an item though you might want to change this so that a later mod or the base game looking for this keyword doesn't do strange things like remove it's armour rating etc.

There's no strict rules on an item needing Keywords, but if a mod feature is not functioning correctly on an item Keywords are a good first place to check.

![image](https://user-images.githubusercontent.com/38520983/157350771-2f402adc-acc6-420d-9370-0f05eb426a24.png)

And lastly we have the `DATA - Data` and `DNAM - Armor Rating` section. the Data section determines the items Value and Weight, again these will be adjusted by things in game so do some testing if you make changes to ensure they're where you want them. The Armor Rating section should be self explanatory, you can raise or lower the armour rating here. I like to look at similar items in the base game based on material and armour type to get something consistent but you can effectively set these to whatever you like, just remember that some keywords you use can affect things based on other mods.

---

## Crafting Recipes

ForgottenGlory covered this already in an old document [HERE](https://docs.google.com/document/d/1E1c3e5D_GS_mJrpR7EgupUfq0b1PBHbidf62fBhhEOg/)
I'd recommened reading that first and then coming back to this if you need to.

This section will cover editing crafting recipes for items. I'll add a section for Temper and Breakdown recipes later but they are very similar anyway, so you may be able to figure it out yourself. Again I'll assume you've read the weapon stats section and won't cover the basic instructions twice.

---

![image](https://user-images.githubusercontent.com/38520983/157354957-cbee72d2-f7bd-4112-bb50-d7c24283e50c.png)

Crafting, and Temper recipes are bundled under the Constructible Object Record section (COBJ) I'm going to use the Dark Elf Mask recipe as the example in this section.

![image](https://user-images.githubusercontent.com/38520983/157355220-cb0d6c87-a149-4523-a0b4-3c1431dc27cd.png)

So you can see the armour patch we made now has the Armor record we changed earlier, and the newly added COBJ recipe for the armour piece. Be sure to check it is the actual crafting recipe for the item and not the temper recipe, sometimes if the mod has poor naming of records it can be hard to tell.

![image](https://user-images.githubusercontent.com/38520983/157355375-4fa69133-1a29-4495-ac33-1fca0c7ebf0c.png)

This one is nice and simple. We don't need to worry about flags here.

![image](https://user-images.githubusercontent.com/38520983/157355484-084dde00-b8eb-4e9e-a6ed-79de83475e11.png)

The `Items` section is the important part for a recipe. This section lists which items and how many of them are required to create the item. as you can see here it currently takes 2 leather pieces to make the item. Since this item is Daedric quality from the armour keywords we'll add an Ebony Ingot, a Deadra Heart and reduce the leather by 1. that should cover most things you need to change for a crafting recipe.

![image](https://user-images.githubusercontent.com/38520983/157355643-80e135d1-8f92-4406-8ba9-7d8cc86c8e79.png)

To add an item you'll want to right click in the `Items (sorted)` row and then click 'Add' to add a new item, you can add multiple at once, just remember to set them to actual items and not to leave them as Null Reference (The default when you create new things a lot of the time)

![image](https://user-images.githubusercontent.com/38520983/157355787-6cf34dc8-c3ff-4dfb-a2d1-5ebd99adde29.png)

Now we have 2 new `CNTO - Item` records, we'll change one to Ebony Ingots and another to Deadra Hearts. Since these are base Skyrim items they should show up no matter what as new plugins automatically have Skyrim set as a master. If you wanted DLC items, or items from another mod. you'd need to add them as masters to your patch, like so:

![image](https://user-images.githubusercontent.com/38520983/157355941-3e1d5261-49cb-4336-85c9-0b47f0a606be.png)

Right clicking on your plugin on the left of Xedit and clicking `Add Masters` will bring up a dialogue to choose which plugins to add.

![image](https://user-images.githubusercontent.com/38520983/157356051-d303219c-c094-46fd-98da-0ea24a0a9c6f.png)

In this case I've checked Dawnguard. Once I click OK, the Dawnguard DLC would be added as a master and I could select items added in that DLC to use in crafting recipes. 

**NOTE: DO NOT ADD MERGES AS MASTERS. IF THE MERGE CHANGES YOU CAN BREAK YOUR REFERENCES IN THE PATCH**

![image](https://user-images.githubusercontent.com/38520983/157356412-82593d53-a01e-4c97-8fca-7386ac0ef3d3.png)

Double click on the `Null Reference` we added in the `Item` row. this will bring up a drop down menu to add something. You can begin typing the item name and Xedit should find it for you. If the item you want doesn't show it might have an odd naming scheme, or it's not available because the mod the item is from is not enabled as a master. You can also used Item IDs in this case for a Daedra Heart you could type `003AD5B` in the box and it will select the heart for you when you press enter.

![image](https://user-images.githubusercontent.com/38520983/157356801-6d6e3cd3-8abd-4f71-9adf-7e44dbcebbb3.png)

Notice that doing the same for Ebony Ingot shows no results. Ingots have names formatted like: `IngotEbony` 

![image](https://user-images.githubusercontent.com/38520983/157356957-556d981b-0f40-4825-b3fa-71938992bddf.png)

As you can see this completes correctly. Next we have to set the amount of items the recipe requires.

![image](https://user-images.githubusercontent.com/38520983/157357072-4a05088f-6ceb-4e40-a7bf-ac59db8cee40.png)

You'll notice these items currently have 0 in the `Count` Row. so they don't currently require any of these items. Simply click on the 0 in the `Count` row and change it to 1 (or whatever other amount you like)

![image](https://user-images.githubusercontent.com/38520983/157357215-2fa695c6-b724-41da-b6ed-f68606aaeb81.png)

Doing the same for the existing Leather item now means you'll need to have 1 Daedra Heart, 1 Ebony Ingot and 1 Leather to craft this item. 

![image](https://user-images.githubusercontent.com/38520983/157357527-f81986ce-481d-47ee-b58c-c2d7f96894e6.png)

Next we have some important records, We'll cover Conditions last. as that's a rahter important one. 

The `CNAM - Created Object` record tells the game what you're going to be crafting from this recipe. Generally this should be the item or weapon you want to craft (either the ARMO entry for Armour, or the WEAP record for a Weapon)

The `BANM - Workbench` record tells the game which crafting station is required to craft this item, in this case it's a Tanning Rack, you could change this to a Smithing Forge or even a cookpot if you liked.

The `NAM1 - Created Object Count` tells the game how many of the item to make, for weapons and armour you'd want this to be 1 most of the time. but if you were modifying a recipe to make consumables or arrows etc. then you may want to make this a higher number.

Lastly `Conditions` Conditions are stupidly powerful. I both don't know enough and wouldn't be able to cover everything you can do with these, you'll need to read through them and experiment and see what you can do. I will cover a couple of useful conditions I've found for a couple of things.

![image](https://user-images.githubusercontent.com/38520983/157358425-b1f19938-3154-44db-836f-1efa63db437d.png)

To add a condition (if an item has none) right click in the `Conmditions` row and click `Add`

![image](https://user-images.githubusercontent.com/38520983/157358490-35993403-e692-4a7a-8906-92aafb728860.png)

You'll get a record structured like this. which is currently checking if the Subject is NOT Blocking. This is the default condition when you add one. You'll almost always want to change it, especially for crafting recipes.

Conditions start collapsed, so you'll want to click the + mark next to the `Condition #0` you can see in the screenshot above.

![image](https://user-images.githubusercontent.com/38520983/157358621-8c026646-d95c-4901-a2fd-38f9fe8f7256.png)

You'll be met with this confusing mess. Don't worry we'll go into some specific examples to explain it better hopefully

---

###### What's in a Condition

The `CTDA` record is a break down of the condition and how it works.

![image](https://user-images.githubusercontent.com/38520983/157359032-4d75c5d4-4a66-4309-a0dc-6a1280d61b69.png)

First is the `Type` by default it starts at Equal To. 

Below that is the `Comparison Value` which is currently set to 0. This is what the Type is compared to.

Under that is the `Function` This is what it's checking for. Which is currently `GetWantBlocking` which is Skyrim Engine talk for `Is Blocking`

Further down some lines you can see the `Run On` target record. which is set to Subject which is the Actor that owns the action (useless in most crafting recipe conditions)

If that's confusing lets make our own and see if that clears things up.

---

###### Condition 1 - Hiding a Crafting Recipe

First is a condition you can use to hide a crafting recipe. If you don't want the item crafted but want it placed in the world, hiding the crafting recipe is a good step.

![image](https://user-images.githubusercontent.com/38520983/157360682-884b36a4-7aaf-4aae-b27f-9561b24487de.png)

For this we need to change the `Run On` record. Double click on the Subject entry and you'll get a nice drop down menu, we want to set this to the Player, so we set it to Reference, because we're going to reference the player. This will give us a new entry `Reference` We wnat to change that entry to `PlayerRef` which is the base game reference for the Player. Just typing Player won't give you this result you need the whole input of PlayerRef.

![image](https://user-images.githubusercontent.com/38520983/157359994-bceb7c96-9d54-4051-82a2-b92cf7038e18.png)

Next we need to change the `Function` as checking if the player is blocking isn't too useful for a crafting recipe condition. Double click the `GetWantBlocking` entry and you'll get a nice drop down list. You should read through these as some might make sense just from reading for detailed info better than I could ever write check the [CK Wiki](https://ck.uesp.net/wiki/Condition_Functions)

For our purposes we're going to set this to GetGold. Which will, unsurprisingly, check the `Reference` current gold amount (which we just set to reference the Player).

![image](https://user-images.githubusercontent.com/38520983/157361511-5c52f71a-72ef-43aa-abb0-97eba64fede4.png)

So far we're checking if the `Reference` - The Player, has the `Type` - Equal to, the `Comparison Value` - 0, of the `Function` GetGold. add it all up and this recipe will only show if the Player has exactly 0 Gold on them. But that's something that's possible, so it won't hide the recipe for us. For that we need to change the `Type` to Lesser.

![image](https://user-images.githubusercontent.com/38520983/157361828-d22c4055-4885-46c1-9a58-da36435a980b.png)

So double click the Equal to entry and you'll get a nice drop down list, untick Equal, and tick Lesser. You can have multiple Types selected but in this case one will be plenty.

![image](https://user-images.githubusercontent.com/38520983/157361994-a3a5ba53-3558-48c0-9205-84026af1c0cc.png)

Now once we click out of the drop down menu with Lesser selected you'll see the entry change to Less than - Which means we're checking if the player has *less than 0 Gold* which under 99% of circumstances can't happen. the recipe is functionally hidden. Always test you conditions in game though.

---

*Update:* There is a much easier condition you can use to hide a recipe, it involves setting the Comparison Value to 1, then set the Function value to `IsPS3`. Functionally this will check if the game is being played on the PS3 console, which is actually impossible on the PC version of the game, meaning your recipe will never show. This will work for anything that uses conditions in the game.

---

###### Condtion 2 - Have a Perk Required.

If you would like a crafting recipe to require a perk to be crafted you can use the Function `HasPerk`

![image](https://user-images.githubusercontent.com/38520983/157363358-5dcfbd26-f4d3-4544-868e-f49f40c740d8.png)

Change the Function to HasPerk, and you'll see a new record show up, the `Perk` record. This determines which perk it's going to check.

![image](https://user-images.githubusercontent.com/38520983/157362650-835b37e1-b161-47a4-9afa-1fb3a2c5eff1.png)

Since this is a Deadric level item we'll set it to require Daedric Smithing. Double click the `Perk` record and type DaedricSmithing, to bring up the correct perk we want. You could set it to any perk you like though.

![image](https://user-images.githubusercontent.com/38520983/157363394-9eb0be3b-4d78-465a-98a7-883fde0295e2.png)

So now we're checking if the Subject (The Actor trying to craft the recipe) has a value equal to 0 for DaedricSmithing Perk. since the value is set to 0 however we're actually currently checking if the Subject does *not* have the DeadricSmithing Perk. So we need to change the `Comparison Value` to 1

![image](https://user-images.githubusercontent.com/38520983/157363627-0c4ed089-24ee-4145-9fbe-5fa39bcdfdde.png)

Now we have a condition that will check if the Subject trying to perform the crafting recipe has the DaedricSmithing perk and if it does, the recipe will show up and be craftable.

---

There's plenty more you can do with the conditions system, I don't know enough to explain it completely but the [conditions page](https://ck.uesp.net/wiki/Category:Conditions) of the CK Wiki is invaluable and explains a lot of what I've gone oever (probably better than I can). Give it a read and most of all experiment, see what you can come up with.

---







