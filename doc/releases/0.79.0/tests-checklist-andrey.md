## Install tests
 * install a **previous version** on a clean machine (a clean machine doesn't have the `%localappdata%\Microsoft\PowerToys` folder)
 * open the Settings and for each module change at least one option
 * open the FancyZones editor and create two custom layouts:
    * a canvas layout with 2 zones, use unicode chars in the layout's name
    * one from grid template using 4 zones and splitting one zone
    * apply the custom canvas layout to the primary desktop
    * create a virtual desktop and apply the custom grid layout
    * if you have a second monitor apply different templates layouts for the primary desktop and for the second virtual desktop
 * install the new version (it will uninstall the old version and install the new version)
 - [ ] verify the settings are preserved and FancyZones configuration is still the same
 - [ ] test installing as SYSTEM (LocalSystem account)
   * Download PsTools from https://learn.microsoft.com/en-us/sysinternals/downloads/psexec
   * Run PowerToys installer with psexec tool `psexec.exe -sid <path_to_installer_exe`
   * Brief check if all modules are working

 * PER-USER and PER-MACHINE TESTS:
   * Install **previous version** on a clean machine and update with new per-machine version. Ensure that it is installed in Program files and that registry entries are under **HKLM**/Software/Classes/PowerToys. Go trhough different modules and ensure that they are working correctly.
   * Try installing per-user version over already installed per-machine version and ensure that proper error message is shown.
   * Remove PowerToys and install per-user version. Ensure that it is installed in <APPDATA>/Local/PowerToys and that registry entries are under **HKCU**/Software/Classes/PowerToys. Go trhough different modules and ensure that they are working correctly.
   * Create a new user and install per-user version there as well. Go trhough different modules and ensure that they are working correctly. Ensure that changing settings for one user does not change settings of other user.

## Functional tests

 Regressions:
 - [ ] https://github.com/microsoft/PowerToys/issues/1414#issuecomment-593529038
 - [ ] https://github.com/microsoft/PowerToys/issues/1524

## Localization
 Change the Windows language to a language different than English. Then verify if the following screens change their language:
 - [ ] System tray menu items
 - [ ] Settings
 - [ ] OOBE (What's new)
 - [ ] Keyboard Manager Editor
 - [ ] Color Picker (check the tooltips)
 - [ ] FancyZones Editor
 - [ ] Power Rename (new WinUI 3 may not be localized)
 - [ ] PowerToys Run ("Start typing" string is localized, for example)
 - [ ] Image Resizer
 - [ ] Shortcut Guide (Windows controls are localized)
 - [ ] File Explorer menu entries for Image Resizer, Power Rename and FileLocksmith
 - [ ] Hosts File Editor
 - [ ] File Locksmith
 - [ ] Registry Preview
 - [ ] Environment Variables

## General Settings

**Admin mode:**
 - [ ] restart PT and verify it runs as user
 - [ ] restart as admin and set "Always run as admin"
 - [ ] restart PT and verify it  runs as admin
 * if it's not on, turn on "Run at startup"
 - [ ] reboot the machine and verify PT runs as admin (it should not prompt the UAC dialog)
 * turn Always run as admin" off
 - [ ] reboot the machine and verify it now runs as user

**Modules on/off:**
 - [ ] turn off all the modules and verify all module are off
 - [ ] restart PT and verify that all module are still off in the settings page and they are actually inactive
 - [ ] turn on all the module, all module are now working
 - [ ] restart PT and verify that all module are still on in the settings page and they are actually working

**Quick access tray icon flyout:**
 - [ ] Use left click on the system tray icon and verify the flyout appears. (It'll take a bit the first time)
 - [ ] Try to launch a module from the launch screen in the flyout.
 - [ ] Try disabling a module in the all apps screen in the flyout, make it a module that's launchable from the launch screen. Verify that the module is disabled and that it also disappeared from the launch screen in the flyout.
 - [ ] Open the main settings screen on a module page. Verify that when you disable/enable the module on the flyout, that the Settings page is updated too.

**Settings backup/restore:**
 - [ ] In the General tab, create a backup of the settings.
 - [ ] Change some settings in some PowerToys.
 - [ ] Restore the settings in the General tab and verify the Settings you've applied were reset.

## Keyboard Manager

UI Validation:

  - [ ] In Remap keys, add and remove rows to validate those buttons. While the blank rows are present, pressing the OK button should result in a warning dialog that some mappings are invalid.
  - [ ] Using only the Type buttons, for both the remap windows, try adding keys/shortcuts in all the columns. The right-side column in both windows should accept both keys and shortcuts, while the left-side column will accept only keys or only shortcuts for Remap keys and Remap shortcuts respectively. Validate that the Hold Enter and Esc accessibility features work as expected.
  - [ ] Using the drop downs try to add key to key, key to shortcut, shortcut to key and shortcut to shortcut remapping and ensure that you are able to select remapping both by using mouse and by keyboard navigation.
  - [ ] Validate that remapping can be saved by pressing the OK button and re-opening the windows loads existing remapping.

Remapping Validation:

For all the remapping below, try pressing and releasing the remapped key/shortcut and pressing and holding it. Try different behaviors like releasing the modifier key before the action key and vice versa.
  - [ ] Test key to key remapping
    - A->B
    - Ctrl->A
    - A->Ctrl
    - Win->B (make sure Start menu doesn't appear accidentally)
    - B->Win (make sure Start menu doesn't appear accidentally)
    - A->Disable
    - Win->Disable
  - [ ] Test key to shortcut remapping
    - A->Ctrl+V
    - B->Win+A
  - [ ] Test shortcut to shortcut remapping
    - Ctrl+A->Ctrl+V
    - Win+A->Ctrl+V
    - Ctrl+V->Win+A
    - Win+A->Win+F
  - [ ] Test shortcut to key remapping
    - Ctrl+A->B
    - Ctrl+A->Win
    - Win+A->B
  * Test app-specific remaps
    - [ ] Similar remaps to above with Edge (entered as `msedge`), VSCode (entered as `code`) and cmd. For cmd try admin and non-admin (requires PT to run as admin)
    - [ ] Try some cases where focus is lost due to the shortcut. Example remapping to Alt+Tab or Alt+F4
  - [ ] Test switching between remapping while holding down modifiers - Eg. Ctrl+D->Ctrl+A and Ctrl+E->Ctrl+V, hold Ctrl and press D followed by E. Should select all and paste over it in a text editor. Similar steps for Windows key shortcuts.

## Screen Ruler
 * Enable Screen Ruler. Then:
   - [ ] Press the activation shortcut and verify the toolbar appears.
   - [ ] Press the activation shortcut again and verify the toolbar disappears.
   - [ ] Disable Screen Ruler and verify that the activation shortuct no longer activates the utility.
   - [ ] Enable Screen Ruler and press the activation shortcut and verify the toolbar appears.
   - [ ] Select the close button in the toolbar and verify it closes the utility.
 * With Screen Ruler enabled and activated:
   - [ ] Use the Bounds utility to measure a zone by dragging with left-click. Verify right click dismisses the utility and that the measurement was copied into the clipboard.
   - [ ] Use the Spacing utility to measure something and verify that left-click copies the measurement to the clipboard. Verify that right-click dismisses the utility.
   - [ ] Use the Horizontal Spacing utility to measure something and verify that left-click copies the measurement to the clipboard. Verify that right-click dismisses the utility.
   - [ ] Use the Vertical Spacing utility to measure something and verify that left-click copies the measurement to the clipboard. Verify that right-click dismisses the utility.
   - [ ] While using a Spacing utility, verify that using the mouse scroll wheel will adjust pixel color tolerance while measuring.
   - [ ] Open mspaint and draw 1px-thick straight line, also click with a pencil to draw a single pixel. In any Spacing mode, verify that one of line's dimension is 1, and pixel's dimensions are 1x1.
 * In a multi-monitor setup with different dpis on each monitor:
   - [ ] Verify that the utilities work well on each monitor, with continuous mode on and off.
   - [ ] Without any window opened and a solid color as your background, verify the horizontal spacing matches the monitor's pixel width.
   - [ ] Move your mouse back and forth around the edge of two monitors really quickly in each mode - verify nothing is broken.
   
 * Test the different settings and verify they are applied:
   - [ ] Activation shortcut
   - [ ] Continous mode
   - [ ] Per color channel edge detection
   - [ ] Pixel tolerance for edge detection
   - [ ] Draw feet on cross
   - [ ] Line color

## File Locksmith
 * Start the PowerToys installer executable and let it stay in the initial screen.
   - [ ] Right-click the executable file, select "What's using this file?" and verify it shows up. (2 entries will show, since the installer starts two processes)
   - [ ] End the tasks in File Locksmith UI and verify that closes the installer.
   - [ ] Start the installer executable again and press the Refresh button in File Locksmith UI. It should find new processes using the files.
   - [ ] Close the installer window and verify the processes are delisted from the File Locksmith UI. Close the window
 * Start the PowerToys installer executable again and let it stay in the initial screen.
   - [ ] Right click the directory where the executable is located, select "What's using this file?" and verify it shows up. 
   - [ ] Right click the drive where the executable is located, select "What's using this file?" and verify it shows up. You can close the PowerToys installer now.
 * Restart PowerToys as admin.
   - [ ] Right click "Program Files", select "What's using this file?" and verify "PowerToys.exe" doesn't show up.
   - [ ] Press the File Locksmith "Restart as an administrator" button and verify "PowerToys.exe" shows up.
 - [ ] Right-click the drive where Windows is installed, select "What's using this file?" and scroll down and up, verify File Locksmith doesn't crash with all those entries being shown. Repeat after clicking the File Locksmith "Restart as an administrator" button.
 - [ ] Disable File Locksmith in Settings and verify the context menu entry no longer appears.

## GPO
 * Copy the "PowerToys.admx" file to your Policy Definition template folder. (Example: C:\Windows\PolicyDefinitions) and copy the "PowerToys.adml" file to the matching language folder in your Policy Definition folder. (Example: C:\Windows\PolicyDefinitions\en-US)
   - [ ] Open the "Local Group Policy Editor" on Windows and verify there is a "Microsoft PowerToys" folder in Administrative Templates for both Computer Configuration and User Configuration.
 * In GPO, disable a module that can run as a standalone (FancyZones sounds good for this). Restart PowerToys.
   - [ ] Verify the module is not enabled.
   - [ ] Open settings and verify the module is not enabled and you can't enable it.
   - [ ] Try to open FancyZones Editor directly from the install folder and verify it doesn't run and adds a message to the log saying it didn't run because of GPO.
   - [ ] Verify the module can't be launched from the quick launcher system tray flyout launcher screen (FancyZones editor in this case).
   - [ ] Verify the module can't be enabled/disabled from the quick launcher system tray flyout.
 * In GPO, enable a module that can run as a standalone (FancyZones sounds good for this). Restart PowerToys.
   - [ ] Verify the module is enabled.
   - [ ] Open settings and verify the module is enabled and you can't disable it.
   - [ ] Verify the module can't be enabled/disabled from the quick launcher system tray flyout.
 * In GPO, try to set different settings in the Computer and User Configurations for a PowerToy. Restart PowerToys.
   - [ ] Verify that the setting in Computer Configuration has priority over the setting in User Configuration.
 * In GPO, disable a module that has a context menu entry (File Locksmith sounds good for this). Restart PowerToys.
   - [ ] Verify the module is not enabled. (No context menu entry)
   - [ ] Open settings and verify the module is not enabled and you can't enable it.
   - [ ] Try to open File Locksmith directly from the install folder and verify it doesn't run and adds a message to the log saying it didn't run because of GPO.
 * In GPO, disable a module that is a Preview Handler (Markdown Preview is good for this). Restart PowerToys.
   - [ ] Verify the module is not enabled. (Markdown files won't appear in the preview pane)
   - [ ] Open settings and verify the module is not enabled and you can't enable it.
 * Remember to reset all you Settings to Not Configured after the tests, both in Conputer and User Configurations.

## Paste As Plain Text
 * Copy some rich text (e.g word of the text is different color, another work is bold, underlined, etd.). Then:
   - [ ] Paste the text using standard Windows Ctrl + V shortcut and ensure that rich text is pasted (with all colors, formatting, etc.)
   - [ ] Paste the text using Paste As Plain Text activation shortcut and ensure that plain text without any formatting is pasted.
   - [ ] Paste again the text using standard Windows Ctrl + V shortcut and ensure the text is now pasted plain without formatting as well.
   - [ ] Change the activation shorctut and ensure that Paste As Plain Text is triggered using new shortcut.
   - [ ] Disable the module and ensure that text is not being pasted using activation shortcut. 

## Mouse Without Borders
 * Install PowerToys on two PCs in the same local network:
   - [ ] Verify that PowerToys is properly installed on both PCs.
   
 * Setup Connection:
   - [ ] Open MWB's settings on the first PC and click the "New Key" button. Verify that a new security key is generated.
   - [ ] Copy the generated security key and paste it in the corresponding input field in the settings of MWB on the second PC. Also enter the name of the first PC in the required field.
   - [ ] Press "Connect" and verify that the machine layout now includes two PC tiles, each displaying their respective PC names.
   
 * Verify Connection Status:
   - [ ] Ensure that the border of the remote PC turns green, indicating a successful connection.
   - [ ] Enter an incorrect security key and verify that the border of the remote PC turns red, indicating a failed connection.
   
 * Test Remote Mouse/Keyboard Control:
   - [ ] With the PCs connected, test the mouse/keyboard control from one PC to another. Verify that the mouse/keyboard inputs are correctly registered on the other PC.
   - [ ] Test remote mouse/keyboard control across all four PCs, if available. Verify that inputs are correctly registered on each connected PC when the mouse is active there.
   
 * Test Remote Control with Elevated Apps:
   - [ ] Open an elevated app on one of the PCs. Verify that without "Use Service" enabled, PowerToys does not control the elevated app.
   - [ ] Enable "Use Service" in MWB's settings. Verify that PowerToys can now control the elevated app remotely. Verify that MWB processes are running as LocalSystem, while the MWB helper process is running non-elevated.
   - [ ] Toggle "Use Service" again, verify that each time you do that, the MWB processes are restarted.
   - [ ] Run PowerToys elevated on one of the machines, verify that you can control elevated apps remotely now on that machine.

* Test Module Enable Status:
   - [ ] For all combinations of "Use Service"/"Run PowerToys as admin", try enabling/disabling MWB module and verify that it's indeed being toggled using task manager.
   
 * Test Disconnection/Reconnection:
   - [ ] Disconnect one of the PCs from network. Verify that the machine layout updates to reflect the disconnection. 
   - [ ] Do the same, but now by exiting PowerToys.
   - [ ] Start PowerToys again, verify that the PCs are reconnected.
  
 * Test Various Local Network Conditions:
   - [ ] Test MWB performance under various network conditions (e.g., low bandwidth, high latency). Verify that the tool maintains a stable connection and functions correctly.

 * Clipboard Sharing:
   - [ ] Copy some text on one PC and verify that the same text can be pasted on another PC.
   - [ ] Use the screenshot key and Win+Shift+S to take a screenshot on one PC and verify that the screenshot can be pasted on another PC.
   - [ ] Copy a file in Windows Explorer and verify that the file can be pasted on another PC. Make sure the file size is below 100MB.
   - [ ] Try to copy multiple files and directories and verify that it's not possible (only the first selected file is being copied).
 
 * Drag and Drop:
   - [ ] Drag a file from Windows Explorer on one PC, cross the screen border onto another PC, and release it there. Verify that the file is copied to the other PC. Make sure the file size is below 100MB.
   - [ ] While dragging the file, verify that a corresponding icon is displayed under the mouse cursor.
   - [ ] Without moving the mouse from one PC to the target PC, press CTRL+ALT+F1/2/3/4 hotkey to switch to the target PC directly and verify that file sharing/dropping is not working.

 * Lock and Unlock with "Use Service" Enabled:
   - [ ] Enable "Use Service" in MWB's settings.
   - [ ] Lock a remote PC using Win+L, move the mouse to it remotely, and try to unlock it. Verify that you can unlock the remote PC.
   - [ ] Disable "Use Service" in MWB's settings, lock the remote PC, move the mouse to it remotely, and try to unlock it. Verify that you can't unlock the remote PC.

 * Test Settings:
   - [ ] Change the rest of available settings on MWB page and verify that each setting works as described.

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

 * Profiles - Basic tests
   - [ ] Add new profile with no variables and name it "Test_profile_1" (referenced below by name)
   - [ ] Edit "Test_profile_1": Add one new variable to profile e.g. name: "profile_1_variable_1" value: "profile_1_value_1"
   - [ ] Add new profile "Test_profile_2": From "Add profile dialog" add two new variables (profile_2_variable_1:profile_2_value_1 and profile_2_variable_2:profile_2_value_2). Set profile to enabled and click Save. Open OS Environment variables window and confirm that all variables from the profile are applied correctly. Also, confirm that "Applied variables" list contains all variables from the profile.
   - [ ] Apply "Test_profile_1" while "Test_profile_2" is still aplpied. Open OS Environment variables window and confirm that all variables from Test_profile_2 are unapplied and that all variables from Test_profile_1 are applied. Also, confirm that state of "Applied variables" list is updated correctly.
   - [ ] Unapply applied profile. Open OS Environment variables window and confirm that all variables from the profile are unapplied correctly. Also, confirm that "Applied variables" list does not contain variables from the profile.

 * Overriding existing variable
   - [ ] To "Test_profile_1" add one existing variable from USER variables, e.g. TMP. After adding, change it's value to e.g "test_TMP" (or manually add variable named TMP with value test_TMP).
   - [ ] Apply "Test_profile_1". Open OS Environment variables window and confirm that TMP variable in USER variables has value "test_TMP". Confirm that there is backup variable "TMP_PowerToys_Test_profile_1" with original value of TMP var. Also, confirm that "Applied variables" list is updated correctly - there is TMP profile variable, and backup User variable..
   - [ ] Unapply "Test_profile_1". Open OS Environment variables window and confirm that TMP variable in USER variable has original value and that there is no backup variable. Also, confirm that "Applied variables" list is updated correctly.

 * PATH variable
   - [ ] In "Applied variables" list confirm that PATH variable is shown properly: value of USER Path concatenated to the end of SYSTEM Path.
   - [ ] To "Test_profile_1" add variable named PATH with value "path1;path2;path3" and click Save. Confirm that PATH variable in profile is shown as list (list of 3 values and not as path1;path2;path3).
   - [ ] Edit PATH variable from "Test_profile_1". Try different options from ... menu (Delete, Move up, Move down, etc...). Click Save.
   - [ ] Apply "Test_profile_1". Open OS Environment variables window and confirm that profile is applied correctly - Path value and backup variable. Also, in "Applied variables" list check that Path variable has correct value: value of profile PATH concatenated to the end of SYSTEM Path.

 * Loading profiles on startup
   - [ ] Close the app and reopen it. Confirm that the state of the app is the same as before closing.

 - [ ] "Test_profile_1" should still be applied (if not apply it). Delete "Test_profile_1". Confirm that profile is unapplied (both in OS Environment variables window and "Applied variables" list).
 - [ ] Delete "Test_profile_2". Check profiles.json file and confirm that both profiles are gone.
