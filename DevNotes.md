# Fvwm-StarterKit Dev Log

### - 5/24/24 -INDEV-
* Added support for modular... well modules. Can mix and match via a right click menu and select from an infinite amount of Taskbar styles, pager styles, and additional components. Currently only Taskbars are pieced out and hooked up for quick swap, but the rest are trivlial to do the same with, it's just a matter of organizing their structure into a similar structure as I did the taskbar modules. 

<kbd align="center">
	<img src="Screenshots/Ver-INDEV1/AppearanceMenu.png?raw=true">
</kbd>

<sup align="center">Can use any theme as a starting point, and use the options in the Appearance menu to tweak to perfection.  </sup>


* Once the additional base modules are added, I'll probably work towards cleaning up and finish documenting what I have and work towards an actual release for INDEV1. As it stands it's pretty powerful and useful, but I still need to clean up the oddities I left in just figuring out I wanted everything to interact and flow into eachother. Post INDEV1, I'd like to start to add the graphical form tools for the menu options I've added thus far but first I want to get everything I do have stable and clean and documented.

#
#
#

### - 5/21/24 -INDEV-
* Took an oppurtunity to create a win 2000 theme in my theme engine -- there are plenty of Win 95/98/XP themes for the various window managers out there, but very few styled after 2000 for some reason. It also gave me an chance to add the initial pieces for the dynamic styleable task bars and modules and figure out how I want to piece out of the modules/functionality

![Preview](/Screenshots/Ver-INDEV1/win2k.png?raw=true "Preview Screenshot")

* I still need to add customizable fonts on a per theme or style basis as well as figure out what I want to do with the pager system, however I'm pretty pleased with the results even in the rudimentary implementation I currently have.
#
#
#
### - 5/19/24 -INDEV-
* Added theme and .theme filetype support. Functions by setting a colorset, a decor, a font, and a wallpaper currently. Can additionally call custom modules or set specific styles from these files as well.

![Preview](/Screenshots/Ver-INDEV1/ThemeSwitcher.gif?raw=true "Preview Screenshot")
<sup align="center"> Real time Theme Switching between "TofuShop" and "ChocolateBar" </sup>

* To add custom themes/styles/colorsets/modules simply drop corrosponding files into the user folder for each directory and they'll appear as menu entries in their respective menus
