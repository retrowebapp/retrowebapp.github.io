## How to:
# Install Windows 3.11 on VirtualBox

__Ruth Webster, June 19th 2023__

[Windows 3.11,](https://en.wikipedia.org/wiki/Windows_3.1x) was the last 16-bit
release of the Windows operating system. At RetroWebApp we use it for testing
websites and web apps on the first JavaScript web browsers, like [Netscape 2
](https://en.wikipedia.org/wiki/Netscape_Navigator_2) and [Internet Explorer 3.
](https://en.wikipedia.org/wiki/Internet_Explorer_3)

This how-to guide will help you install and set up an
[OEM](https://en.wikipedia.org/wiki/Original_equipment_manufacturer) version of
Windows for Workgroups 3.11, as a virtual machine on [Oracle VirtualBox.
](https://en.wikipedia.org/wiki/VirtualBox) When it's up and running, check out
the next guide in this series, [How to: Install the Earliest Web Browsers on
Windows 3.](./install-the-earliest-web-browsers-on-windows-3.md)

---

### TL;DR:

__The result of following this guide,__
__'windows-3.11-with-cd-rom-and-network-drivers.zip', is available__ [__here__
](./install-windows-3.11/windows-3.11-with-cd-rom-and-network-drivers.zip)

---

### Manual driver installation:

There are no [Guest Additions](https://www.virtualbox.org/manual/ch04.html)
available for Windows 3, so you'll need to install drivers manually. This guide
explains how to install and configure drivers for:
- VirtualBox's virtual CD-ROM
- Network connection and the Internet

Many thanks to Glijnos on the [virtualbox.org forums
](https://forums.virtualbox.org/index.php) for posting the [excellent tutorial
](https://forums.virtualbox.org/viewtopic.php?t=102121) that this guide is
based on. That tutorial covers some topics not included here, including sound
card installation, and increasing the screen resolution to 1024×768.

---

### Resources and prerequisites:

- 'Microsoft Windows for Workgroups 3.11 (OEM) (3.5-1.44mb)' from
  [winworldpc.com
  ](https://winworldpc.com/download/01c38063-1542-c38a-11c3-a7c29d255254)
  (~12 MB)
- Or; the same file renamed 'windows-fwg-3.11-oem.7z', from [here
  ](./install-windows-3.11/windows-fwg-3.11-oem.7z)
- 'wfw311-cd-rom-and-network-drivers.img.zip', from [here
  ](./install-windows-3.11/wfw311-cd-rom-and-network-drivers.img.zip) (unless
  you want to create it yourself, see [IV.,
  ](#iv-create-a-virtual-floppy-disk-containing-the-cd-rom-and-network-drivers)
  below)
- Ideally, a computer running macOS - but Linux, Solaris or Windows are ok
- VirtualBox 7.0 or later, with a freshly installed MS-DOS 6.22 virtual
  machine - see the previous guide, [How to: Install MS-DOS 6.22 on VirtualBox
  ](./install-ms-dos-6.22-on-virtualbox.md)

VirtualBox is free to download and use. Windows 3.11 can be considered
[abandonware](https://en.wikipedia.org/wiki/Abandonware) - Microsoft stopped
supporting it at the end of 2001. Consequently, Windows 3 drivers can also be
considered abandonware.

This how-to guide is targeted at macOS Monterey on an Intel MacBook. Other
recent macOS versions should work very similarly.

If you're on Linux, Solaris or Windows, just ignore the Mac-specific parts of
this guide. The VirtualBox parts should work similarly on all platforms.

---

## I. Clone an MS-DOS 6.22 virtual machine in 'Guided Mode'

1. In the Finder, Command-Shift-H to open your home folder in a new window
2. Double-click the 'VirtualBox VMs' folder. If it's not there, you may need to
   [install VirtualBox.
   ](./install-ms-dos-6.22-on-virtualbox.md#i-install-virtualbox)
3. If there is no 'MS-DOS-6.22' folder inside the 'VirtualBox VMs' folder, you
   can either:
   - Download and unzip it from [here
     ](./install-ms-dos-6.22/ms-dos-6.22-after-first-successful-restart.zip)
   - Or; follow the [previous how-to guide
     ](./install-ms-dos-6.22-on-virtualbox.md) to build it from scratch
4. In the Finder, Command-Shift-A to open the 'Applications' folder
5. Start typing 'virt...' to find the 'VirtualBox' app -> Command-O to open it
6. You should see the 'Oracle VM VirtualBox Manager' window
7. If the 'MS-DOS-6.22' virtual machine is not listed in the sidebar,
   Command-A -> double-click 'MS-DOS-6.22.vbox' which can be found inside the
   'MS-DOS-6.22' folder
8. If not already selected, click _once_ on 'MS-DOS-6.22' to select it
9. Its current snapshot should be 'After First Successful Restart', and it should
   currently be 'Powered Off'
10. Command-O to open the 'Clone Virtual Machine' window
11. Name: Windows-3.11
12. Path: [keep the default, '/Users/&lt;your-username>/VirtualBox VMs']
13. MAC Address Policy: [keep the default, 'Include only NAT ... addresses']
14. Don't tick 'Keep Disk Names' or 'Keep Hardware UUIDs' -> click 'Next'
15. 'Full clone' should be selected -> click 'Next'
16. 'Current machine state' should be selected -> click 'Finish'

## II. Convert the clone to a Windows 3 virtual machine

1. If not already selected, click _once_ on 'Windows-3.11' to select it
2. Click the 'Settings' icon -> if the 'Type:' and 'Version:' fields are
   grayed-out, it's because the virtual machine is not 'Powered Off', so you'll
   need to click 'Cancel' and power it off yourself
3. Type: Microsoft Windows -> Version: Windows 3.1
4. Click 'Description' -> 'Windows for Workgroups 3.11 (OEM)'
5. Note that 'Invalid settings detected' has appeared. If you hover over the
   small icon, it should tell you that the video memory is less than the minimum
   required.
6. Click the 'Display' icon -> Video Memory: 32 MB
7. Note that 'Invalid settings detected' has disappeared
8. Click the 'System' icon -> Base Memory: 256 MB
9. Click 'OK'
10. You should see that the icon to the left of 'Windows-3.11' has changed
    from the 'DOS' logo to the '3.1' logo
11. Click the menu icon to the right of 'Windows-3.11' -> click 'Snapshots'
12. The only snapshot should be 'Current State' -> click 'Attributes' (you may
    need to double-click 'Current State' first)
13. Name: Initial State
14. Description: After cloning from MS-DOS-6.22, and before starting up for the
    first time.
15. Click 'Take'
16. You should see 'Initial State' in the snapshots list, with 'Current State'
    nested underneath
17. Command-Q to quit VirtualBox Manager (good practice before backing up)
18. In the 'Windows-3.11' folder, you should one .vdi file (2.1 MB) inside the
    'Snapshots' folder
19. Optionally, delete the 'Logs' folder inside the 'Windows-3.11' folder
20. Control-click the 'Windows-3.11' folder -> 'Compress “Windows-3.11”'
21. Rename the 'Windows-3.11.zip' file to [windows-3.11-initial-state.zip
    ](./install-windows-3.11/windows-3.11-initial-state.zip)
22. Back up the 'windows-3.11-initial-state.zip' file (~3.5 MB)

> __DOWNLOAD:__ The 'windows-3.11-initial-state.zip' archive is available [here
> ](./install-windows-3.11/windows-3.11-initial-state.zip).

## III. Extract the Windows 3.11 floppy disk images into a new 'Assets' folder

1. In the 'VirtualBox VMs' folder, Command-Shift-N to create a new folder
2. Type: 'Windows-3.11-Assets' -> press the Return key
3. Download [Microsoft Windows for Workgroups 3.11 (OEM) (3.5-1.44mb).7z
   ](#resources-and-prerequisites) or [windows-fwg-3.11-oem.7z
   ](#resources-and-prerequisites) to your new
   'Windows-3.11-Assets' folder
4. Double-click the .7z file to unzip it, creating a
   'Microsoft Windows for Workgroups 3.11 (OEM) (3.5-1.44mb)' folder
5. Double-click the 'Microsoft Windows for Workgroups 3.11 (OEM) (3.5-1.44mb)'
   folder - you should see eight .img files dated late 1993, plus a folder of
   .jpg files, and the standard winworldpc.com.txt file:
   - Disk1.img (1.5 MB)
   - Disk2.img (1.5 MB)
   - Disk3.img (1.5 MB)
   - Disk4.img (1.5 MB)
   - Disk5.img (1.5 MB)
   - Disk6.img (1.5 MB)
   - Disk7.img (1.5 MB)
   - Disk8.img (1.5 MB)
   - artwork/ (1.4 MB)
   - winworldpc.com.txt (691 B)
6. Command-UpArrow back to the 'Windows-3.11-Assets' folder

## IV. Create a virtual floppy disk, containing the CD-ROM and network drivers

Since there are no Guest Additions for Windows 3, the virtual machine can't
use a shared folder. It can use VirtualBox's virtual floppy disk drive though,
and the five files needed to get the CD-ROM and network connection working
fit comfortably onto one 1.5 MB floppy disk.

1. If you download and unzip 'wfw311-cd-rom-and-network-drivers.img.zip' from
   [here](./install-windows-3.11/wfw311-cd-rom-and-network-drivers.img.zip),
   and place the .img file in the 'Windows-3.11-Assets' folder, then you can skip the following steps
2. Otherwise, Command-Shift-N to make a new folder inside 'Windows-3.11-Assets'
3. Type 'WFW311 CD-ROM and Network drivers' -> press Return
4. Download the 'Oak Technology CD-ROM Driver' file 'AOATAPI.SYS' from
   [fsck.technology
   ](https://fsck.technology/software/Microsoft/Windows%20x86%20Install%20Media/Microsoft%20Windows%203.x/Microsoft%20Windows%203.11%20VMWare%20Drivers/CD%20ROM/)
   (~34 KB), and move it into your 'WFW311 CD-ROM and Network drivers' folder
5. Command-Comma to open 'Finder Preferences'
6. Click 'Sidebar' -> make sure 'External disks' is ticked -> Command-W
7. Download 'Microsoft TCP-IP-32 For Windows 3.1 (3.5)' from [winworldpc.com
   ](https://winworldpc.com/download/47c2a8c3-8fc3-8118-c39a-11c3a4e284a2)
   (~1 MB), and unzip 'Microsoft TCP-IP-32 For Windows 3.1 (3.5).7z'
8. Double-click the 'Disk01.img' file -> click the 'TCP' volume in the sidebar
9. Click the 'TCP32B.EXE' file to select it -> Command-C to copy it
10. Command-[ back to 'Windows-3.11-Assets' -> Control-click
    'WFW311 CD-ROM and Network drivers' -> click 'Paste Item'
11. Using the 'ZIP' link at [archive.org/details/pcntn3.386
    ](https://archive.org/details/pcntn3.386), download and unzip
    'PCNET.ZIP' (~562 KB)
12. Double-click the 'PCNET' folder
13. Double-click the 'WFW311' folder
14. Command-A to select all -> Command-C to copy them
15. Command-[ back to 'Windows-3.11-Assets' -> Control-click
    'WFW311 CD-ROM and Network drivers' -> click 'Paste 3 Items'
16. Command-Shift-A -> type 'virt' to find the 'VirtualBox' app -> Command-O
17. Double-click the Powered Off 'Windows-3.11' in the sidebar, to start it
    running
18. Note that the small 'Floppy' icon at the bottom of the window is grayed-out,
    which indicates that the virtual floppy disk drive is currently empty
19. When `C:\>` and a blinking `_` appears, type `DIR A:` -> press Return
20. You should see:  
    `General failure reading drive A`  
    `Abort, Retry, Fail?`
21. Click the small 'Floppy' icon at the bottom of the window (you may need to
    press the 'host key' to get your mouse cursor back)
22. Click 'Choose/Create a disk image...' -> click the 'Create' icon
23. Next to 'File Path', click the down-arrow icon -> click 'Other...'
24. Save As: 'wfw311-cd-rom-and-network-drivers.img' -> choose the
    'Windows-3.11-Assets' folder -> click 'Save'
25. Click 'Create' [default Size and Format 1.44M and FAT12 are fine]
26. Under 'Not Attached' you should see that
    'wfw311-cd-rom-and-network-drivers.img' is selected -> click 'Choose'
27. At the `Abort, Retry, Fail?` prompt, type `R` to retry reading the disk
28. You should see:
    ```
    Volume in drive A has no label
     Volume Serial Number is 4C9A-FC13 (a unique ID assigned to each disk)  
     Directory of A:\
    
    File not found
    ```
    ...which means that the disk was read, but contains no files
29. Command-Tab to the 'Finder' (you may need to click outside the vm window 
    first) -> open the 'Windows-3.11-Assets' folder
30. Double-click the new 'wfw311-cd-rom-and-network-drivers.img' file
31. Control-click the text 'Untitled' (or sometimes 'Untitled 1') of the volume
    which has appeared under 'Locations' in the sidebar
32. Click 'Rename “Untitled”' (or “Untitled 1”, etc) -> type 'WFW3DVRS' ->
    press Return
33. Double-click 'WFW311 CD-ROM and Network drivers' -> Select these five files:
    - AOATAPI.SYS
    - OEMSETUP.INF
    - PCNTN3.386
    - PCNTND.DOS
    - TCP32B.EXE
34. Drag the five files onto the 'WFW3DVRS' volume in the sidebar.  
    Note that your mouse cursor becomes a '+' in a green circle, with '5' in a
    red circle, just before you complete the drag. This indicates you are
    copying (not moving) five files.
35. Click the 'WFW3DVRS' volume in the sidebar, and check the files are there
36. Command-Tab back to 'VirtualBox VM', and type `DIR A:` at the prompt, again
37. This time you should see:  
    ```
    Volume in drive A is A
     Volume Serial Number is 4C9A-FC13
     Directory of A:\
    
    AOATAPI  SYS        34,262 06-19-23  11:32a (today's date and time)
    OEMSETUP INF         1,500 06-30-95   2:00a
    PCNTN3   386        35,935 06-30-95   2:00a
    PCNTND   DOS        52,768 06-30-95   2:00a
    TCP32B   EXE       690,031 06-01-08   2:54p
            5 file(s)        814,496 bytes
                             620,544 bytes free
    ```
    ...Note that this provides an almost 'live' way of passing files to MS-DOS.
38. HostKey-Q -> select 'Power off the machine'
39. Tick 'Restore current snapshot ‘Initial State’' -> click 'OK'
40. Command-Tab to 'VirtualBox' -> Command-Q to quit
41. Command-Tab to the 'Finder' -> click the 'eject' icon next to 'WFW3DVRS'
42. Control-click the 'wfw311-cd-rom-and-network-drivers.img' file
43. Click 'Compress “wfw311-cd-rom-and-network-drivers.img”'
44. Back up the 'wfw311-cd-rom-and-network-drivers.img.zip' file (~739 KB)

## V. Copy the CD-ROM and network drivers to the virtual hard drive

1. Command-Tab to the 'Finder' -> Command-Shift-A -> type 'virt' to find the
   'VirtualBox' app -> Command-O to open it
2. Double-click the Powered Off 'Windows-3.11' in the sidebar, to start it
   running
3. When `C:\>` and a blinking `_` appears, type `DIR` -> press Return
4. You should see:  
   ```
   Volume in drive C is MS-DOS_6
    Volume Serial Number is 56D0-5D09
    Directory of C:\
   
   DOS          <DIR>         06-16-23  11:40a
   COMMAND  COM        54,645 05-31-94   6:22a
   WINA20   386         9,349 05-31-94   6:22a
   CONFIG   SYS            71 06-16-23  11:42a
   AUTOEXEC BAT            78 06-16-23  11:42a
           5 file(s)         64,143 bytes
                        261,828,608 bytes free
   ```
5. Type `MD WFW3DVRS` -> press Return -> type `DIR` and Return again
6. You should see that a new directory has been made in the hard drive's root:  
   ```
   WFW3DVRS     <DIR>         06-19-23  12:11p
   ```
7. Type `CD WFW3DVRS` to 'change directory' into it
8. The prompt should now be `C:\WFW3DVRS\>` -> type `DIR A:` -> press Return
9. The virtual floppy disk drive is currently empty, so you should see:  
    `General failure reading drive A`  
    `Abort, Retry, Fail?`
10. Click the small grayed-out 'Floppy' icon at the bottom of the window (you may
    need to press the 'host key' to get your mouse cursor back)
11. Click 'Choose a disk file...' -> double-click
    'wfw311-cd-rom-and-network-drivers.img' in the 'Windows-3.11-Assets' folder
12. At the `Abort, Retry, Fail?` prompt, type `R` to retry reading the disk
13. You should see:
    ```
    Volume in drive A is A
     Volume Serial Number is 4C9A-FC13
     Directory of A:\
    
    AOATAPI  SYS        34,262 06-19-23  11:32a
    OEMSETUP INF         1,500 06-30-95   2:00a
    PCNTN3   386        35,935 06-30-95   2:00a
    PCNTND   DOS        52,768 06-30-95   2:00a
    TCP32B   EXE       690,031 06-01-08   2:54p
            5 file(s)        814,496 bytes
                             621,568 bytes free
    ```
14. Type `COPY A:\ .` -> press Return
15. You should see:  
    ```
    A:\AOATAPI.SYS
    A:\OEMSETUP.INF
    A:\PCNTN3.386
    A:\PCNTND.DOS
    A:\TCP32B.EXE
            5 file(s) copied
    ```
16. Note that 'TCP32B.EXE' will unzip 33 files into whatever the current
    directory is, when it's executed. If that's the 'WFW3DVRS' directory, it
    will try to overwrite 'OEMSETUP.INF'.
17. Type `MD TCP32B` -> press Return -> Type `CD TCP32B` -> press Return
18. Now you can type `..\TCP32B.EXE | MORE` to unzip the files -> press Return
19. Using `| MORE` lets us see the output of `..\TCP32B.EXE`, page-by-page:
    ```
    PKSFX (R)   FAST!   Self Extract Utility   Version 2.04g   02-01-93
    Copr. 1989-1993 PKWARE Inc. All Rights Reserved. Registered version
    PKSFX Reg. U.S. Pat. and Tm. Off.

    Searching EXE: C:/WFW3DVRS/TCP32B/../TCP32B.EXE
      Inflating: ARP.EXE       -AV
      Inflating: FTP.EXE       -AV
      Inflating: HOSTS.SAM     -AV
    ...
      Inflating: SERVICES      -AV
    -- More --
    ```
    -> press Return to show the next page of output
    ```
      Inflating: TCP32UI.DLL   -AV
      Inflating: TELNET.EXE    -AV
      Inflating: TELNET.HLP    -AV
    ...
      Inflating: WSTCP.386     -AV
    
    Authentic files Verified!   # MEP325
    MICROSOFT CORPORATION
    ...
    -- More --
    ```
    -> press Return to get back to the prompt
20. Type `CD \` to go back to the top of the hard drive -> press Return
21. Click the small 'Floppy' icon again -> 'Remove disk from virtual drive'
22. Press HostKey-T to take a snapshot
23. Snapshot Name: After Copying WFW3DVRS to Drive C
24. Snapshot Description: WFW311 CD-ROM and Network drivers, ready to install.
25. Click 'Ok' -> HostKey-Q -> select 'Power off the machine'
26. Tick 'Restore current snapshot ‘After Copying ... Drive C’' -> click 'OK'
27. In VirtualBox Manager, you should see 'Saved' under 'Windows-3.11'
28. Click 'Current State (changed)' to select it -> click the 'Discard' icon
29. At the 'Are you sure ...' popup, click 'Discard'
30. You should see that the virtual machine is now 'Powered Off'
31. Command-Q to quit VirtualBox Manager (good practice before backing up)
32. Command-Tab to 'Finder' -> Command-Shift-H -> double-click 'VirtualBox VMs'
33. Optionally, delete the 'Logs' folder inside the 'Windows-3.11' folder
34. Control-click the 'Windows-3.11' folder -> click 'Compress “Windows-3.11”'
35. Press Return -> name it [windows-3.11-after-copying-wfw3dvrs-to-drive-c.zip
    ](./install-windows-3.11/windows-3.11-after-copying-wfw3dvrs-to-drive-c.zip)
36. Back up the 'windows-3.11-after-copying-wfw3dvrs-to-drive-c.zip' file
    (~7.7 MB)

## VI. Install the CD-ROM driver

> __RETRO TIP__ Edits you make to 'AUTOEXEC.BAT' or 'CONFIG.SYS' don't
> take effect until MS-DOS has rebooted.

1. Command-Tab to the 'Finder' -> Command-Shift-A -> type 'virt' to find the
   'VirtualBox' app -> Command-O to open it
2. Double-click the Powered Off 'Windows-3.11' in the sidebar, to start it
   running
3. When `C:\>` and a blinking `_` appears, type `DIR WFW3DVRS` -> press Return
4. You should see tha six files copied to the virtual hard drive earlier - see
   [V.,](#v-copy-the-cd-rom-and-network-drivers-to-the-virtual-hard-drive) above
5. Note that the small 'IDE' icon to the left of the 'Floppy' icon is
   grayed-out, which indicates that the virtual CD-ROM drive is currently empty
6. At the top of your computer's screen, click 'Devices' ->
   'Insert Guest Additions CD image...' (Windows 3 cannot actually install Guest
   Additions, but the CD image is still handy for testing the CD-ROM driver)
7. The 'IDE' icon should now be light blue, which means a virtual CD is inserted
8. Type `DIR D:` -> press Return -> you should see an error message:  
   `Invalid driver specification`  
   ...confirming that MS-DOS cannot currently see VirtualBox's virtual CD-ROM
9. Type `EDIT CONFIG.SYS` -> press Return, to start editing [DOS's primary
   configuration file](https://en.wikipedia.org/wiki/CONFIG.SYS)
10. You should see a funky text editor with a blue background and four lines:
    ```
    DEVICE=C:\DOS\SETVER.EXE
    DEVICE=C:\DOS\HIMEM.SYS
    DOS=HIGH
    FILES=30
    ```
11. Press the DownArrow key four times, so that the blinking `_` cursor is on a
    new line
12. Type `DEVICE=C:\WFW3DVRS\AOATAPI.SYS /D:IDECD000`
13. Press Alt -> press Return -> press S, to save
14. Press Alt -> press Return -> press X, to exit
15. You should be back in the regular MS-DOS environment
16. Type `EDIT AUTOEXEC.BAT` -> press Return, to start editing
    [DOS's list of commands to run on startup
    ](https://en.wikipedia.org/wiki/AUTOEXEC.BAT)
17. This time you should see the following five lines:
    ```
    C:\DOS\SMARTDRV.EXE /X
    @ECHO OFF
    PROMPT $p$g
    PATH C:\DOS
    SET TEMP=C:\DOS
    ```
18. Press the DownArrow key five times, to reach a new line
19. Type `C:\DOS\MSCDEX.EXE /D:IDECD000`
20. Press Alt -> press Return -> press X -> press Y, to save and exit
21. You should be back in the normal MS-DOS environment again
22. HostKey-Q -> select 'Power off the machine'
23. 'Restore current snapshot ...' _must NOT be ticked_ -> click 'OK'
24. Double-click the Powered Off 'Windows-3.11' in the sidebar, to start it
    running again. A ['cold' reboot
    ](https://en.wikipedia.org/wiki/Reboot#Cold_versus_warm_reboot) like this
    is generally more reliable than a 'warm' Control-Alt-Delete reboot.
25. You should see that the CD-ROM driver outputs some new boilerplate, as
    MS-DOS starts up:
    ```
    CD-ROM Device Driver for IDE (Four Channels Supported)
    (C)Copyright Oak Technology Inc. 1993-1996
    Driver Version     : V340
    Driver Name        : IDECD000
    Transfer Mode      : Programmed I/O
    Drive 0:  Port= 170 (Secondary Channel), Master  IRQ= 15
    Firmware Version   : 1.0
    ```
    ...Additionally, a new line appears above the `C:\>` prompt:  
    `Drive D: = Driver IDECD000 unit 0`
26. The 'IDE' icon should still be light blue, meaning the Guest Additions
    virtual CD is still inserted
27. Type `DIR D:` -> press Return -> you should see a dozen or so files, which
    confirms that VirtualBox's virtual CD-ROM is now working correctly
28. Click the 'IDE' icon -> 'Remove disk from virtual drive' (you may need to
    press the 'host key' to get your mouse cursor back)
29. Type `DIR D:` -> press Return -> a different error message appears this time:  
    `CD101: Not ready reading drive D`
30. At the `Abort, Retry, Fail?` prompt, type `A` to get the `C:\>` prompt back
31. Type `CLS` -> press Return, to clear the screen ready for another snapshot
32. Press HostKey-T to take a snapshot
33. Snapshot Name: After Installing CD-ROM Driver
34. Snapshot Description: Oak Technology CD-ROM driver 'AOATAPI.SYS' is working.
35. Click 'Ok' -> HostKey-Q -> select 'Power off the machine'
36. Tick 'Restore current snapshot ‘After Installing CD-ROM Driver’' ->
    click 'OK'
37. In VirtualBox Manager, you should see 'Saved' under 'Windows-3.11'
38. Click 'Current State (changed)' to select it -> click the 'Discard' icon
39. At the 'Are you sure ...' popup, click 'Discard'
40. You should see that the virtual machine is now 'Powered Off'
41. Command-Q to quit VirtualBox Manager (good practice before backing up)
42. Command-Tab to 'Finder' -> Command-Shift-H -> double-click 'VirtualBox VMs'
43. Optionally, delete the 'Logs' folder inside the 'Windows-3.11' folder
44. Control-click the 'Windows-3.11' folder -> click 'Compress “Windows-3.11”'
45. Press Return -> name it [windows-3.11-after-installing-cd-rom-driver.zip
    ](./install-windows-3.11/windows-3.11-after-installing-cd-rom-driver.zip)
46. Back up the 'windows-3.11-after-installing-cd-rom-driver.zip' file
    (~9.5 MB)

## VII. Install Windows 3.11

![Windows 3.11 showing the 'Main' program group, during 'Windows Setup'.
](./install-windows-3.11/install-windows-3.11-vii-470x340-poster.gif)  
_Windows 3.11 showing the 'Main' program group, during 'Windows Setup'._  
Watch the screencast: [MP4 (recommended)
](./install-windows-3.11/install-windows-3.11-vii-940x680-12fps.mp4) or
[Animated GIF
](./install-windows-3.11/install-windows-3.11-vii-470x340-12fps.gif)

1. Command-Tab to the 'Finder' -> Command-Shift-A -> type 'virt' to find the
   'VirtualBox' app -> Command-O to open it
2. Double-click the Powered Off 'Windows-3.11' in the sidebar, to start it
   running
3. Click the small 'Floppy' icon at the bottom of the window (you may need to
   press the 'host key' to get your mouse cursor back)
4. Click 'Choose a disk file...' -> double-click 'Disk01.img' in 
   'Microsoft Windows for Workgroups 3.11 (OEM) (3.5-1.44mb)' in the
   'Windows-3.11-Assets' folder
5. After `C:\>`, type `A:` -> press Return -> type `SETUP` -> press Return
6. The 'Welcome to Windows for Workgroups 3.11 Setup' page should appear
7. Press Return -> The 'There are two types of Setup' page should appear
8. Press Return for 'Express Setup' -> wait for 'Please ... Disk 2' to appear
9. Click the small 'Floppy' icon at the bottom of the window (you may need to
   press the 'host key' to get your mouse cursor back)
10. Click 'Choose a disk file...' -> select 'Disk02.img' -> click 'Open'
11. At this point your mouse cursor should start working in the virtual machine,
    appearing as a white Windows-style arrow. The UI should switch from MS-DOS
    to graphical, with a big 'Windows Setup' heading in the background. The
    setup will appear to hang for a moment while it attempts to detect your
    network card - this delay is normal.
12. Wait for 'Thank you for ...' to appear (~20 seconds)
13. Your Full Name: [Enter your name here]
14. Company: [Optionally enter your company's name here]
15. Product Number: [Can be left blank]
16. Click 'Continue' -> 'Please verify that ...' should appear
17. Click 'Continue' -> wait for 'Please ... Disk 3' to appear (~5 seconds)
18. This time, select 'Disk03.img' -> click 'Open'
19. Click 'Continue' -> wait for 'Please ... Disk 4' to appear (~5 seconds)
20. Repeat for Disks 4, 5 and 6, until you see 'Printer Installation'
21. Press Return to skip installing a printer -> 'Network Setup' should appear
22. Press Return, because there is 'No Network Installed' yet
23. Click the small 'Floppy' icon again -> 'Remove disk from virtual drive'
24. 'Set Up Applications' should appear -> press Return to choose 'MS-DOS Editor'
25. On 'Set Up Applications' again -> press Return to choose 'FTP PING Utility'
26. If 'System Error Cannot read from drive D.' appears, keep clicking the 'Cancel' button until it disappears
27. When 'Setup can now run a short tutorial ...' appears, the installation is
    complete. You can try out the tutorial for some retro fun, or click
    'Skip Tutorial' to go straight to 'Exit Windows Setup'.
28. Clicking the 'Restart' button sometimes leads to an E200 error (see
    [part VIII. of 'How to: Install MS-DOS 6.22 on VirtualBox'
    ](./install-ms-dos-6.22-on-virtualbox.md#viii-deal-with-an-unresponsive-restart)
    ). So instead, HostKey-Q -> select 'Power off the machine'.
29. 'Restore current snapshot ...' _must NOT be ticked_ -> click 'OK'
30. Command-Tab to 'VirtualBox' -> double-click 'Windows-3.11' to restart it
31. Wait for the `C:\>` prompt to appear -> type `WIN` -> press Return
32. Windows 3.11 should open, showing 'Program Manager' and 'Main'
33. Press HostKey-T to take a snapshot
34. Snapshot Name: Fresh Windows 3.11 Install
35. Snapshot Description: Restart after installing Windows for Workgroups 3.11.
36. Click 'Ok' -> HostKey-Q -> select 'Power off the machine'
37. Tick 'Restore current snapshot ‘Fresh Windows 3.11 Install' -> click 'OK'
38. Command-Q to quit VirtualBox Manager (good practice before backing up)
39. Command-Tab to 'Finder' -> Command-Shift-H -> double-click 'VirtualBox VMs'
40. Optionally, delete the 'Logs' folder inside the 'Windows-3.11' folder
41. Control-click the 'Windows-3.11' folder -> click 'Compress “Windows-3.11”'
42. Press Return -> name it [windows-3.11-fresh-windows-3.11-install.zip
    ](./install-windows-3.11/windows-3.11-fresh-windows-3.11-install.zip)
43. Back up the 'windows-3.11-fresh-windows-3.11-install.zip' file
    (~23.5 MB)

## VIII. Install the Network drivers

![Entering 'Network Names' while installing Network drivers on Windows 3.11.
](./install-windows-3.11/install-windows-3.11-viii-470x340-poster.gif)  
_Entering 'Network Names' while installing Network drivers on Windows 3.11._  
Watch the screencast: [MP4 (recommended)
](./install-windows-3.11/install-windows-3.11-viii-940x680-12fps.mp4) or
[Animated GIF
](./install-windows-3.11/install-windows-3.11-viii-470x340-12fps.gif)

1. Command-Tab to the 'Finder' -> Command-Shift-A -> type 'virt' to find the
   'VirtualBox' app -> Command-O to open it
2. Double-click the Saved 'Windows-3.11' in the sidebar, to restore the
   most recent snapshot
3. Windows 3.11 should already be running, showing 'Program Manager' and 'Main'
4. Double-click 'Windows Setup' -> press Alt -> press O -> press N
5. You should see the 'Network Setup' panel -> press N for 'Networks'
6. On the 'Networks' panel -> press I for 'Install Microsoft Windows Network'
7. 'No additional network' should already be selected -> press Return for 'OK'
8. Back on the 'Network Setup' panel again -> press Return
9. On the 'Add Network Adapter' panel, 'Unlisted or Updated Network Adapter'
   should already be selected -> press Return
10. The 'Install Driver' panel should appear, with its default path `A:\`
11. Press Delete -> type `C:\WFW3DVRS` -> press Return
12. Windows 3.11 should have identified a Network driver, and show the
    'Unlisted or Updated Network Adapter' panel. This lists one driver,
    'Advanced Micro Devices PCNET family'. It's selected, so -> press Return
13. Base I/O Port: [The default, `0x0000`, is fine] -> press Return
14. Interrupt Value: `9` (any number seems to work here) -> press Return
15. DMA Channel Value: [The default, `Auto_Scan`, is fine] -> press Return
16. User Name: [Choose a short memorable name]
17. Workgroup: [Keep the default, `WORKGROUP`]
18. Computer Name: [Choose a short memorable name] -> press Return
19. You should see 'An error ... file NDIS.386.' - what it really means is that
    you need to insert Windows 3.11 installation Disk 7
20. Click the small 'Floppy' icon at the bottom of the window (you may need to
    press the 'host key' to get your mouse cursor back)
21. Click 'Choose a disk file...' -> double-click 'Disk07.img' in 
    'Microsoft Windows for Workgroups 3.11 (OEM) (3.5-1.44mb)' in the
    'Windows-3.11-Assets' folder
22. Press Return to 'Retry' -> wait for 'Insert ... Disk 8' to appear
23. This time, select 'Disk08.img' -> Press Return for 'OK'
24. Wait for the 'Windows setup has modified ...' panel to appear (~5 seconds)
25. Press Return for 'OK'
26. Click the small 'Floppy' icon again -> 'Remove disk from virtual drive'
27. Clicking the 'Restart Computer' button sometimes leads to an E200 error (see
    [part VIII. of 'How to: Install MS-DOS 6.22 on VirtualBox'
    ](./install-ms-dos-6.22-on-virtualbox.md#viii-deal-with-an-unresponsive-restart)
    ). So instead, HostKey-Q -> select 'Power off the machine'.
28. 'Restore current snapshot ...' _must NOT be ticked_ -> click 'OK'
29. Command-Tab to 'VirtualBox' -> double-click 'Windows-3.11' to restart it
30. Wait for the `C:\>` prompt to appear -> type `WIN` -> press Return
31. You should see 'Welcome to Windows for Workgroups', with your 'Logon Name'
    filled in and the cursor blinking in the 'Password' field -> press Return
32. For 'There is no password-list file ...' -> press Y for 'Yes'
33. Keep 'New Password' and 'Confirm New Password' blank -> press Return
34. Double-click the program group 'Network'
35. The program 'Network Setup' should be selected -> press Return to open it
36. Under 'Network Drivers:' you should see
    'Advanced Micro Devices PCNET family [NDIS2/NDIS3]' selected.
    Under that should be 'Microsoft NetBEUI' and
    'IPX/SPX Compatible Transport with NetBIOS'.
37. Press D to open the 'Network Drivers' panel -> press P for 'Add Protocol...'
38. On the 'Add Network Protocol' panel, 'Unlisted or Updated Protocol'
    should already be selected -> press Return for 'OK'
39. The 'Install Driver' panel should appear, as before
40. Press Delete -> type `C:\WFW3DVRS\TCP32B\` -> press Return
41. Windows 3.11 should have identified the protocol, and show the
    'Unlisted or Updated Protocol' panel. This lists one driver,
    'Microsoft TCP/IP-32 3.11b'. It's selected, so -> press Return
42. You should see it added under 'IPX/SPX Compatible Transport with NetBIOS'
43. Press Return to close -> press Return for 'OK'
44. On the 'Microsoft TCP/IP configuration' panel -> tick the
    'Enable Automatic DHCP configuration' checkbox
45. For 'Microsoft TCP/IP' panel -> press Y to enable DHCP -> Press Return
46. The 'Network setup ... PROTOCOL.000.' panel should appear -> press Return
47. Clicking the 'Restart Computer' when the 'You need to quit Windows ...'
    panel appears sometimes leads to an E200 error. Instead, HostKey-Q ->
    select 'Power off the machine'.
48. 'Restore current snapshot ...' _must NOT be ticked_ -> click 'OK'
49. Command-Tab to 'VirtualBox' -> double-click 'Windows-3.11' to restart it
50. You should see some new boilerplate, which wasn't there before:
    ```
    C:\>C:\WINDOWS\net start
    The command completed successfully.
  
    C:\>C:\DOS\SMARTDRV.EXE /X
    MSCDEX Version 2.23
    Copyright (C) Microsoft Corp. 1986-1993. All rights reserved.
    ```
51. Note that `PING` is installed now, but will not work in the 'real' MS-DOS
    environment (and will actually hang the virtual machine)
52. Wait for the `C:\>` prompt to appear -> type `WIN` -> press Return
53. After Windows 3.11 starts, double-click the 'MS-DOS Prompt' icon in the
    'Main' program group
54. Note that the newly installed `PING` should _usually_ work here in the
    'sub-Windows' MS-DOS environment, and should _usually_ let you break out of
    it using Control-C.
55. Wait for the `C:\>` prompt to appear -> type `PING g.co` -> press Return
56. _Usually,_ if your Internet connection is working, you should see:
    ```
    Pinging g.co [172.217.17.238] with 32 bytes of data:
    Reply from 172.217.17.238: bytes=32 time<10ms TTL=31
    Reply from 172.217.17.238: bytes=32 time<10ms TTL=31
    Reply from 172.217.17.238: bytes=32 time<10ms TTL=31
    Reply from 172.217.17.238: bytes=32 time<10ms TTL=31
    ```
    ...which confirms that your virtual machine will be able to browse web pages
    on the Internet. If nothing happens, Control-C _usually_ returns you to the
    `C:\>` prompt, where you can try again with a different domain.
57. Command-Tab to the 'Finder' (you may need to press the 'host key' to get
    your mouse cursor back)
58. Command-Shit-U to show the 'Utilities' folder -> start typing 'term...' to
    find the 'Terminal' utility -> Command-O to open it
59. Type `ifconfig en0 | awk '$1 == "inet" {print $2}'` -> press Return ->
    select and Command-C to copy the IP address, something like `192.168.1.100`
60. Command-Tab back to 'VirtualBoxVM' -> type `PING <Your IP address>`, for
    example `PING 192.168.1.100` -> click Return
61. _Usually_ you should see something like:
    ```
    Pinging [192.168.1.100] with 32 bytes of data:
    Reply from 192.168.1.100: bytes=32 time<10ms TTL=31
    Reply from 192.168.1.100: bytes=32 time<10ms TTL=31
    Reply from 192.168.1.100: bytes=32 time<10ms TTL=31
    Reply from 192.168.1.100: bytes=32 time<10ms TTL=31
    ```
    ...which confirms that your virtual machine will be able to browse web pages
    on your computer's 'localhost'. If nothing happens, Control-C _usually_
    returns you to the `C:\>` prompt, where you can try again.
62. Type `EXIT` -> press Return to go back to the Windows environment
63. Press HostKey-T to take a snapshot
64. Snapshot Name: With CD-ROM and Network Drivers
65. Snapshot Description:
    ```
    Successfully installed:
    - Oak Technology CD-ROM driver 'AOATAPI.SYS'
    - Microsoft Windows for Workgroups 3.11 (OEM)
    - 'Advanced Micro Devices PCNET family' Network drivers
    - 'Microsoft TCP/IP-32 3.11b' Network driver
    ...and successfully `PING`ed localhost and the Internet.
    ```
66. Click 'Ok' -> HostKey-Q -> select 'Power off the machine'
67. Tick 'Restore current snapshot ‘With ... Network Drivers’' -> click 'OK'
68. In VirtualBox Manager, you should see 'Saved' under 'MS-DOS 6.22'
69. Command-Q to quit VirtualBox Manager (good practice before backing up)
70. Command-Tab to 'Finder' -> Command-Shift-H -> double-click 'VirtualBox VMs'
71. Optionally, delete the 'Logs' folder inside the 'Windows-3.11' folder
72. Control-click the 'Windows-3.11' folder -> click 'Compress “Windows-3.11”'
73. Press Return -> name it [windows-3.11-with-cd-rom-and-network-drivers.zip
    ](./install-windows-3.11/windows-3.11-with-cd-rom-and-network-drivers.zip)
74. Back up the 'windows-3.11-with-cd-rom-and-network-drivers.zip' file
    (~27 MB)

> __DOWNLOAD:__ The 'windows-3.11-with-cd-rom-and-network-drivers.zip' archive
> is available [here
> ](./install-windows-3.11/windows-3.11-with-cd-rom-and-network-drivers.zip).

---

### Next:

Windows 3.11 is a great choice for testing your website or web app on the first
generation of 16 bit Windows web browsers. To start surfing the World Wide Web
like it's 1995, check out our next how-to guide:
- [How to: Install the Earliest Web Browsers on Windows 3
  ](./install-the-earliest-web-browsers-on-windows-3.md)
