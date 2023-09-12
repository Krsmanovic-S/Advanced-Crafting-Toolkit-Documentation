Welcome to the ACT Plugin! Here we will go over some basic stuff about the plugin and I'll make a couple of sections about how to do certain stuff and how you can expand upon these systems. Without further ado, let's first take a look at what classes interact with which and what is the general pipeline of the plugin:

![Crafting System Documentation](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/ce59771e-c320-46b7-b094-a771ae8e7725)

___

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [How to Install the Plugin](#how-to-install-the-plugin)
- [Implementing Input & Integrating Your Character](#implementing-input--integrating-your-character)
- [Plugin How-To's](#plugin-how-tos)
  - [How To Add More Items](#how-to-add-new-items)
  - [How To Customize the Inventory](#how-to-customize-the-inventory)
  - [How To Customize the Crafting Component](#how-to-customize-the-crafting-component)
  - [How To Customize Shops](#how-to-customize-shops)
  - [How To Customize Widgets](#how-to-customize-widgets)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

___

# How to Install the Plugin

When you purchase the plugin, you can install it for an engine version inside the Epic Games Launcher.

- Once doing that, the plugin will appear in the following path on your PC -> **Local Disc:\Where You Installed Unreal Engine\UE Version\Plugins\AdvancedCraftingToolkit**

Once you find the plugin, you should make a folder called 'Plugins' in your project directory.

Paste my plugin into that folder and run your project. I suggest doing it like thus rather than just installing in engine as if you want to modify something in the code you can without worrying that something gets messed up. You will always have a backup of the original files with easy access to them!

___

# First Steps

Let's start off by adding the **Inventory Component** and the **Crafting Component** to your Player Actor or any other one that wishes to utilize these components:

![ACT_Components](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/77689453-ebb4-468b-837f-801895ac1b06)

After we successfully added these components, it is time to customize them to your liking. We go over the customization in the *'How To'* section below.

# Implementing Input & Integrating the Widgets

As far as the inputs go, you can copy over the inputs from the character I provided directly into your own:

![Input](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/dc74ead0-95fb-41bd-b2c8-992d0b23d06f)

After that add the widgets located in **WGB_HUD** to your own HUD if you have it and copy over the **On Drop** method into your HUD.

![image](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/428afcea-0021-4ddb-bf11-0cd9107095fe)

- This method is only required if you want to drop items by dragging them to an empty space in the HUD, if you don't want this feel free to skip that part

I'd also suggest creating a variable for your **Player Character/Pawn** inside the **BP_ItemUseDefinitions** as this gives you easy access to modify his stats/other things

This concludes the first part of the integration, now we move on to some customization and you are good to go 😄

___

# Plugin How-To's

In this section I will clarify a bit on how to use the plugin and what can you customize. Without further ado, let's begin:

## How To Add New Items

Adding Items is as easy as adding a new row in the **Item Data Table**:

![ACT_Item](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/83b464d4-f8fc-465c-a2d4-b14ce3131739)

After adding a new row, just fill out the information below and you are good to go.

## How To Customize the Inventory

First add the '**Inventory**' component to any actor you want to use it one. Once added, select it in blueprints and head over to the details panel:

![Inventory Customization](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/2dbb8d81-ee3b-4bf2-abd2-ba5a58f31aaf)

Here you can customize all the options regarding the inventory. You should hover over the variables in the blueprint to see what they exactly do. Keep in mind that your Player **must have** this component in order for the UI to work.

## How To Customize the Crafting Component

Add the '**Crafting**' component to whichever actor you want to in blueprints. After adding it, click on it and go to the details panel:

![Crafting Customization](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/2b8c347a-0c48-42b2-970c-a2d5832f25ef)

Same as above for the inventory, here is where you can customize how you want your crafting to be. Actors that should have this component are the Player and the Crafting Stations. This component, like the inventory, can be customized per instance as well, you do not need to have the same settings on every single component! Different components can have different recipes as well!

- for crafting recipes, make sure that you tick the '**IsCraftable**' boolean in the '**ItemDataTable**' for any item you wish to use for crafting

## How To Customize Shops

Shop Actors do not have any components related to them. The way you edit what is in each shop is by placing this actor into the world and then, after clicking on it, editing the available items for sale like so:

![Shop Customization](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/e5e59a9a-66ae-4e2b-9ee0-1bd1bf13b9aa)

- make sure to input the '**Row Name**' of the item you want, not the actual name or it will not show up, the same logic applies for adding 'Default Items' to the Inventory and adding recipes to Crafting Components

- Shops use the '**Item Value**' part in the '**ItemDataTable**' to determine how much to sell for and what to give the Player upon selling (sell value is set to 1/2 of the total price by default)

If you would like to make a character vendor, you can copy over the blueprint node logic in the'**BP Shop Actor**'. Shops do not use C++ logic, the only relevant thing for them is an array of Item Structs that sybolizes their sellable items.

## How To Customize Widgets

For the inventory, the main widget is the '**WGB Inventory**'. You should not customize anything here, but rather if you want to change how the inventory looks, change the slot image of the '**WGB Inventory Slot**' and how the '**WGB Splitting Slider**' looks like. The part that goes on the HUD (WGB Player Inventory) should be customized to your liking. The equipment screen is optional, however be aware that if you want to add more equipment slots to it, you will need to modify the '**Initialize Equipment Slots**' function in the Player Inventory widget to accomodate the new slot or it won't be included.

For crafting, the main widget is the '**WGB Crafting Screen**'. You can modify this widget to style it in whatever way you want and you can also edit individual parts of it in their respective widgets (recipes, filters etc..). Shops are very simple to edit, you just need to change the look of the '**WGB Fished Item**' and the '**WGB Shop**'.

- Widgets use custom made C++ delegates to update their information accordingly, you can track what each delegate does in the widget blueprints
