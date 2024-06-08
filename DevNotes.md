# Fvwm-StarterKit Dev Log

### - 6/7/24 -INDEV-
* This one is going to be quite a large set of notes as I haven't updated the patch documentation in a little bit. I'll try to highlight and summerize each piece seperately. 

# Rewrote project core

* Created a standalone version of the "Fvwm99" theme(https://github.com/jStimpert0430/Fvwm99) as I feel there may be interest in just a Win2000-like environment for Fvwm without the rest of the project and it has given me an oppurtunity to really identify and isolate the project core from the theme files. It's also given me a chance to add a whole bunch of infostore variables in effort to make structure as generic and as easily rearranged as possible in case of future restructuring so it won't be such a collosal effort.

    ### Core Structure
    #
     I'm currently torn between two different structures for the theme/styles/colorset folders. In the version of the theme engine present in Fvwm-StarterKit the theme is structured as--

1. Local.config reads from the start.conf entry file which InfoStore variables that define various filepaths in the program. It's structured this way so I can simply set the root folder, and as long as the subfolders follow the same structure, It should be super portable and easy to rename a lot of things.

2. The settings.conf file is loaded -  which defines InfoStore variables used by the default theme in order to set its parameters, or by other themes that don't want to override every option so they'll have a default available as a fallback. 

    * My intention behind this file is to at some point in the future make a GUI control in the Fvwm Forms engine for these options and to save them between sessions as an override file as well as provide a "tweaks" menu so you can override other theme defaults, and save the tweaked theme in a user folder. But for now, they're largely redunant as the other themes simply override them when they're loaded.


3. Global Functions and Modules are loaded - Any functions or modules needed globally throughout all themes are defined here. Currently only built in Fvwm Functions and Modules reside in here,  but will add more as time goes on.

4. Input and default behaviour are set - In thinking about this one, this may get moved into the theme or styles' domain entirely. As I currently have window/taskbar bevariour/pager already set per theme already. Having a global input file feels a little redundant. Will look at this one more.

5. Menu Builder - The menu much like the rest of the program is split into modules. Each module defines a menu or piece of functionality for the menu(i.e. Program dock is a group of 4 menu entries that link to commonly used system programs and Appearance menu is used for theme tweaks). I've structured it this way so a user or theme builder can create a menu easily out of components like they can with task bar or any other part of the themes in Fvwm. Rearrange or expand to your hearts content, without having to major edit core functionality of each peice. Just call the pieces you want from the package or add your own. This feels a little too messy and confusing in this iteration and I'd like to maybe condense it back into another style option but for now this will suffice and gives me freedom to build with it.
    * The appearance menu - The appearance menu functions by creating catagory folders (Wallpaper, Colorsets, Styles, Taskbar) and then populating each of those folders based on the contents of the corrosponding folder inside the theme directory. 
    
        Styles for example use "Piperead" in a for loop to find each ".style" file in the style folder and add them as a menu entry that will read that style file upon execution. The same for the other options but with their corrosponding filetypes filtered. Can also use piperead to identify folders from within one of these folders in order to add sub-menus automatically.

6. Default Theme is loaded - The theme structure is where the magic of Fvwm-StarterKit happens and is what I feel is one of the most interesting parts of Fvwm.
    * Themes are defined as .theme files and are a collection of read statements pointing at a colorset, a fontset, a style, and a taskbar. 
    * A .style file - what dictates the window decorations as well as the functionality of each of the buttons.
    * A .colorset file - a file definiting 8 colorsets that can be used globally by any theme. Themes/styles may add more if the theme calls for it, but in order to keep compatability with any colorset provided by Fvwm-StarterKit on your themes, it's best if you cap these at 8 colors. 
    * A Taskbar file - Contains arrangement, functionality, and styling defintions for taskbars

     Each of these files can choose to override defaults or just use them if no override definition is provided, structured in a way to allow somebody who is interested to go in and look at pieces of functionality, pick it apart, and add their own pieces by simply adding their own files and they'll appear in the menus alongside all the other style options. In each of these files are standard Fvwm command script so it's the same syntax somebody would use to make their own configs. I've always felt more comfortable learning this way and it's the kind of thing that I really wish I had learning Fvwm. The wiki is great and gives wonderful examples, but sometimes you just don't know what you're looking for. It's easier to find the functionality of a component when the definition is included right in the program itself.

    ### Directory Structure
    #
    The directory structure in this iteration of the theme engine is pretty flat and shallow. Present in the root folder is-- 
    * a colorset folder - colorset definitions
    * a style folder - styleset definitions
    * a theme folder - theme definitions
    * a bg folder - background images
    * a icons folder - icon images
    * a component folder - system components and modules
    * a config folder. - global input/settings
    
    Each theme can provide its own folder in each of these folders to add theme specific styles, assets, modules, or functionality. As long as the root folders contain the .style/.colorset/.theme files for the corrosponding theme they'll automatically be added to the menu upon menu building.

    ### New Core Changes!
    #
    In porting out Fvwm99 from the rest of the package. It really gave me a chance to go over the current implementation with an extremely granular line by line rewrite in which I was able to switch a lot of hardcoded functionality over into variables. Some of the major changes include
    * Style Targets - Stylesets now use an InfoStore variable named "targetComponent" which make them more generic. Can be called by various pieces in order to style themselves without having repeating code for each theme or similar styles.
    * StyleOverrideFiles - Contain small functionality definitions that will be used in themes to define their behaviour or by the "tweaks" menu to make small granular changes to your environment through a GUI. A lot of these files are really simply one line commands, but this makes it so they're easily able to be added to a menu or called through a GUI. 
    
        (Ex. One of these files might be called "ClickToRaise" and another might be "SloppyFocus". Each theme could easily call these commands directly, but set up this way I could have a Appearence -> Tweaks -> Focus folder in which the user is able to switch between them from any theme, regardless of how the theme is defined as well as just providing an easy to parse list of all possible Fvwm options through a standard context menu for new users).
    * Theme Path Restructuring - Each theme is now responsible for its own theme filepaths with a standard definition being the theme name. Each individual theme folder now contains a copy of the main program structure (a colorset, a styles, a modules folder, etc.). 
    
        This was an organization attempt I think might be taking it one abstraction step too far. This project was intended to be an easy to parse and simple to pick apart project. While this arrangement is a little neater inside the folder, I feel like it buries functionality/styling too deep into folder within folders. It's hard for a new user to dig through without a guide. The advantages of writing this way however include having nice self contained theme folders that are able to be distributed by copying a .theme file and the corrosponding folder. I'd like to play around with this design a little more before totally trashing it, however. 

    * Extreme Modularizing effort - Almost everything in the theme engine is controlled through variables set in the settings.conf file so everything is accessible from one neatly arranged file. This will make making large updates to systems *much* easier going forward and it just feels way neater to use when you can use quick identifiers for more complicated, but often used commands. Will create documentation for each of these command aliases for the release version. 

    * The User Folder - Core functionality now resides inside the "Core" folder inside the root menu, the root also contains a "User" folder which houses a copy of the main core structure, but instead stores any user created themes/colorsets/styles/ etc. This will be used by GUI tools to store changes made by user so the core functionality will remain unchanged and can easily be updated without breaking things or overwriting something written by the user as well as making it easier to distinguish between built in themes and user created ones.

    * Directory Map Files - Contains definition for filepaths used by the program. Currently a user/core variant. This will be used to easily update folder structure for future updates. Each filepath is build from an InfoStore of the filepath that came before it, so if the root is changed, all other filepaths will be updated automatically. Leaving each option controlling exactly one piece of the filepath.

    Going forward with the rewrite, I'll try to update the current themes from this version to the new core and see how I like the new structure and if I can identify any shortcomings with the design I'm not seeing right now. If I don't like it I'll simply revert the structure to the current implementation and keep the other core improvements, then I'll update Fvwm-StarterKit with the new core. At this point I should be in a pretty good spot for release apart from documentation. The logic has been cleaned and organized and is really extenable as is. I'm excited for anybody curious to try it and leave feedback. Still the ocassional bug here and there, but overall it's a really useable package. This note has gotten pretty wordy, and there isn't much visually to show for it, so continuing on with --

# New Themes, Styles, Taskbars, and Components
* ### New Themes

    * Moscow Theme - a soft purple gray with a subtle darker purple highlight color and new side panel default taskbar and a muted blue window highlight color. Insprired by old ID games and their unix environments
        <kbd align="center">
	    <img src="Preview/screenshots/indev/patch/moscow.png?raw=true"  />
        </kbd>


* ### New Styles

    * Default-AltColors - Uses the menu highlight color for the window highlight color rather than the standard theme. These are often very different colors, and adds an easy way to add even more variation with the same colorsets already present
        <kbd align="center">
	    <img src="Preview/screenshots/indev/patch/defaultStyleAltColors.png?raw=true"  />
        </kbd>


* ### New Taskbars

    * Floating - Center of the screen mini taskbar
    * Micro Floating - Center of the screen taskbar with a smaller height and cleaner no icon appearance
    * Gaps - Taskbar with a 10px gap on each side to accomodate a gaps like setup
    * Islands - First implementation of a side panel. A floating frame panel where each component is its own "island" Includes variant with a spotify controller and one without 
        <kbd align="center">
	    <img src="Preview/screenshots/indev/patch/IslandPanelUpgrade.png?raw=true"  />
        </kbd>

* ### New Colorsets

    * Soot - Moscow default color
        <kbd align="center">
	    <img src="Preview/screenshots/indev/patch/soot.png?raw=true"  />
        </kbd>
    * Chalkboard - Darkmode Variant of Soot
        <kbd align="center">
	    <img src="Preview/screenshots/indev/patch/chalkboard.png?raw=true"  />
        </kbd>

* ### New Components

    * Spotify-player-controls - Spotify player controls is a simple spotify-player controller module and small song info display window with realtime album art support that is present in a version of the right panel, or available to be called and moved freely from any theme. Currently, this module is only interfaced to the TUI client - Spotify-player, but will try to add support for standard spotify and the more popular spotify-tui. If possible, I'd like to just map these controls to some global media control.

        <kbd align="center">
	    <img src="Preview/screenshots/indev/patch/spotify_player_controls.png?raw=true"  />
        </kbd>


    * Weather - Gets weather
    * Date - Gets day name, month name, and day number

# Github updates
 * Added this devlog page to reduce some of the clutter in the main page
 * Added theme/colorset preview page

#
#
#








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

    <kbd align="center">
	<img src="Screenshots/Ver-INDEV1/win2k.png?raw=true"  />
    </kbd>

* I still need to add customizable fonts on a per theme or style basis as well as figure out what I want to do with the pager system, however I'm pretty pleased with the results even in the rudimentary implementation I currently have.
#
#
#
### - 5/19/24 -INDEV-
* Added theme and .theme filetype support. Functions by setting a colorset, a decor, a font, and a wallpaper currently. Can additionally call custom modules or set specific styles from these files as well.

    <kbd align="center">
	<img src="Screenshots/Ver-INDEV1/ThemeSwitcher.gif?raw=true ">
    </kbd>
    <sup align="center"> Real time Theme Switching between "TofuShop" and "ChocolateBar" </sup>

* To add custom themes/styles/colorsets/modules simply drop corrosponding files into the user folder for each directory and they'll appear as menu entries in their respective menus
