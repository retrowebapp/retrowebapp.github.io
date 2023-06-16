## How to:
# Install MS-DOS 6.22 on VirtualBox

__Ruth Webster, June 16th 2023__

1994's [MS-DOS 6.22](https://en.wikipedia.org/wiki/MS-DOS) was the last
standalone DOS product sold by Microsoft. It's the foundation for 1993's
[Windows 3.11](https://en.wikipedia.org/wiki/Windows_3.1x), which is the
earliest OS that 1996's
[Internet Explorer 3](https://en.wikipedia.org/wiki/Internet_Explorer_3) can
run on.

This how-to guide will help you install MS-DOS 6.22 as a virtual machine
on [Oracle VirtualBox](https://en.wikipedia.org/wiki/VirtualBox). After
creating an MS-DOS 6.22 virtual machine, you'll be able to install Windows 3.11.
Check out our how-to guide:  
- [How to: Install Windows 3.11 on VirtualBox](
  ./install-windows-3.11-on-virtualbox.md)

VirtualBox is free to download and use. MS-DOS 6.22 can be considered
[abandonware](https://en.wikipedia.org/wiki/Abandonware) - Microsoft stopped
supporting it at the end of 2001.

---

### Prerequisites and resources:

- 'Microsoft MS-DOS 6.22 Plus Enhanced Tools (3.5-1.44mb)' from [winworldpc.com
  ](https://winworldpc.com/download/c38fc38d-68c2-bbe2-80a6-4b11c3a4c2ac) (~5 MB)
- Or; the same file renamed 'ms-dos-6.22-plus-enhanced-tools-3.5.7z', from [here
  ](./install-ms-dos-6.22/ms-dos-6.22-plus-enhanced-tools-3.5.7z)
- Ideally, a computer running macOS - but Linux, Solaris or Windows are ok
- VirtualBox 7.0 or later, [downloaded from virtualbox.org
  ](https://www.virtualbox.org/wiki/Downloads) (~130 MB)

This how-to guide is targeted at macOS Monterey on an Intel MacBook. Other
recent macOS versions should work very similarly.

If you're on Linux, Solaris or Windows, just ignore the Mac-specific parts of
this guide. The VirtualBox parts should work similarly on all platforms.

---

## I. Install VirtualBox

1. Download VirtualBox 7.0 or later from [virtualbox.org](
   https://www.virtualbox.org/wiki/Downloads) - about 130 MB
2. Double-click the downloaded 'VirtualBox-7.0.8-156879-OSX.dmg'
3. Double-click 'VirtualBox.pkg' in the window which pops up
4. Click 'Continue' -> click 'Install'
5. Enter your Mac's password -> click 'Install Software'
6. Wait for 'The installation was successful' -> click 'Close'
7. 'Do you want ...' -> click 'Keep', you may need 'VirtualBox_Uninstall.tool'
8. Command-W to close the 'VirtualBox' window
9. Eject the 'VirtualBox' volume

> __UNINSTALLING:__ If you need to uninstall VirtualBox, double-clicking the
> 'VirtualBox_Uninstall.tool' just shows a popup saying '...Apple cannot check
> it for malicious software'. Instead of double-clicking, Control-click
> 'VirtualBox_Uninstall.tool' -> click 'Open', which shows a similar popup but
> this time with an 'Open' button. Also note that after
> 'VirtualBox_Uninstall.tool' finishes running, you may still need to delete:
> - ~/Library/LaunchAgents/org.virtualbox.vboxwebsrv.plist
> - ~/Library/Preferences/org.virtualbox.app.VirtualBox.plist
> - ~/Library/Preferences/org.virtualbox.app.VirtualBoxVM.plist
> - ~/Library/Saved Application State/org.virtualbox.app.VirtualBox.savedState/
> - ~/Library/Saved Application State/org.virtualbox.app.VirtualBoxVM.savedState/
> - ~/Library/VirtualBox/

## II. Optionally, hide VirtualBox 7's 'Notification Center' overlay

VirtualBox 7 often shows a 'Notification Center', overlaying the right side of
the virtual machine's window. Here's a slightly hacky way to prevent it from
appearing:

1. In the Finder, Command-Shift-U, to open the 'Utilities' folder
2. Start typing 'ter...' to find the 'Terminal' app -> Command-O to open it
3. Type `VBoxManage getextradata global GUI/SuppressMessages` and Return
4. You should see 'No value set!'. This confirms that VBoxManage exists, and
   shows that the following step has not already been done.
5. Type `VBoxManage setextradata global GUI/SuppressMessages all` and Return
6. Press the UpArrow key twice to show `VBoxManage getextradata ...` and Return
7. This time you should see 'Value: all', confirming that `setextradata` worked
8. Command-Q to quit Terminal -> Command-W to close the 'Utilities' window

VirtualBox 7 has a second 'Notification Center', which overlays the right side
of the 'VirtualBox Manager'. There doesn't currently seem to be a way to keep
it hidden, but luckily it rarely gets in the way.

## III. Create a new virtual machine in 'Guided Mode'

1. In the Finder, Command-Shift-H to open your home folder in a new window
2. You should see there is currently no 'VirtualBox VMs' folder
3. Command-Shift-A to open the 'Applications' folder
4. Start typing 'virt...' to find the 'VirtualBox' app -> Command-O to open it
5. You should see the 'Oracle VM VirtualBox Manager' window
6. Click the 'New' icon
7. Name: MS-DOS-6.22
8. Folder: [keep the default, '/Users/&lt;my-username>/VirtualBox VMs']
9. ISO Image: &lt;not selected> [the default]
10. Type: Other [selected automatically when you type 'MS-DOS' in the Name]
11. Version: DOS [selected automatically when you type 'MS-DOS' in the Name]
12. Click 'Next'
13. Base Memory: 128 MB -> Processors: 1 -> click 'Next'
14. Under 'Create a Virtual Hard Disk Now', Disk Size: 256.00 MB -> click 'Next'
15. Click 'Finish' - you should see 'MS-DOS-6.22 Powered Off' in the sidebar

> __HOT TIP:__ When naming a new virtual machine, only use digits 0-9, uppercase
> and lowercase letters A-Z and a-z, hyphens '-', dots '.' and underscores '_'.
> VirtualBox will use the virtual machine name as a filename, and characters
> outside the range [-._0-9A-Za-z], can cause headaches later on. The space
> character ' ' is especially bad.

## IV. Create an initial snapshot

1. Click the menu icon to the right of 'MS-DOS-6.22' -> click 'Snapshots'
2. You should just see 'Current State'
3. Command-Tab to the 'Finder' -> Command-Shift-H to open your home folder
4. Double-click the new 'VirtualBox VMs' folder
5. You should see it contains just one item, the 'MS-DOS-6.22' folder
6. Double-click the 'MS-DOS-6.22' folder - you should see three files:
   - MS-DOS-6.22.vbox (2 KB)
   - MS-DOS-6.22.vbox-prev (1 KB)
   - MS-DOS-6.22.vdi (2.1 MB)
7. Command-Tab to 'VirtualBox' -> click the 'Take' icon
8. Snapshot Name: 'Initial State'
9. Snapshot Description: 'Before starting up for the first time.' -> click 'Ok'
10. You should see 'Initial State' in the snapshots list, with 'Current state'
    nested underneath
11. Command-Q to quit VirtualBox Manager (good practice before backing up)
12. In the 'MS-DOS-6.22' folder, you should see that a 'Snapshots' folder has
    been added. Inside is a .vdi file (2.1 MB).
13. Command-UpArrow, to the 'VirtualBox VMs' folder
14. Control-click the 'MS-DOS-6.22' folder -> 'Compress 'MS-DOS-6.22'
14. Note that the compressed .zip file is tiny - only about 9 KB. Compression
    works really well on the Virtual Disk Image (.vdi) files, because they're
    currently empty. Your .zip archive files will be much bigger later, when the
    .vdi files contain data.
15. Rename the 'MS-DOS-6.22.zip' file to [ms-dos-6.22-initial-state.zip
    ](./install-ms-dos-6.22/ms-dos-6.22-initial-state.zip)
16. Back up the 'ms-dos-6.22-initial-state.zip' file

> __DOWNLOAD:__ The 'ms-dos-6.22-initial-state.zip' archive is available [here
> ](./install-ms-dos-6.22/ms-dos-6.22-initial-state.zip).

## V. Grab your assets!

1. In the 'VirtualBox VMs' folder, Command-Shift-N to create a new folder
2. Command-Shift-N -> type: 'MS-DOS-6.22-Assets' -> press the Return key
3. Download [the .7z file](#prerequisites-and-resources) to your new 'MS-DOS-6.22-Assets' folder
4. Double-click the .7z file to extract the folder containing floppy-disk images
5. You should see the 'Microsoft MS-DOS 6.22 Plus Enhanced Tools (3.5)' folder
6. Double-click that folder - you should see nine files, all dated late 2014:
   - Disk1.img (1.5 MB)
   - Disk1.jpg (108 KB)
   - Disk2.img (1.5 MB)
   - Disk2.jpg (106 KB)
   - Disk3.img (1.5 MB)
   - Disk3.jpg (105 KB)
   - Microsoft MS-DOS 6.22 Plus Enhanced Tools (3.5).txt (233 B)
   - Suppdisk.img (1.5 MB)
   - winworldpc.com.txt (691 B)

## VI. Get to the 'Microsoft MS-DOS 6.22 Setup' screen

![The MS-DOS 6.22 Setup screen, after pressing F5 to turn the background black.
](./install-ms-dos-6.22/install-ms-dos-6.22-vi-720x454.gif)

1. Command-Option-D to toggle the macOS dock into view
2. Click on the 'VirtualBox' icon to reopen the VirtualBox Manager
3. If not already selected, click _once_ on 'MS-DOS-6.22' to select it
4. Click its 'Settings' icon -> Storage
5. Under 'Controller: Floppy', click 'Empty'
6. Under 'Attributes', click the small floppy disk icon on the right
7. Click 'Choose a disk file...'
8. For any popups like '“VirtualBox” would ... folder.', click 'Don’t Allow'
9. Select 'Disk1.img' from the folder of unzipped .7z files -> click 'Open'
10. You should see 'Empty' has changed to 'Disk1.img' -> click 'OK'
11. Note that 'Disk1' is a [boot disk](https://en.wikipedia.org/wiki/Boot_disk).
    VirtualBox has already created an appropriate [
    BIOS](https://en.wikipedia.org/wiki/BIOS) on the virtual machine, and it
    expects a boot disk to be inserted when it powers up.
12. Click the 'Start' icon (the main part, not the small down-arrow)
13. You should see a white on blue page headed 'Microsoft MS-DOS 6.22 Setup'
14. At the top of your screen, 'View' -> 'Virtual Screen 1' -> 'Scale to 150%'
15. Press fn-F5 to turn the background black. This is less painful on the eyes,
    and also confirms that VirtualBox's keyboard-capturing is working.
16. Click on the MS-DOS window - your mouse pointer will actually disappear,
    because MS-DOS is text only!
17. If 'You have clicked ...' appears, tick 'Do not show...' -> click 'Capture'
18. By default, the 'host key' is the Left Command key. Press it now to check
    that you can get your mouse cursor back.

> __HOT TIP:__ VirtualBox virtual machines run as their own individual
> application, named 'VirtualBox VM'. You could actually quit the 'VirtualBox
> Manager' app, and all your virtual machines would continue running.

## VII. Install MS-DOS 6.22 from the virtual floppy-disks

![The MS-DOS 6.22 Setup screen, after completing the installation, and before
restarting.](./install-ms-dos-6.22/install-ms-dos-6.22-viI-720x568.gif)

1. The 'Microsoft MS-DOS 6.22 Setup' screen should be saying 'press ENTER'
2. Press the Return key. Some keyboards have an Enter key in addition to a
   Return key, and some apps treat them differently. But in this context, the
   MS-DOS virtual machine treats a Return-press the same as an Enter-press.
3. Keep 'Configure unallocated disk space (recommended)' selected
4. Press the Return key again
5. Step VI.9. above inserted 'Setup Disk 1' into drive A, so press Return
6. Wait for 'Formatting drive C' to complete (about 30 seconds)
7. Optionally, edit 'Date/Time', 'Country' or 'Keyboard Layout' -> press Return
8. Accept the default 'C:\DOS' by pressing Return
9. Wait for 'Please insert ... Setup Disk #2' to appear (about 30 seconds)
10. Press the 'host key' to get your mouse cursor back
11. Click the small floppy disk icon in the row of icons under the VM window
12. Click 'Choose a disk file...'
13. For any popups like '“Terminal” would like ... folder.', click 'Don’t Allow'
14. Select 'Disk2.img' from the folder of unzipped .7z files -> click 'Open'
15. Press Return -> wait for 'Please ... Setup Disk #3' to appear (~30 seconds)
16. This time, choose 'Disk3.img' -> click 'Open'
17. Press Return -> wait for 'Remove disks ...' to appear (~30 seconds)
18. Click the floppy disk icon again -> click 'Remove disk from virtual drive'
19. Press Return -> you should see a 'MS-DOS Setup Complete' message
20. Press Return

## VIII. Deal with an unresponsive restart

This fix can be used if, after a restart, you see these two lines:  
`ata0 master: VBOX HARDDISK ATA-6 Hard-Disk (256 MBytes)`  
`ata1 master: VBOX CD-ROM ATAPI-6 CD-ROM/DVD-ROM`

1. Although you can see a blinking cursor, the keyboard is be unresponsive, so
   press the 'host key'
2. At the top of your computer's screen, click 'Machine' -> 'Reset (Host-R)'
3. On a 'Do you really ...' popup -> tick 'Do not show...' -> click 'Reset'
4. You should see the following line below `ata1 master: ...`:  
   `iPXE (http://ipxe.org) E2:00.0 E2001.10 E200`  
5. At the top left corner, click 'VirtualBox VM' -> 'Quit VirtualBox VM'
6. On the 'You want to:' popup -> click 'Power off the machine' -> click 'OK'
7. Command-Tab one or more times, to the go to 'VirtualBox'
8. You should see 'MS-DOS 6.22 Powered Off' selected in the sidebar
9. Click the 'Start' icon (the main part, not the small down-arrow)

## IX. Create a snapshot after the first successful restart

1. You should see:  
   `Starting MS-DOS...`  
   `HIMEM is testing extended memory...done.`  
   `C:\>C:\DOS\SMARTDRV.EXE /X`  
   `C:\>`  
2. Type 'DIR' at the prompt, to check that MD-DOS is working -> press Return.  
   MS-DOS commands are not case sensitive, so 'dir' works the same as 'DIR'.
3. You should see a summary of drive C, containing '5 file(s)'
4. Press HostKey-T to take a snapshot
5. Snapshot Name: After 1st Successful Restart
6. Snapshot Description: Installed MS-DOS 6.22 and invoked 'DIR'. -> click 'Ok'
7. Press the 'host key', Command-Tab to the VirtualBox Manager
8. Click the menu icon to the right of 'MS-DOS 6.22' -> click 'Snapshots'
9. You should see 'After 1st Successful Restart' listed on the right. The
   'Current State (changed)' means that your virtual machine has continued
   running after you took the snapshot.
10. Command-Tab back to 'VirtualBox VM'
11. HostKey-Q -> choose 'Save the machine state' -> click 'OK'
12. In VirtualBox Manager, you should see 'Saved' under 'MS-DOS 6.22'
13. Click 'Current State (changed)' to select it -> click the 'Discard' icon
14. At the 'Are you sure ...' popup, click 'Discard'
15. Command-Q to quit VirtualBox Manager (good practice before backing up)
16. In the 'Snapshots' folder in the 'MS-DOS-6.22' folder, you should see two
    .vdi files (2.1 MB and 9.4 MB) and a .sav file (666 KB).
17. Follow the steps in section IV. above, to create
    [ms-dos-6.22-after-1st-successful-restart.zip
    ](./install-ms-dos-6.22/ms-dos-6.22-after-1st-successful-restart.zip)
16. Back up the 'ms-dos-6.22-after-1st-successful-restart.zip' file (~4 MB)

> __DOWNLOAD:__ The 'ms-dos-6.22-after-1st-successful-restart.zip' archive is
> available [here
> ](./install-ms-dos-6.22/ms-dos-6.22-after-1st-successful-restart.zip).

---

### Next:

Now that you have a fully working MS-DOS 6.22, you can install
[Windows 3.11](https://en.wikipedia.org/wiki/Windows_3.1x).

Check out the next how-to guide in this series:  
- [How to: Install Windows 3.11 on VirtualBox](
  ./install-windows-3.11-on-virtualbox.md)
