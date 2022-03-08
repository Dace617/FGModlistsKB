
# Crafting Recipes and Armour/Weapon Stats and You

This will be a brief walkthrough of how to edit Crafting Recipes, and Weapon and Armour stats in Xedit for Skyrim SE. It will assume some basica understanding of Xedit. Hopefully a more indepth Xedit guide will be written in the future

---

## Weapon Stats

Once you have found the mod which contains the weapon you'd like to edit expand the plugin records and find the `Weapon` heading, expanding this will give a list of every weapon that is contained in the mod, be they edits, or brand new items.

![image](https://user-images.githubusercontent.com/38520983/157177824-6a228fce-f4c8-4b32-8c5d-7476beff37e0.png)

For an explanation of the colours used for the records here (They may look slightly different for you depending on your Xedit theme being used) click the legend button in the top right of Xedit, you can leave this legend open while you work to remind yourself if you need to.

![image](https://user-images.githubusercontent.com/38520983/157177979-2625562e-c680-4b6e-b5c6-f9e63d2c9f20.png)

In this example these Weapon records are 'Masters' noted by the purple text, but are being overrided by a later plugin, noted by the brownish yellow background.

![image](https://user-images.githubusercontent.com/38520983/157178309-5c7621a2-7911-4ada-b9b6-602570d7cfc0.png)

Clicking on a particular record will show you which plugins are affecting the record. In this case it is JSwords.esm (The master mod file, as it's furthest to the left) and [Syn] Engarde Patch.esp, which is a plugin for a Synthesis patcher for Engarde. The Engarde patch is currently winning all conflicts since it is the plugin to the furthest right of the screen here, whatever is listed in the records for this plugin will be what shows in game.

---

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

![image](https://user-images.githubusercontent.com/38520983/157185798-680e4b1d-ebd5-433c-9bdd-e670ae302ed8.png)

I'll keep the explanations simple in this write up. We'll focus on a couple of important parts. First is Keywords, these are massively important to a lot of mods and in this case you can see there's a few we need to move `MCT_WeakAgainstArmored` and `MCT_CanCritHigh` are in the Engarde patch but not in our patch. this is because we copied the records from the base mod. not the patch. so we can just drag these from the column they're in over to our patch keeping them in line to add the keywords to our patch.

![image](https://user-images.githubusercontent.com/38520983/157186149-899a02a6-ebbd-4f4f-8dfb-8e7c3a10efda.png)

Depending on where the records you're copying come from you may get a warning like this. in this case we see these Keywords come from Engarde.esp so it needs to be a Master file for our patch to function with these Keywords. so we'll say yes. You won't always get this notification, but if you do you likely want to say yes.

![image](https://user-images.githubusercontent.com/38520983/157186412-9237cff5-48ef-4290-b8d3-fbf49b2a7e65.png)

There we go, now we have the proper keywords winning conflicts and applying in game.

Other important Keywords to check might be the `WeapMaterialxxx` keyword. you'll want to make sure this matches up with the crafting materials and/or the damage range you require for the weapon.


