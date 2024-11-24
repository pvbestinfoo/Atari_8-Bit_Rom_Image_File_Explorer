# Atari 8-bit Rom Image File Explorer (ARIFE) introduction

***Atari 8-bit Rom Image File Explorer*** is based upon *ATR Image Explorer* github project from Rossumur (and peterbarrett1967 ?), see: atr_image_explorer.htm at https://github.com/rossumur/esp_8_bit

***Atari 8-bit Rom Image File Explorer*** is there : https://pvbestinfoo.github.io/atari8-bit_rom_image_file_explorer.html

The original github.io webpage link for *ATR Image Explorer* is: https://rossumur.github.io/esp_8_bit/atr_image_explorer.htm

The purpose of the modifications and upgrades that I propose in ARIFE are:
- fix the bugs,
- improvement implemented functions,
- add new features,
- and not to cancel any existing features of ATR Image Explorer.

20 years ago, I coded a Windows 32 application called *ARFD* for *Atari ROM File Designer* (see my website http://pvb.free.fr/Atari/atari_pg4.htm) that I wanted to port to other systems .
Then I discovered *ATR Image Explorer* from Rossumur in a link on _Gury's Atari 8-bit Forever Portal_ (see https://gury.atari8.info/pc_tools.php), it was so awesome, and thanks to Javascript, it runs on every platforms... so I decided to take some of my time to improve it.

Thanks to Rossumur, peterbarrett1967 and all previous contributors!

# Atari 8-bits and 5200 ROM cartridge management: a great improvement! 

ARIFE considers the following ROM image file extensions: _'.a52'_, _'.rom'_, _'.bin'_ and _'.car'_.

## ROM cartridge management feature

ARIFE features a great improvement, the ***ROM image file management***, including the Atari 5200 ROM support, and the ROM type selection as per the A800 emulator list standard (see https://github.com/atari800/atari800/blob/master/DOC/cart.txt), but only for the 75 first types that are more often.

For instance, if you load a ROM image file like _'Bounty...rom'_, the system does not really know what this 40KB ROM is about in terms of stucture, load address, layout of memory banks...
So, the drop-down list selection menu lets you select the possible ROM type from the list, where only 40KB size ROM type entries are filtered and can be selected.

![image](https://github.com/user-attachments/assets/236164c6-198c-45ec-b30b-acf3983b561b)

So the obvious choice will be to select the Type_07 for an Atari 5200 ROM, or Type_18 for an Atari 800/XL/XE ROM:

![image](https://github.com/user-attachments/assets/e81a189a-7824-4a99-bfc5-f64fcf062dca)

To see how to check that Type_18 is the right one, see [Modifying and save a CART cartridge type ROM image file](https://github.com/pvbestinfoo/Atari-8-bit-Rom-File-Explorer/edit/main/README.md#modify-and-save-a-cart-cartridge-type-rom-image-file).

Then, ARIFE will display all the following ROM image information on screen:
- Size and number of banks, and corresponding memory addresses
- ROM cartridge vectors and flag
- ROM cartridge name and copyright date for an Atari 5200 ROM (if it exists)
- The dump of all banks of the ROM cartridge, with hyperlink for quick navigation

So try it !

## Modify and save a CART cartridge type ROM image file

As an useful feature, ARIFE allows you to modify ROM image file (_'.a52'_, _'.rom'_, _'.bin'_ extensions) into a known-type "CART ROM file" which extension is _'.car'_.

"CART ROM files" are automatically identified and properly loaded in A800 or Altirra emulators, and in retroarch emulationstation (recalbox, retrobat...)

As an example : if a cartridge type is unknown, the emulationstation will not launch the ROM image, and the Altirra emulator will show a menu to choose relevant type, like this:

![image](https://user-images.githubusercontent.com/123185835/229629896-c3a63b09-7014-4c32-937d-a0c40854228c.png)

In order to avoid this, thanks to ARIFE, you can set and save the relevant cartridge type, and then get an automatic loading of the ROM image in emulators.

This is how to proceed:

**1/ Load the raw ROM image file (for example _Ballbla...com_):**

![image](https://user-images.githubusercontent.com/123185835/229630444-45ee8e68-be04-4e0a-af6b-043e7226a6e3.png)

**2/ Select relevant type:**
When several types are available and you are not sure of the right one, the simplest would be to test each of them by repeating the present operation until it works in Altirra emulator:

![image](https://github.com/user-attachments/assets/27ac9658-ca5c-4be4-9fb3-6e4dfc730183)

**3/ Click "Download New Cart" (extension ".car" is added to the file):**

![image](https://user-images.githubusercontent.com/123185835/229630947-6345aafd-3ff7-46ee-a150-3013a6aadb82.png)

**4/ Then test it in Altirra: the CART file should automatically load:**

![image](https://user-images.githubusercontent.com/123185835/229631152-fc483a99-e350-43ba-ac81-702e56ff1075.png)

It runs fine!

**5/ Test it in Retrobat emulationstation for instance.**
Note that the CART extension shall be in the list of Atari800 system extensions in the _'.emulationstation/es_systems.cfg'_ file.

![image](https://github.com/user-attachments/assets/1df0221c-0f2c-4582-81d3-b894fe354137)

If not, you shall add the '.car' and '.CAR' extensions in the config file.

**6/ If it is OK, the emulation station will directly launch and run the proper system configuration.**
For instance, test it with _'Donkey K...rom.car'_:

![image](https://github.com/user-attachments/assets/b5dac63d-2cf9-408f-be0a-61040aac5549)

It runs fine!

## The OS ROM support

An additionnal ARIFE feature is to support the OS ROM type and display it. This is possible by keeping the default Type_00, and ROM data are set to a bank in the OS ROM address area, accordingly to its size, as follows:
- 2KB ROM file will be set as an Atari 5200 OS ROM, loaded into $F800
- 8KB ROM file will be set as an ATARI BASIC ROM, loaded into $A000
- 10KB ROM file will be set as an ATARI OS A/B ROM, loaded into $D800
- 16KB ROM file will be set as an ATARI OS XL/XE ROM, loaded from $C000

For instance, when loading _'ATA..XL.ROM'_ image file, ARIFE will show its hexdump from $C000 address and then you can to disassemble it:

![image](https://github.com/user-attachments/assets/b11d78fe-533d-40b1-86ba-54ffab6139b4)

...

![image](https://github.com/user-attachments/assets/87ad4184-343c-454f-ac56-e03a47e5889c)

Please note that OS ROM vectors are not correctly displayed, because the information shown are for standard ROM cartridge where the last 6 bytes stand for:
- 'BFFA, BFFB': CARTCS" = CARTRIDGE COLD START ADDRESS
- 'BFFC': CART = CARTRIDGE AVAILABLE FLAG BYTE
- 'BFFD': CARTFG = CARTRIDGE FLAG BYTE
- 'BFFE, BFFF': CARTAD = CARTRIDGE START VECTOR ADDRESS.

For an OS ROM, the last 6 bytes of the OS ROM shall be read as the 6502 CPU resident vectors:
- '$FFFA, FFFB': NMIVEC = NMI NON MASKABLE INTERRUPT OS ROM VECTOR
- '$FFFC, FFFD': RESETVEC = RESET OS ROM VECTOR"
- '$FFFE, FFFF': IRQVEC = IRQ INTERRUPT REQUEST OS ROM VECTOR".

# The disassembly feature improvement

## ROM dump disassembly

Of course, the disassembly routine improvement applies to the ROM image: just click on the ***<< Toggle Disass/HexDump >>*** button on top of the ROM bank, and the hexdump will be replaced by the disassembly listing of the bank. You can click again to display back the hexdump.

![image](https://github.com/user-attachments/assets/0a87b498-c590-485d-b6fc-4687c1f1baab)

## Menu for Display & Disassembly options

ARIFE now features a Display & Disassembly option menu:

![image](https://github.com/user-attachments/assets/0d7ac773-1f7c-4c44-a054-fe56e3e48577)

The Display & Disassembly options are:
- *Listing display with Atari Font*: just try it!
- *Show destination address in hyper links*: a great improvement to follow the JMP, JSR and relative jumps in the 6502 code disassembly listing, just try and easily navigate in the program listing!
- *Accept to disassemble up to 2 BRK instructions*: means that BRK instructions are accepted and will be considered as valid code in the disassembly listing (otherwise a BRK instruction breaks the disassembly listing and is shown in a data bloc).
- *Show address with Rom bank number as BK00..FF*: useful for ROM disassembly with multiple banks at same addresses. The ROM bank number will be added in front of the disassembly address.
- *Show program code flags (info for dev)*: useful for ARIFE development about the 6502 Atari code disassembly routine verification, see below and the Javascript code of ARIFE for more information.

## Disassembly with A5200 equates

ARIFE disassembly routine features the Atari 5200 equates addresses, instead of Atari 800/XL/XE ones, whenever an Atari 5200 file is loaded.
Atari 5200 equate reference are taken from:
- Altirra Source Code
- AtariAge forum https://forums.atariage.com/topic/90339-atari-5200-equates-anyone/
- DAN B Atari 5200 webpages: https://atarihq.com/danb/a5200.shtml

Please note that Dan B also proposes a commented OS 5200.ROM listing on his website which is great: see https://atarihq.com/danb/files/5200BIOS.txt

Atari 5200 equates are set on when the Atari file is either:
- a 2KB ROM size
- an '.a52' Atari file extension
- the selection of a type_XX coresponding to an Atari 5200 ROM type
Following is an example of the Atari 5200 OS ROM disassembly with Atari 5200 equates:

![image](https://github.com/user-attachments/assets/fbc03498-0909-402a-87be-cb4bf9e42121)
![image](https://github.com/user-attachments/assets/4fa69601-a042-4eb1-a216-15e3744a911b)

## Disassembly routine improvement

The disassembly routine has been improved, notably as follows:
- Make the difference on memory equate name when Writing or Reading OS chip address
- Manage the disassembly stop at the end of memory or at the end address: ARIFE will display _"!End of data or max address reached!"_
- Validation of the disassembly blocs with a recursive function
- Accept relative jump instruction only on certain conditions (like BNE+BEQ, CLC+BCC, LDA#$00+BEQ)
- Cancel (invalidate) jump on a target address that points to an invalid instruction

You can check how the disassembly routine runs by displaying the program code flags (see 'Display & Disassembly option menu' above)

**For instance**, a 0x80 bit in the flag means that this is an entry address, so a bloc of disassembly listing should start at this address.
If the code does not set the 0x80 flag with an Entry Point, a JUMP, a JSR or a relative jump instructions, then this entry address is ignore.
As a consequence a bloc of disassembly should always start with an entry address.

Let's visualy compare previous and actual ARIFE display on same file:

![image](https://github.com/user-attachments/assets/92ab9538-5234-4132-b23e-0014e0f9e50f)

You can check the improved details by compairing the ARIFE result with previous version of ATR Image Explorer on your favorite file disassembly listing.

## Extract menu: Disassembly of extracted data

When a program on boot disk is loaded, only the boot sectors are automatically disassembled and displayed.

In the next example, let's open a boot disk program. The disassembly listing is displayed for the 2 sectors loaded on boot. Sectors #3 and above are not disassembled:

![image](https://github.com/user-attachments/assets/fa18b7c0-3cd0-4bcb-a3ff-8dcddb43f5f7)
![image](https://github.com/user-attachments/assets/85c47e5d-d11e-49b2-9bbe-fca0ce3c0063)

From the above example, the disassembly of the remaining code in sectors #3 and above is accessible thanks to the **ARIFE Extract feature**.
Click on the ***\<\<E>>*** on the left floater menu:

![image](https://github.com/user-attachments/assets/2ba6542b-cabf-4da4-aa93-30baa7362cb4)

Then ARIFE displays:
- the full sector hexdump in the _'show'_ windows, with \[sector:offset] index
- _Extract data from disk and disassemble Menu_: this menu allows to select the sector start, stop, and starting address for the disassembly
- _ReShow full HexDump_: this button reset the disassembly and display the full sector hexdump.

By reading the 6502 code in the boot disassembly listing, the boot loads 3 sectors, from sector #3, into address $2100:

![image](https://github.com/user-attachments/assets/fb60860a-7505-4071-a0b7-650f147dc9c2)
![image](https://github.com/user-attachments/assets/8bcfbbc5-682f-4399-b495-e5b20b4780ae)

So let's disassemble the corresponding extract, as follows:

![image](https://github.com/user-attachments/assets/3f441824-388a-4b61-a7e7-499748c52b4b)

# The XFD/PRO vs ATR disk image conversion

The principle of _ATR Image Explorer_ is to work with ATR disk image in memory, so the XFD/PRO image disks are automatically converted to ATR as soon as they are loaded.

This makes possible to save image disk converted into ATR disk image file, for this use the ***<< Download ATR file >>*** button.

Furthermore the file type drop-down menu can be used to force changing file type (this feature is a work in progress).

In case of an ATR file or XFD file loaded in ARIFE that would be smaller than a real Atari disk in size, then it will be converted into a full size ATR disk image in memory.

# The listing saving features

ARIFE now features several possibilities to save the listing for your own purpose, by clicking the corresponding button.

![image](https://github.com/user-attachments/assets/49a9816b-bebb-433b-a51b-2d3520993b1c)

The display window is the HTML element \<pre id="show"\>, at the bottom right in the ARIFE page - let's call it the _'show'_ window. This is the window that can be saved.

![image](https://github.com/user-attachments/assets/159a1cec-2877-4175-ab06-c3068cf0d9ff)

Saving possibilities are among the following:
- Save listing as text: save all the text displayed in the _'show'_ window in simple raw '.txt' file.
- Save listing as .html (without html style): save all the text in a simple HTML file, without any particular CSS style. This allows to save the hyperlinks of the disassembly listing, within a simple HTML file.
- Save listing as .html (Atari font included): save all the text in a HTML file, with all the CSS style and the embeded Atari font style. Just try it !

# The ATR/XFD... disk image analysis and information display

For the DOS system information reference, there is a good website named AtariWiki: https://atariwiki.org/wiki/Wiki.jsp?page=Articles#section-Articles-DiskOperatingSystemsDOS

But the best webpages are the Atariki.krap.pl from http://atariki.krap.pl/index.php/Formaty_system%C3%B3w_plik%C3%B3w

Translated by google from polish, they give a lot of detailled information regarding DOS TOC, directories, file format... Thank you people for your work!

Thanks to these information, ARIFE now supports DOS1 and DOS3.

## Disk, BOOT information and DOS directory

ARIFE now display more accurate caracteristics of the disk, the boot information according to DOS, and a DOS directory in the _'show'_ window.

![image](https://github.com/user-attachments/assets/2766bcc7-1d40-45bf-a49b-c05949c6ee3b)

As shown on previous screenshots, ARIFE displays on top of the _'show'_ window:
- the disk information of the Image disk, like "Image has 1040 ($410) sectors of 128 bytes - 1050 Enhanced Density (Medium Density)"
- the identified DOS type with the size of corresponding bloc in sector count, like "DOS2.5 disk has been identified, 1 bloc is 1 sector"
- the free blocs and the total blocs on disk, like "DOS disk has 0 ($0) free blocs, among a total of 1010 ($3F2) blocs".

The directory that is displayed on the left in white on blue is the official valid directory handled by ARIFE.
The directory displayed in the _'show'_ window is a more detailed one. For example:

![image](https://github.com/user-attachments/assets/eea8bd61-3886-4b44-b3f1-f178d7eca361)

The empty and non-compliant files in directory entries are listed and commented, they are not displayed in the blue valid directory.
As you can see in ARIFE, the $03 & $43 file flags are correctly supported for DOS2.5 disk with 1040 sectors. For example:

![image](https://github.com/user-attachments/assets/aad1d504-6f65-41f6-9aea-303f7c0b5e01)


## DOS1 support

Current version of ARIFE handles flawlessly the DOS1 disk system:

![image](https://github.com/user-attachments/assets/99e33e86-6037-4e46-921a-41c401081794)

## DOS3 support

Current version of ARIFE handles flawlessly the DOS3 disk system:

![image](https://github.com/user-attachments/assets/1b0f8811-27e6-4f11-b357-12ed1e7ef7fc)

## DOS file segments support improvement

The management of the Atari executable files and their segments have been improved as follows:
1. Management of _'DOS.SYS'_ file and other _'.SYS'_ files that have no $FFFF header
2. Handle more than one $FFFF header in an executable file
3. Display in red the last inconsistent segment when buggy
4. Handle and display properly the one byte segment
5. Handle of the Entry Points segments for file execution vectors file in the disassembly listing.

**1/ Example of '.sys' file without header:**

On the example, the default loading address is $700 for the _'superloa.sys'_ file. Note that only _DOS.SYS_ is loaded at the known $7CB address.

![image](https://github.com/user-attachments/assets/4c8cae8e-0255-49f4-8215-ec2af27c253f)

**2/ Example of multi header Executable DOS file:**

![image](https://github.com/user-attachments/assets/b9ff02df-7799-451c-9438-c5860f811937)

**3/Example of the last buggy segment:**

![image](https://github.com/user-attachments/assets/e8c114aa-aa37-480f-9204-3ccd1468b58f)
![image](https://github.com/user-attachments/assets/53c527fc-10b7-4a92-90bf-a055f9d472ca)

A last buggy segment usualy occurs when the last byte of the last sector, corresponding to the data length in the last sector, is wrong.

**4/Example of one byte segment:**

![image](https://github.com/user-attachments/assets/f131c0f1-92ec-417b-888f-16034b04d4ef)

# TO DO

What can we do for next update of ARIFE:
- improve the Extract fonction
- check and correct behaviour on changing file type from the drop-down menu selection
- support DOS XE by creating a class like SPARTA
- add hyperlinks to start sector for all the valid files in directory
- test and adjust code for MyDOS subdirectories (I don't have ones to check it)
- Implement the Search menu feature
- For ROM, add the ROM bank number in front of banks hexdump.
- OS ROM vectors to display as Entry Points

You can check ARIFE Javascript inline code and comments for other ideas, and come back to me!

Enjoy!

>PVBest inFoo Oct/2023

>see www.pvbest.com/atari




