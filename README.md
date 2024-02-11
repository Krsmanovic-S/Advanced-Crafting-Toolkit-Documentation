Welcome to the **ACT Plugin!** Here we will go over some basic stuff about the plugin and I'll make a couple of sections about how to do certain stuff and how you can expand upon these systems. If you ever get stuck with something you can always hit me up on my Discord () and I'll be glad to help!

Without further ado, let us begin:
___

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [How to Install the Plugin](#how-to-install-the-plugin)
  - [First Steps](#first-steps)
  - [Implementing Input & Integrating the Widgets](#implementing-input--integrating-the-widgets)
- [Plugin How-To's](#plugin-how-tos)
  - [How To Add New Items](#how-to-add-new-items)
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

## First Steps

Let's start off by adding the **Inventory Component** and the **Crafting Component** to your Player Actor or any other one that wishes to utilize these components:

![ACT_Components](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/77689453-ebb4-468b-837f-801895ac1b06)

Crafting Stations need to know what class of actor they will be interacting with so make sure you set it in the Details panel inside BP Crafting Station:

![Set Player Class for Station](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/0dab6eb8-cdc6-42c1-9a7c-fe306fe669fe)

After we successfully added these components, it is time to customize them to your liking. We go over the customization in the *'How To'* section below.

## Implementing Input & Integrating the Widgets

As far as the inputs go, you can copy over the inputs from the character I provided directly into your own:

![Input](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/dc74ead0-95fb-41bd-b2c8-992d0b23d06f)

After that add the widgets located in **WBP HUD** to your own HUD if you have it and copy over the **On Drop** method into your HUD.

![HUD Drop Event](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/1731d82a-7eeb-42d1-9a29-d0c086396b96)

- This method is only required if you want to drop items by dragging them to an empty space in the HUD, if you don't want this feel free to skip that part

I'd also suggest creating a variable for your **Player Character/Pawn** inside the **BP_ItemUseDefinitions** as this gives you easy access to modify his stats/other things

This concludes the first part of the integration, now we move on to some customization and you are good to go 😄

___

# Plugin How-To's

In this section I will clarify a bit on how to use the plugin and what can you customize. Without further ado, let's begin:

## How To Add New Items

Adding Items is as easy as adding a new row in the **Item Data Table**:

![Adding Items Edited](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/2daf69c6-f47b-4c82-b290-d700b6c005ca)

After adding a new row, just fill out the information below and you are good to go. If you want to create or customize a **Bag** item, you will also do it here.

## How To Customize the Inventory

First add the '**Inventory**' component to any actor you want to use it one. Once added, select it in blueprints and head over to the details panel:

![Inventory Customization](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/2dbb8d81-ee3b-4bf2-abd2-ba5a58f31aaf)

Here you can customize all the options regarding the inventory. You should hover over the variables in the blueprint to see what they exactly do. Keep in mind that your Player **must have** this component in order for the UI to work.

## How To Customize the Crafting Component

Add the '**Crafting**' component to whichever actor you want to in blueprints. After adding it, click on it and go to the details panel:

![Crafting Customization](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/2b8c347a-0c48-42b2-970c-a2d5832f25ef)

Same as above for the inventory, here is where you can customize how you want your crafting to be. Actors that should have this component are the Player and the Crafting Stations. This component, like the inventory, can be customized per instance as well, you do not need to have the same settings on every single component! Different components can have different recipes as well!

- for crafting recipes, make sure that you tick the '**IsCraftable**' boolean in the '**ItemDataTable**' for any item you wish to use for crafting

As far as **Crafting Stations** go, you can edit their Crafting Component anywhere, even on just one instance in the world:

![Customizing Crafting Station Instance](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/bd3572ad-412d-47dd-bc45-fd24f1b3a3a4)

## How To Customize Shops

Shops are created by using a **Shop Component** on an actor. This actor then just needs to implement the *Create Shop Widget* event and thats pretty much it. You can customize the Shop Component in the Details panel of the actor where you added it:

![Adding Shop Components](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/d831e1f4-8c52-4f5a-8222-c8977d96211d)

![Shop Customization](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/05a5b6e2-40ca-472c-9a7c-c8dfb3dc90e2)

- make sure to input the '**Row Name**' of the item you want, not the actual name or it will not show up, the same logic applies for adding 'Default Items' to the Inventory and adding recipes to Crafting Components

- Shops use the '**Item Value**' part in the '**Item Data Table**' to determine how much to sell for and what to give the Player upon selling (sell value is set to **50%** of the total price by default)

- Shop widget logic is entirely in Blueprint, there is currently no C++ class for it, so if you want to explore that part take a look at **WBP Shop Widget**

If you would like to make a *character vendor*, you can just add the shop component to him, implement the widget creation event and you are done!

## How To Customize Widgets

For the inventory, the main widget is the '**WGB Inventory**'. You should not customize anything here, but rather if you want to change how the inventory looks, change the slot image of the '**WBP Inventory Slot**' and how the '**WGB Splitting Slider**' looks like. The part that goes on the HUD (WGB Player Inventory) should be customized to your liking. The equipment screen is optional, however be aware that if you want to add more equipment slots to it, you will need to modify the '**Initialize Equipment Slots**' function in the Player Inventory widget to accomodate the new slot or it won't be included.

For crafting, the main widget is the '**WGB Crafting Screen**'. You can modify this widget to style it in whatever way you want and you can also edit individual parts of it in their respective widgets (recipes, filters etc..). Shops are very simple to edit, you just need to change the look of the '**WGB Fished Item**' and the '**WGB Shop**'.

- Widgets use custom made C++ delegates to update their information accordingly, you can track what each delegate does in the widget blueprints

## How to Implement Use-Functionality

Using items is done through a UObject based class called **ItemUseDefinitions**. You should implement methods either in C++ or Blueprints on what you want your items to do when they are used:

![Blueprint Using Items](https://github.com/Krsmanovic-S/Advanced-Crafting-Toolkit-Documentation/assets/103185975/e24d23d8-1602-43b4-8dad-8d7b7a95efef)

For C++, simply add your functions in the **UItemUseDefinitions::MasterFunction()**. When used, items will lower their stack by the **UseDecrementStackAmount** variable that they posses, this is edited in the data table.
