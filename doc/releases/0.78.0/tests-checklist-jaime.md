## Image Resizer
- [x] Disable the Image Resizer and check that `Resize images` is absent in the context menu
- [x] Enable the Image Resizer and check that `Resize images` is present in the context menu. (On Win11) Check if both old context menu and Win11 tier1 context menu items are present when module is enabled.
- [x] Remove one image size and add a custom image size. Open the Image Resize window from the context menu and verify that changes are populated
- [x] Resize one image
- [x] Resize multiple images
- [x] Open the image resizer to resize a `.gif` file and verify the "Gif files with animations may not be correctly resized." warning appears.

- [x] Resize images with `Fill` option
- [x] Resize images with `Fit` option
- [x] Resize images with `Stretch` option

- [x] Resize images using dimension: Centimeters
- [x] Resize images using dimension: Inches
- [x] Resize images using dimension: Percents
- [x] Resize images using dimension: Pixels

- [x] Change `Filename format` to `%1 - %2 - %3 - %4 - %5 - %6` and check if the new format is applied to resized images
- [x] Check `Use original date modified` and verify that modified date is not changed for resized images. Take into account that `Resize the original pictures(don't create copy)` should be selected
- [x] Check `Make pictures smaller but not larger` and verify that smaller pictures are not resized
- [x] Check `Resize the original pictures (don't create copies)` and verify that the original picture is resized and a copy is not created
- [x] Uncheck `Ignore the orientation of pictures` and verify that swapped width and height will actually resize a picture if the width is not equal to the height

## PowerRename
- [x] Check if disable and enable of the module works. (On Win11) Check if both old context menu and Win11 tier1 context menu items are present when module is enabled.
- [x] Check that with the `Show icon on context menu` icon is shown and vice versa.
- [x] Check if `Appear only in extended context menu` works.
- [x] Enable/disable autocomplete.
- [x] Enable/disable `Show values from last use`.
* Select several files and folders and check PowerRename options:
    - [x] Make Uppercase/Lowercase/Titlecase (could be selected only one at the time)
    - [x] Exclude Folders/Files/Subfolder Items (could be selected several)
    - [x] Item Name/Extension Only (one at the time)
    - [x] Enumerate Items. Test advanced enumeration using different values for every field ${start=10,increment=2,padding=4}.
    - [x] Case Sensitive
    - [x] Match All Occurrences. If checked, all matches of text in the `Search` field will be replaced with the Replace text. Otherwise, only the first instance of the `Search` for text in the file name will be replaced (left to right).
    * Use regular expressions
        - [x] Search with an expression (e.g. `(.*).png`)
        - [x] Replace with an expression (e.g. `foo_$1.png`)
        - [x] Replace using file creation date and time (e.g. `$hh-$mm-$ss-$fff` `$DD_$MMMM_$YYYY`)
        - [x] Turn on `Use Boost library` and test with Perl Regular Expression Syntax (e.g. `(?<=t)est`)
    * File list filters.
        - [x] In the `preview` window uncheck some items to exclude them from renaming.
        - [x] Click on the `Renamed` column to filter results.
        - [x] Click on the `Original` column to cycle between checked and unchecked items.

## PowerToys Run

 * Enable PT Run in settings and ensure that the hotkey brings up PT Run
   - [x] when PowerToys is running unelevated on start-up
   - [x] when PowerToys is running as admin on start-up
   - [x] when PowerToys is restarted as admin, by clicking the restart as admin button in settings.
 * Check that each of the plugins is working:
   - [x] Program - launch a Win32 application
   - [x] Program - launch a Win32 application as admin
   - [x] Program - launch a packaged application
   - [x] Calculator - ensure a mathematical input returns a correct response and is copied on enter.
   - [x] Windows Search - open a file on the disk.
   - [x] Windows Search - find a file and copy file path.
   - [x] Windows Search - find a file and open containing folder.
   - [x] Shell - execute a command. Enter the action keyword `>`, followed by the query, both with and without space (e.g. `> ping localhost`).
   - [x] Folder - Search and open a sub-folder on entering the path.
   - [x] Uri - launch a web page on entering the uri.
   - [x] Window walker - Switch focus to a running window.
   - [x] Service - start, stop, restart windows service. Enter the action keyword `!` to get the list of services.
   - [x] Registry - navigate through the registry tree and open registry editor. Enter the action keyword `:` to get the root keys.
   - [x] Registry - navigate through the registry tree and copy key path.
   - [x] System - test `lock`.
   - [x] System - test `empty recycle bin`.
   - [x] System - test `shutdown`.

 - [x] Disable PT Run and ensure that the hotkey doesn't bring up PT Run.

 - [x] Test tab navigation.

 * Test Plugin Manager
   - [x] Enable/disable plugins and verify changes are picked up by PT Run
   - [x] Change `Direct activation phrase` and verify changes are picked up by PT Run
   - [x] Change `Include in global result` and verify changes picked up by PT Run
   - [x] Clear `Direct activation phrase` and uncheck `Include in global result`. Verify a warning message is shown.
   - [x] Disable all plugins and verify the warning message is shown.

## OOBE
 * Quit PowerToys
 * Delete %localappdata%\Microsoft\PowerToys
 - [ ] Start PowerToys and verify OOBE opens
 * Change version saved on `%localappdata%\Microsoft\PowerToys\last_version.txt`
 - [ ] Start PowerToys and verify OOBE opens in the "What's New" page
 * Visit each OOBE section and for each section:
   - [ ] open the Settings for that module
   - [ ] verify the Settings work as expected (toggle some controls on/off etc.)
   - [ ] close the Settings
   - [ ] if it's available, test the `Launch module name` button
 * Close OOBE
 - [ ] Open the Settings and from the General page open OOBE using the `Welcome to PowerToys` link

## Mouse Utils

Find My Mouse:
  * Enable FindMyMouse. Then, without moving your mouse:
    - [x] Press Left Ctrl twice and verify the overlay appears.
    - [x] Press any other key and verify the overlay disappears.
    - [x] Press Left Ctrl twice and verify the overlay appears.
    - [x] Press a mouse button and verify the overlay disappears.
  * Disable FindMyMouse. Verify the overlay no longer appears when you press Left Ctrl twice.
  * Enable FindMyMouse. Then, without moving your mouse:
    - [x] Press Left Ctrl twice and verify the overlay appears.
  * Enable the "Do not activate on game mode" option. Start playing a game that uses CG native full screen.
    - [x] Verify the overlay no longer appears when you press Left Ctrl twice.
  * Disable the "Do not activate on game mode" option. Start playing the same game.
    - [x] Verify the overlay appears when you press Left Ctrl twice. (though it'll likely minimize the game)
  * Test the different settings and verify they apply:
    - [x] Overlay opacity
    - [x] Background color
    - [x] Spotlight color
    - [x] Spotlight radius
    - [x] Spotlight initial zoom (1x vs 9x will show the difference)
    - [x] Animation duration
    - [x] Change activation method to shake and activate by shaking your mouse pointer
    - [x] Excluded apps

Mouse Highlighter:
  * Enable Mouse Highlighter. Then:
    - [x] Press the activation shortcut and press left and right click somewhere, verifying the hightlights are applied.
    - [x] With left mouse button pressed, drag the mouse and verify the hightlight is dragged with the pointer.
    - [x] With right mouse button pressed, drag the mouse and verify the hightlight is dragged with the pointer.
    - [x] Press the activation shortcut again and verify no highlights appear when the mouse buttons are clicked.
    - [x] Disable Mouse Highlighter and verify that the module is not activated when you press the activation shortcut.
  * Test the different settings and verify they apply:
    - [x] Change activation shortcut and test it
    - [x] Left button highlight color
    - [x] Right button highlight color
    - [x] Opacity
    - [x] Radius
    - [x] Fade delay
    - [x] Fade duration

Mouse Pointer Crosshairs:
  * Enable Mouse Pointer Crosshairs. Then:
    - [x] Press the activation shortcut and verify the crosshairs appear, and that they follow the mouse around.
    - [x] Press the activation shortcut again and verify the crosshairs disappear.
    - [x] Disable Mouse Pointer Crosshairs and verify that the module is not activated when you press the activation shortcut.
  * Test the different settings and verify they apply:
    - [x] Change activation shortcut and test it
    - [x] Crosshairs color
    - [x] Crosshairs opacity
    - [x] Crosshairs center radius
    - [x] Crosshairs thickness
    - [x] Crosshairs border color
    - [x] Crosshairs border size

Mouse Jump:
  * Enable Mouse Jump. Then:
    - [x] Press the activation shortcut and verify the screens preview appears.
    - [x] Change activation shortcut and verify that new shorctut triggers Mouse Jump.
    - [x] Click around the screen preview and ensure that mouse cursor jumped to clicked location.
    - [x] Reorder screens in Display settings and confirm that Mouse Jump reflects the change and still works correctly.
    - [x] Change scaling of screens and confirm that Mouse Jump still works correctly.
    - [x] Unplug additional monitors and confirm that Mouse Jump still works correctly.
    - [x] Disable Mouse Jump and verify that the module is not activated when you press the activation shortcut.

## Awake
 - [ ] Try out the features and see if they work, no list at this time.

## Text Extractor
 * Enable Text Extractor. Then:
   - [x] Press the activation shortcut and verify the overlay appears.
   - [x] Press Escape and verify the overlay disappears.
   - [x] Press the activation shortcut and verify the overlay appears.
   - [x] Right-click and select Cancel. Verify the overlay disappears.
   - [x] Disable Text Extractor and verify that the activation shortuct no longer activates the utility.
 * With Text Extractor enabled and activated:
   - [x] Try to select text and verify it is copied to the clipboard.
   - [x] Try to select a different OCR language by right-clicking and verify the change is applied.
 * In a multi-monitor setup with different dpis on each monitor:
   - [x] Verify text is correctly captured on all monitors.
 * Test the different settings and verify they are applied:
   - [x] Activation shortcut
   - [x] OCR Language

## GPO
 * Copy the "PowerToys.admx" file to your Policy Definition template folder. (Example: C:\Windows\PolicyDefinitions) and copy the "PowerToys.adml" file to the matching language folder in your Policy Definition folder. (Example: C:\Windows\PolicyDefinitions\en-US)
   - [x] Open the "Local Group Policy Editor" on Windows and verify there is a "Microsoft PowerToys" folder in Administrative Templates for both Computer Configuration and User Configuration.
 * In GPO, disable a module that can run as a standalone (FancyZones sounds good for this). Restart PowerToys.
   - [x] Verify the module is not enabled.
   - [x] Open settings and verify the module is not enabled and you can't enable it.
   - [x] Try to open FancyZones Editor directly from the install folder and verify it doesn't run and adds a message to the log saying it didn't run because of GPO.
   - [x] Verify the module can't be launched from the quick launcher system tray flyout launcher screen (FancyZones editor in this case).
   - [x] Verify the module can't be enabled/disabled from the quick launcher system tray flyout.
 * In GPO, enable a module that can run as a standalone (FancyZones sounds good for this). Restart PowerToys.
   - [x] Verify the module is enabled.
   - [x] Open settings and verify the module is enabled and you can't disable it.
   - [x] Verify the module can't be enabled/disabled from the quick launcher system tray flyout.
 * In GPO, try to set different settings in the Computer and User Configurations for a PowerToy. Restart PowerToys.
   - [x] Verify that the setting in Computer Configuration has priority over the setting in User Configuration.
 * In GPO, disable a module that has a context menu entry (File Locksmith sounds good for this). Restart PowerToys.
   - [x] Verify the module is not enabled. (No context menu entry)
   - [x] Open settings and verify the module is not enabled and you can't enable it.
   - [x] Try to open File Locksmith directly from the install folder and verify it doesn't run and adds a message to the log saying it didn't run because of GPO.
 * In GPO, disable a module that is a Preview Handler (Markdown Preview is good for this). Restart PowerToys.
   - [x] Verify the module is not enabled. (Markdown files won't appear in the preview pane)
   - [x] Open settings and verify the module is not enabled and you can't enable it.
 * Remember to reset all you Settings to Not Configured after the tests, both in Conputer and User Configurations.

## Paste As Plain Text
 * Copy some rich text (e.g word of the text is different color, another work is bold, underlined, etd.). Then:
   - [ ] Paste the text using standard Windows Ctrl + V shortcut and ensure that rich text is pasted (with all colors, formatting, etc.)
   - [ ] Paste the text using Paste As Plain Text activation shortcut and ensure that plain text without any formatting is pasted.
   - [ ] Paste again the text using standard Windows Ctrl + V shortcut and ensure the text is now pasted plain without formatting as well.
   - [ ] Change the activation shorctut and ensure that Paste As Plain Text is triggered using new shortcut.
   - [ ] Disable the module and ensure that text is not being pasted using activation shortcut. 

## Crop And Lock
 * Thumbnail mode
   - [ ] Test with win32 app
   - [ ] Test with packaged app
   
 * Reparent mode (there are known issues where reparent mode doesn't work for some apps)
   - [ ] Test with win32 app
   - [ ] Test with packaged app

## Environment Variables
 * NOTE: Make backup of USER and SYSTEM Path and TMP variables before testing so you can revert those is something goes wrong!
 * Open Environment Variables settings
   - [ ] Launch as administrator ON - Launch Environment Variables and confirm that SYSTEM variables ARE editable and Add variable button is enabled
   - [ ] Launch as administrator OFF - Launch Environment Variables and confirm that SYSTEM variables ARE NOT editable and Add variable button is disabled

 * User/System variables
   - [ ] Add new User variable. Open OS Environment variables window and confirm that added variable is there. Also, confirm that it's added to "Applied variables" list.
   - [ ] Edit one User variable. Open OS Environment variables window and confirm that variable is changed. Also, confirm that change is applied to "Applied variables" list.
   - [ ] Remove one User variable. Open OS Environment variables window and confirm that variable is removed. Also, confirm that variable is removed from "Applied variables" list.
   - Repeat the steps for System variables.

