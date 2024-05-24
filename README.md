# Fvwm-StarterKit
Fvwm-StarterKit is a set of lightweight, yet robust, configs and tools for Fvwm which highlight some of the more unique features of Fvwm and its derivatives.

Featuring an easy to use and intuitive GUI config interace, out of the box dynamic and modular Colorset, Decor, Theme, and Component support, Desktop scrolling, and more.

Fvwm-StarterKit is designed at its core with a clean, modular, and extendable structure in mind so those curious can dive in and learn by picking apart rather than from scratch by using small pieces of immedietly documented and reuseable functionality as a template to further extend without fully obsfucating away the Fvwm that is underneath or those just looking for more of a standard desktop experience out of the box than that of the default Fvwm configutation provides.

![Preview](Screenshots/Ver-INDEV1/screenshot.png?raw=true "Preview Screenshot")

[CURRENTLY IN ACTIVE DEVELOPMENT - FEATURESET, STRUCTURE, AND IMPLEMENTATION MAY CHANGE FROM UPDATE TO UPDATE - THINGS WILL MOST CERTAINLY BREAK - NOT READY FOR DAILY USE - INSTALL AT YOUR OWN RISK!]

## Author Note
This software was initially created as a means to familiarize myself with Fvwm and what I could do with the config files. I saw all of what NSCDE was able to accomplish with Fvwm and was really impressed, but I wanted to use something similar without all of the CDE heritage baggage and it seemed easier to do that from scratch within Fvwm than tear out of the pieces of NSCDE I didn't want. 

What I've ended up with is a modular set of pieces I'm able to easily mix and match dynamically and in realtime. It resembles something like what "fvwm-themes" was in a lot of ways but with the key differences of -- Fvwm-StarterKit is less invasive(No StartX needed, loads immedietly after the default config with non-destructive installation), features a more standard and current fvwm3 design, and features a contained rootfolder/subfolder structure that is extensible by simply dropping the appropriate filetypes that contain definitions into the corrosponding user folder or by using the custom GUI tools to build those files for you.

 This is something I wish I had available to me when I first tried Fvwm, and I hope it can become a useful starting point for others going forward. It's a wonderful, powerful, and surprisingly modern window manager but one with quite a large wall of a learning curve for just a casual curious hobbyist.

## Feature Highlights
* A Clean, sharp, and sensible set of defaults that provide a neat and useable floating window desktop evironment out of the box

* Multiple Dynamic Decors, Colorsets, Themes, Tools, and Styles included with the ability to add additional custom sets by simply creating .colors, .styles, .theme, or .sys modules or by using the built in GUI toolset. Mix and match to your personal preference and watch changes propogate on screen in realtime!

* Self contained, modular, and well documented design. Functionality is split into small pieces that are easier learn from, extend, and mix and match how you want. Easily build the Fvwm desktop for you by selecting the components you want and don't want.

* Realtime Scrolling Desktop - Multiply your screen real estate with the ability to scroll up and down or left and right in real time by hovering over your desktop and using the scroll wheel like you would on a webpage. Drag a window to the edge of a page to snap it and your view to the next page or use the pager to arrange windows as you'd like.

* Non-Destructive design, No additional commands or setup needed and won't interfere with any other settings or configurations used by other DE's or WM's. Uninstall by simply removing the Fvwm-StarterKit directory and the local.config entry point to return your Fvwm Desktop to exactly how it was before.


## Features Wishlist

* Internal Custom GUI Toolset, no need for external applications or libraries outside of Fvwm (Partially implemented)

* Multiple Taskbar options and designs

* Tweak individual decors and colors through the use of GUI Tweak menu to set functionality as desired without the need to open a text editor while using any built in style as a starting point

* Includes all fvwm wiki example decors, colors, and tools (Partially implemented)

## Some Recommendations for better app integration

* Raleigh GTK theme(https://github.com/thesquash/gtk-theme-raleigh)

* OneStepBack GTK theme (https://github.com/raorn/OneStepBack)

* Sevenicons(https://github.com/markyb86/SevenIcons)

* Palemoon browser with the "Moonscape" theme.

* Enable settings inside GTK applications to honor system theming(ex. show titlebar in firefox)

* Stanalone tray - used to pin running applications onto the panel.

## Installation

* Backup your personal config and local.config files and then copy the local.config and the themes folder into your .fvwm config directory (Default: home/{user}/.fvwm) 

NOTE: This software was designed to load after the default config file, any personal changes made to this file may cause problems with conflicting configurations within Fvwm-StarterKit, considering moving personal changes to your own local.config, restoring config to default, and then installing Fvwm-StarterKit for optimal functionality.

* Copy stanalonetrayrc into home directory and rename to ".stanalonetrayrc" - can provide your own, but I found these settings work best with this panel arrangement.

## Recent Update Notes
- 5/24/24 -INDEV-
    Added support for modular... well modules. Can mix and match via a right click menu and select from an infinite amount of Taskbar styles, pager styles, and additional components. Currently only Taskbars are pieced out and hooked up for quick swap, but the rest are trivlial to do the same with, it's just a matter of organizing their structure into a similar structure as I did the taskbar modules. 

    ![Preview](Screenshots/Ver-INDEV1/AppearanceMenu.png?raw=true "Preview Screenshot")

    <sup align="center">Can use any theme as a starting point, and use the options in the Appearance menu to tweak to perfection.  </sup>

    Once the additional base modules are added, I'll probably work towards cleaning up and finish documenting what I have and work towards an actual release for INDEV1. As it stands it's pretty powerful and useful, but I still need to clean up the oddities I left in just figuring out I wanted everything to interact and flow into eachother. Post INDEV1, I'd like to start to add the graphical form tools for the menu options I've added thus far but first I want to get everything I do have stable and clean and documented.

- 5/21/24 -INDEV-
    Took an oppurtunity to create a win 2000 theme in my theme engine -- there are plenty of Win 95/98/XP themes for the various window managers out there, but very few styled after 2000 for some reason. It also gave me an chance to add the initial pieces for the dynamic styleable task bars and modules and figure out how I want to piece out of the modules/functionality

    ![Preview](Screenshots/Ver-INDEV1/win2k.png?raw=true "Preview Screenshot")

    I still need to add customizable fonts on a per theme or style basis as well as figure out what I want to do with the pager system, however I'm pretty pleased with the results even in the rudimentary implementation I currently have.

- 5/19/24 -INDEV-
    Added theme and .theme filetype support. Functions by setting a colorset, a decor, a font, and a wallpaper currently. Can additionally call custom modules or set specific styles from these files as well.

    ![Preview](Screenshots/Ver-INDEV1/ThemeSwitcher.gif?raw=true "Preview Screenshot")
    <sup align="center"> Real time Theme Switching between "TofuShop" and "ChocolateBar" </sup>

    To add custom themes/styles/colorsets/modules simply drop corrosponding files into the user folder for each directory and they'll appear as menu entries in their respective menus