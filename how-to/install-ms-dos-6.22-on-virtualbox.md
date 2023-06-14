## How to:
# Install MS-DOS 6.22 on VirtualBox

__Ruth Webster, June 14th 2023__

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

If you're on Linux, Solaris or Windows, steps 'I. Install VirtualBox' and 'II.
Open VirtualBox' will be very different for you. But the steps after that should
be quite easy to follow, if you ignore the Mac-specific keyboard shortcuts.

---

### This guide uses one placeholder:

- Substitute `/Users/kimdoe/VirtualBox VMs` with your 'Default Machine Folder'

---

## I. Install VirtualBox

1. Download VirtualBox 7.0 or later from [virtualbox.org](
   https://www.virtualbox.org/wiki/Downloads) - about 130 MB
2. Double-click the downloaded 'VirtualBox-7.0.8-156879-OSX.dmg'
3. Double-click 'VirtualBox.pkg' in the window which pops up
4. Click 'Continue' -> click 'Install'
5. Enter your Mac's password -> click 'Install Software'
6. Wait for 'The installation was successful' -> click 'Close'
7. 'Do you want ...' -> click 'Keep' if you may need 'VirtualBox_Uninstall.tool'
8. Close the 'VirtualBox' window, and eject the 'VirtualBox' volume

## II. Open VirtualBox

1. Command-Shift-A to open the 'Applications' folder
2. Start typing 'virtu...' to find the 'VirtualBox' app
3. Command-O to open VirtualBox

## III. Create a new virtual machine in 'Guided Mode'

1. You should see the 'Oracle VM VirtualBox Manager' window
2. Click the 'New' icon
3. Name: MS-DOS 6.22
4. Folder: `/Users/kimdoe/VirtualBox VMs` [keep your own default]
5. ISO Image: &lt;not selected> [the default]
6. Type: Other -> Version: DOS [the defaults, after you entered the Name]
8. Click 'Next'
9. Base Memory: 128 MB -> Processors: 1 -> click 'Next'
10. Under 'Create a Virtual Hard Disk Now', Disk Size: 256.00 MB -> click 'Next'
11. Click 'Finish' - you should see 'MS-DOS 6.22 Powered Off' in the sidebar

## IV. Grab your assets

1. Command-Tab one or more times, to the go to the Finder
2. Command-Shift-G, to open the 'Go to Folder' popup
3. Start typing '~/Virtu...' to find the 'VirtualBox VMs' folder
4. Press the Return key - you should see the 'MS-DOS 6.22' folder
5. Double-click the 'MS-DOS 6.22' folder - you should see three files:
    - MS-DOS 6.22.vbox (2 KB)
    - MS-DOS 6.22.vbox-prev (1 KB)
    - MS-DOS 6.22.vdi (2.1 MB)
6. Command-UpArrow, to show your `/Users/kimdoe/VirtualBox VMs/` folder again
7. Command-Shift-N -> type: 'MS-DOS 6.22 Assets' -> press the Return key
8. Download [the .7z file](#prerequisites-and-resources) to your new 'MS-DOS 6.22 Assets' folder
9. Double-click the .7z file to extract the folder containing floppy-disk images
