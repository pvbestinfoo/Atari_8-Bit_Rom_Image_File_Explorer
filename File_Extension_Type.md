# File Extension Types in Atari 8-bit Rom Image File Explorer

This is the file type extension as used in the Atari 8-bit Rom Image File Explorer Tool.

The list of supported type extension is displayed at the Tool's openning.

If a file is loaded in the tool with an extension a type is not listed, the Tool will try to guess it according to its data.

If it not succeed, then the default extension DAT is set to the file in order to display it as Hexdump.

![image](https://github.com/user-attachments/assets/1d5d966d-1f70-4348-8c2f-4787387a9c55)

## DAT extension files

DAT is the default extension and the file is displayed as Hexdump if no known type has been guessed according to its data.

## Disk Images types

ATR, ATX, PRO, XFD, DSK are disk image file. Usually this is the kind of file you will load intot the Tool to explore its contents.

* ATR contains the specific Nick 16-bytes header.
* DSK is a raw copy of disk image sectors. Change its type to XFD to explore its content.

## ARC file

ARC file is like ZIP file. It contains compressed file.

## Languages (formated text files)

### BAS file

"BAS" file is an ATARI BASIC source code file.

This file is not directly readable as it contains compressed and encoded BASIC data.
It is readable, editable, modifyable only in the BASIC programs. Usually, on your Atari, at BASIC Editor prompt, you should use the LOAD "D:TOTO.BAS" command to load the file in the BASIC program interface.

The Atari 8-bit Rom Image File tool is able to load and decode the BASIC file, display it in an HTML Editor, and then save your modification in a "LST" file.

Obviously,on Atari, there are many BASIC programs, like the XL/XE OS resident BASIC ROM, the XL/XE BASIC, the MICROSOFT BASIC... so the "BAS" file encoded source code may differ.

### LST file

"LST" file shoud be an ATARI BASIC text file, or a file used to save source listing of any language, but in reality this is a text file without control char.

This file is plain readable text on an Atari text editor, and also readable in BASIC programs.

But the LST file display will be limited on a Client OS system like WINDOWS, since it contains ATARI ASCII control chars that is not understood on Client, like the $9B ATARI char for a line-feed (return), whereas WINDOWS Client uses the ASCII UTF+0A char for a line feed.

### M65 file

"M65" file is an Assembler Source code file, usually used by Atari MAC65 Assembler. 

This file is not directly readable as it contains compressed and encoded M65 data.
It is readable, editable, modifyable only in the M65 Editor program.

The Atari 8-bit Rom Image File tool is able to load and decode the M65 file, display it in an HTML Editor, and then save your modification *in a "LST" file*.

### ASM, LIS, DOC, ATA, TXT, BAT, MAN files

These files are plain text files. They may contain inverse chars and graphic chars, but no specific Atari control char.

Only the End-Of-Line (RETRUN) $9B char should be used for the line feed, as the other control char are not displayable.

## Font & Graphics

### FNT, CHAR Font files

FNT and CHR are font files. They should contain a bloc of $400 bytes as a charset.

### GR7, GR8, GR9, GR10, MIC, MCP, APC, PLM, PZM, ILC, INP, CIN, PIC, RAW, SCR, IST, RIP, HIP, TIP Graphics files

GR7, GR8, GR9, GR10, MIC, MCP, APC, PLM, PZM, ILC, INP, CIN, PIC, RAW, SCR, IST, RIP, HIP, TIP are graphics or pictures files

## SYS, OBJ, XEX, EXE, COM Executable Atari DOS Files & BIN Dump Files

### Executable Code Header

What ever the Atari DOS revision, the executable Atari DOS files must have the $FFFF DOS executable code header. This is a file signature located in their first 4 bytes of data, that is the $FF $FF two bytes header.

Then the following data in the file are called segments. Segments feature a header with bytes indicating the address where to load data in memory, and then the bytes of data themselves.

A segment header is 4 bytes: 2 bytes for the start address where to load data in memory, then 2 bytes for the end address of datato load into memory.

If loaded by a DOS command like R (run) or L (load) "D:TOTO.COM" or by a boot DOS file loader, this kind of file will be loaded in memory according to segment adresses, and thanks to a specific segment address, it must be automaticaly run.
DOS command or loaders usulally runs the program at address that is contained in the memory location $2E0-$2E1 (RUNADD Vector), that is usually initialized by the last segment of the file.

### OBJ files

"OBJ" files are Object Code files, containing data or executable. When created by Assemblers programs or by the DOS, these files should have headers to load them into the right address of memory.

But this is not mandatory. So in case there is no header, default address $700 is used to display they disassembly or data Hexdump.

Please note that you can change the default address by using the extract menu.

### SYS, COM, EXE, XEX files

"SYS", "COM", "EXE", "XEX" files are _the_ ATARI binary executable code files.  These files _must_ have headers to load and run them into the right address of memory.

If no or faultly headers are found, default address $700 is used to display they disassembly or data Hexdump.

### DOS.SYS files

DOS.SYS files have no header, it is because they are loaded in memory on purpose by the Boot program of the DOS disk.

### "BIN" ATARI DOS Files

"BIN" ATARI DOS Files are Raw Binary Dump File. They should not have the $FFFF executable file header. The default address $700 is used to display they disassembly or data Hexdump.

If the BIN file has a header, you will be able to see it on the Hexdump, the 2 first bytes will be $FF FF, then you can try to change its extension to an ATARI binary executable file like COM or EXE file.

**Conclusion: usually a BIN file should not have any header, and OBJ, COM, EXE, XEX file should have one. For SYS files, there is no rule, as this is a file can be loaded and run direcly by DOS BOOT program. If a header was expected and is not found, then the default address $700 is used. Use Extract Menu to change origin address.**

## BIN, ROM, A52, CAR dump image files

* BIN > Atari Raw Binary Dump File
* ROM > ROM Dump Image File
* A52 > Atari 5200 Rom Dump Image File
* CAR > Cartridge Image File with CART header (16-bytes encoding the type of machine and mapping of the ROM Cartdridge banks)

## BIN, ROM, A52, CAR dump image as Atari DOS Files

BIN, ROM, A52, CAR dump image as Atari DOS files will be converted into simple Atari DOS "BIN" files.

Note: if you dump your OS ROM in the DOS menu, you should save it as OBJ file as the DOS ususally add an executable segment header.

In case of a ROM raw dump file, wihtout header, change its extenson to ROM. The Tool can guess the start address avoiding the use of the $700 default address.
The guess is base on the size of the file that must be an exact multiple of §1000 (4KB).

Here is an example of an OS ROM dump that should have been named with OBJ instead or ROM extension because MyDOS has put a $FFFF executable header in the file and segment addresslocation in memory:

![image](https://github.com/user-attachments/assets/571c035d-cf78-4c14-b6bc-8281da36ab41)

So change it into OBJ file and it works:

![image](https://github.com/user-attachments/assets/660a0b20-4b71-46be-827e-5a2b87129d0c)

Here is an example of a ROM dump without the header nor segment. Its size is $4000 multiple of $1000 (4kB).
The Tool calulates a start address at $8000:

![image](https://github.com/user-attachments/assets/ca0ea763-fb33-4ec1-b959-03dbafc32244)

## Comparing text options for viewing and saving text files

Let's figure that you have this BASIC file in the Tool:

![image](https://github.com/user-attachments/assets/853cecb7-1a23-481c-9cba-8dbbd2edc52c)

**1/** You can use **Save as UTF text**, for you reference to get a text copy on your Client's system.
Save and open it in a Client's text editor, the result is:

![image](https://github.com/user-attachments/assets/e4bd3920-ff01-4995-ac80-f5069c4e388d)

=> Because with saving as UTF Text File, each char is converted into the closest displayable char available on the Client. Inverted Atari chars are converted to normal char, except the Inverted SPACE char.

**2/** If you use **Save as Atari LST**, the result is not compatible for Client's text editor, so you should not use this feature to get a clean text copy on your Client's system. This is the example:

![image](https://github.com/user-attachments/assets/f67de4bd-eac9-4451-9928-c61c1e32fb61)

**3/** Last option you have is to **copy & paste** the text from the Tool Editor to your Client's system text editor:

![image](https://github.com/user-attachments/assets/afba56e8-61d4-4ccb-91a6-b43a2c6a799b)

**And if you can change the default monospace font for an Atari System font** previously installed on your Client editor, you will get this very close result:

![image](https://github.com/user-attachments/assets/f7fb7ca5-28b5-4516-9794-ad2dfe30dd59)


_PVBest infoo Nov 2024_
