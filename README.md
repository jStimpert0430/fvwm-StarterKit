# Fvwm-StarterKit
Fvwm-StarterKit is a robust set of modular default configs for Fvwm which highlight the more advanced features of fvwm in an easy to digest gui presentation and is designed with a  clean modular organization in mind for those curious can dive in and learn by picking apart rather than building up by using small pieces of functionality as a template to further extend.

![Preview](screenshot.png?raw=true "Preview Screenshot")

This software was created as a means to learn my way around fvwm and what I could do with the config files. I ended up with a really modular set of configs that I was able to easily arrange into a set of GUI options and is the kind of thing I wish I had available to me when I first started trying to learn. 

This software is ment to be a lighterweight and current alternative to "Fvwm-themes" and functions by loading immedietly after the default config for fvwm is loaded and does not require the use of a startx command or another invasive initialization process. If you're not happy with how it functions, simply remove the downloaded files from your .fvwm directory and everything will return to how it was set previously.

[CURRENTLY IN ACTIVE DEVELOPMENT - FEATURES AND ORGANIZATION MAY CHANGE FROM UPDATE TO UPDATE - NOT READY FOR DAILY USE - INSTALL AT YOUR OWN RISK!]

## Features

* Modular and unobtrusive design that is easy to pick apart should you want to learn how to set up your own or extend this design

* Scrolling desktop like that found in NSCDE

* Dynamic Decor and Colorset support, simply pick which combination of styling and colors you would like from the appearance menu and mix and match fvwm to your preference through the GUI. Add your own by dropping .color or .style files into the appropriate folder

* Select and omit the custom components you want and don't want

## Features Wishlist

* Internal Custom GUI Toolset, no need for external applications or libraries outside of Fvwm (Partially implemented)

* Multiple Taskbar options and designs

* Tweak individual decors and colors through the use of GUI Tweak menu to set functionality as desired without the need to open a text editor while using any built in style as a starting point

* Includes all fvwm wiki example decors, colors, and tools (Partially implemented)

## What this is not
* A full DE implementation, this is ment to be as an alternative default to the included fvwm config that is intended to be a more reasonable starting point as well as showcase some of the more unique features of fvwm that I feel the default configuration was missing. 

## Recommended for proper integration

* Raleigh GTK theme(https://github.com/thesquash/gtk-theme-raleigh)

* Sevenicons(https://github.com/markyb86/SevenIcons)

* Palemoon browser with the "Moonscape" theme.

* Enable settings inside GTK applications to honor system theming(ex. show titlebar in firefox)

* Stanalone tray - used to pin running applications onto the panel.

* Gmrun - small simple lightweight runner program with auto complete support

* Fonts - Most of the theme is using default X11 built in fonts(I like the bitmap aesthetic), however I did use "c059" romanized at 8 points for some of my applications found in the "gsfonts" library on Arch linux, You'll have to source this from your own package manager on other distrobutions.

## Installation

* Backup your personal config and local.config files and then copy the config, local.config, and the icons folder into your .fvwm config directory (Defaul: home/{user}/.fvwm)

* Copy stanalonetrayrc into home directory and rename to ".stanalonetrayrc" - can provide your own, but I found these settings work best with this panel arrangement.
