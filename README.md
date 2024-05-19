# ModernMotifMinimal
Modern Motif Minimal is a simple and clean personal set of default configs for fvwm 2.7(and likely 3, although untested) in a motif-esque coat of paint with a modern design skew.

![Preview](screenshot.png?raw=true "Preview Screenshot")

This theme was created as a means to learn my way around fvwm and what I could do with the config files. I ended up with a really useable clean and simple modern desktop that takes visual cues from design languges of the early 2000's and as a "what if" for if the MWM had continued to be refined. This is still a WIP and is in the process of being organized and genericised(The bar size is currently hardcoded for 1440p, for example), but it's more than useable in its current state.

## Features 

* Clean and straightforward menu panel

* Scrolling desktop like that found in NSCDE

* Standard panel design with clock and stanalonetray integration

## What this is not
* A full DE implementation, this is ment to be as an alternative default to the included fvwm config that is intended to be a more reasonable starting point as well as showcase some of the more unique features of fvwm that I feel the default configuration was missing. 

## Major themes and apps recommended for good integration

* Raleigh GTK theme(https://github.com/thesquash/gtk-theme-raleigh)

* Sevenicons(https://github.com/markyb86/SevenIcons)

* Palemoon browser with the "Moonscape" theme.

* Various tweaks in GTK apps to ensure system theming.

* Stanalone tray - used to pin running applications onto the panel.

* Gmrun - small simple lightweight runner program with auto complete support

* Fonts - Most of the theme is using default X11 built in fonts(I like the bitmap aesthetic), however I did use "c059" romanized at 8 points for some of my applications found in the "gsfonts" library on Arch linux, You'll have to source this from your own package manager on other distrobutions.

## Installation

* Backup your personal config and local.config files and then copy the config, local.config, and the icons folder into your .fvwm config directory (Defaul: home/{user}/.fvwm)

* Copy stanalonetrayrc into home directory and rename to ".stanalonetrayrc" - can provide your own, but I found these settings work best with this panel arrangement.
