# Features and Manual of the Atari Rom Image File Explorer Tool

This web page purpose is to present the features and to give hints on how the ***Atari Rom Image File Explorer*** Tool works and how to use it.

This is a screenshot of the HTML page at its openning when no image file is loaded:

![image](https://github.com/user-attachments/assets/abf3efeb-400b-4b3a-80e4-11383c0e024b)

The left display panel of the HTML page => display the main menu (Tool letter commands), name of loaded image file, type of image file, directory of readable (validated) Atari files, size of image file.

The right display panel of the HTML page => 
* If no image file is loaded => display the known file extensions of the **[Ext Type]** list, as the screenshot above.
* If an image file is loaded => display the selected file from the directory according to its extension. See examples below.

## 1. Displaying Atari Files

### 1.1. Disk Image files

Disk image files are usually binary image of Atari floppy disks, and have the **ATR, ATX, PRO, XFD** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/a993d99d-f067-41f6-bfdd-c528c30d9f9e)

Left display panel => The disk image name and size, and the retrieved directory with all the validated files from the disk DOS structure.

Right display panel => The identified "Ext Type", the disk characteristics, the boot sector informations, and the full DOS directory analysis. Then below is displayed the boot sectors disassembly (disk boot program), and the hexdump of all sectors of the disk image.

The Tool's context button **[Download ATR file]** can convert the _XFD_ file into an _ATR_ file with the famous Nick Atari 16-bytes header.

### 1.2. Language and Formated text files

Language and Formated text files have the **BAS, LST, ASM, M65, LIS, DOC, ATA, TXT, BAT, MAN** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/38bc6c61-45e1-4b51-beec-a8a056f8b3c2)

Right display panel => The selected file from the left directory is displayed as follows:
* identified "Ext Type",
* file characteristics with checksum,
* formating options: number of chars per column...
* the displayed text in an **Editor window that can be modified**.

Please note that only "Language and Formated text files" open in an **Editor** window. See description of features with the **Editor** below.

### 1.3. Font files

Font files have the **FNT, CHR** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/6bec2e30-f6fc-4e04-9b0a-e3d773eeacea)

Right display panel => The selected file from the left directory is displayed as follows:
* identified "Ext Type",
* file characteristics with checksum,
* formating options: number of chars per column, fonct color selection...
* the displayed font, with text example, in an window that can not be modified.

Note: right click on the display window to save it as a picture!

### 1.4. Graphics files

Graphics files have the **GR7, GR8, GR9, GR10, MIC, MCP, APC, PLM, PZM, ILC, INP, CIN, PIC, RAW, SCR, IST, RIP, HIP, TIP** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/137235cb-dd9c-419f-a897-7a7e7df798db)

Right display panel => The selected file from the left directory is displayed as follows:
* identified "Ext Type",
* file characteristics with checksum,
* formating options: color selection...
* the displayed picture in an window that can not be modified.

Note: right click on the picture to save it!

### 1.5. Executable Atari DOS files and Dump files

Executable Atari DOS files have the **SYS, OBJ, XEX, EXE, COM, BIN** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/9b51d8f6-9d22-456e-9818-4a3250f4e26d)

Right display panel => The selected file from the left directory is displayed as follows:
* identified "Ext Type",
* file characteristics with checksum,
* file headers and code segments,
* the full disassembly if code can be disassembled, and/or hexdumps of data.

The **OBJ** extension describes Object files, containing data and/or 6502 machine code.

In Atari DOS files, the **BIN** extension describes Binary files, which contains binary data. It may also be a binary dump of a ROM into an Atari DOS file. So it may also contain 6502 machine code. 

The  will always try to disassemble the code if possible, with the expected or a default loading addresses.

See [chapter 1.6](#16-rom-image-files) below for **BIN** files as ROM Image files.

See [chapter 2.2](#22-display-of-executable-atari-dos-files) below for details of how the handles the *Executable Atari DOS files and Dump files*.

### 1.6. ROM Image files

ROM Images files are usually binary image of Atari ROM cartdridges, and have the **BIN, ROM, A52, CAR** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/23898af2-0827-49ca-8737-7d58e692fb78)

Left display panel => The ROM image name and size.

Right display panel => The identified "Ext Type", the ROM characteristics, the ROM Information, the ROM Memory Bank mapping type in the **[Rom Type Selection]** list.

Then below is displayed: the ROM vectors, the list of the ROM Banks, and the Hexdump of each bank.

Clicking on the **[Toggle Disassembly/HexDump View]** button shows the disassembly of the bank instead of its hexdump.

Note that the ROM Memory Bank mapping type is also the Cartdridge type. This information is retreived from the CART header (if **CAR** image file).
If no type is found in the ROM image file, then the possible types are validated in the **[Rom Type Selection]** list according to memory size parameter.

**Note:** Single **BIN** files loaded in the  will be considered as a ROM Image File. If the **BIN** file is an Atari DOS file in an Atari Disk Image (image of an Atari floppy disk), it will be displayed as a *Executable Atari DOS file and Dump file*. The same applies to files with **ROM, A52, CAR** extensions.

### 1.7. DSK Image files

DSK Images files have the **DSK** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/ccfc858d-65e6-4bfd-b406-799f86e24c88)

A DSK file is just a raw disk image file, no analysis of the boot is done, and only the hexdump of the sectors is displayed. The  will nevertheless search for DOS2.X directory.

You can click on **[Download ATR file]** button to convert it into ATR or **[Download XFD file]** to update its extension.

### 1.8. ARC Image files

ARC Images files have the **ARC** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/0bedb022-f1a9-4542-84bf-b12809710e3f)

An ARC file is like a ZIP file, it is an ARChive containning compressed files. Click on **[Extract]** buttons to extract files from ARC archive.

### 1.9. DAT Image files

DAT Images files have the **DAT** file extensions. They are displayed like this:

![image](https://github.com/user-attachments/assets/6a5589f9-66a8-456b-ae9b-8d2b997a3ee4)

A DAT file is considered as a data file. So only its Hexdump is displayed.

In an Atari Disk Image (image of an Atari floppy disk), the Atari DOS files may have every kind of extensions.

When a file type is unknown (not in the extension list of the previous **1.2 to 1.5 chapters** above), it is considered as *DAT* by the  in order to be displayed. Thus **DAT** is the *default* file type.

## 2. Display features

### 2.1. Display Options for Disk Images, Executable Atari DOS Files and Dumps

This is the display option menu that can be hide with the Tool "P" command (see below chapter 3.6)

![image](https://github.com/user-attachments/assets/ac934141-4e79-4954-83a6-995cc51ea66a)

**[1] Dump & Disassembly options**

* **[Show ATASCII code DUMP]** => toggle the display of ATASCII code DUMP for data bytes, as highlighted in the screenshot above.
* **[Show ANTIC internal display code DUMP]** => toggle the display of ANTIC internal display code DUMP for data bytes, as highlighted in the screenshot above.
* **[ROM: Show addresses with Rom bank number (n00..FF) index]** => works only for ROM dump.
* **[DIS: Show disassembly destination address in hyperlinks]** => very useful to navigate in a disassembly listing, thanks to HTML power.
* **[DIS: Accept code disassembly with up to 2 BRK instructions]** => useful if the code uses BRK instruction, otherwise the BRK instruction is not valid and considered as data (since BRK is $00)
* **[DIS: Use Atari 5200 OS equates instead of 800/XL/XE equates]** => automacilly set when the ROM is intended for the Atari 5200 console, as the addresses equates are not same as Atari 8-bit. You can force by cliking on the buttton.
* **[DIS: Show disassembly code flags (webpage js info for dev.)]** => Show addresses flags used in the disassembly javascript code of the : these info are for the  development, to check accuracy of disassembly routine.

**[2] The save listing buttons**
* **[Save listing as .txt]** => download all the text of the right display panel in a Client's UTF8 text file. Please note that if you open the text file on the Client while applying an Atari Font, then you will get the same display as in the HTML page of the  (except the color display).
* **[Save listing as .html (without html style)]** => download all the text of the right display panel in a simple HTML file, **without** the actual CSS styles, so Atari chars are replaced with the "unknown" '' char. HTML file is very interesting because it keeps the hyperlinks for easy navigation through disassembly listing.
* **[Save listing as .html (Atari font included)]** =>  download all the text of the right display panel in a simple HTML file, **with** the actual CSS styles, that means with the embedded Atari Font. Please note that if you open this HMTL file on the Client, then you will get the same display as in the HTML page of the , even the color display.

**[3] The font display options**.
* **[Normal Dump with Atari Font]** => standard display, using monospace font for text, and Atari Chars from the embedded CSS Font style to display data bytes.
* **[Dump with monospace webfont]** => standard display, using monospace font for text, and trying to use the closest UTF8 char of the HTML font to display data bytes **(experimental)**.
* **[Display all with Atari Font]** => use a standard Atari Font to display every texts and chars in the right display panel **(experimental)**.

### 2.2. Display of Executable Atari DOS files

According to their extensions, the Executable Atari DOS files with be managed by the  as follows:
* _"DOS.SYS"_: there is no $FFFF executable header considered because the DOS.SYS is loaded by DOS boot code on a real system. Disassembly origin address is $0780 for DOS1, or $07CB for DOS 2.X.
* _.SYS_ files: _.SYS_ files other than _"DOS.SYS"_ should have a $FFFF executable header, so disassembly origin addresses are taken from the file segment next to $FFFF header.
* _.OBJ, .EXE, .XEX, .COM_ files: same as _.SYS_ files.
* _.ROM_ files: there is no $FFFF executable header expected. If the size meet a ROM size in 4KB units, the starting address will be computes to match a real ROM.
* _.BIN, CAR, A52_ files: same as .ROM files, except that the $0700 default address is used for the disassembly origin address.
* "unknown" extension file as Atari DOS files: displayed as _.DAT_ file, so only hexdump is is displayed.

Don't hesitate to change file extensions from the **[Ext Type]** list to check, verify and display accordingly a file.

### 2.3. File Extensions management

#### File known extensions that are wrong

The Tool trusts the given file extension which is known in the **[Ext Type]** list. For instance, if you load the file _MICROSOF.BAS_ Atari DOS file, it has the extension _.BAS_, so the  will decode it as BASIC and.... this will lead to an error ! The _BAS_ extension seems to be wrong. Look at the screenshot:

![image](https://github.com/user-attachments/assets/c4f514f8-f2dc-4840-b644-7cfd20d1b745)

In fact this file an executable file, this is the "Microsoft ATARI 800 BASIC V2.5" utility program for Atari. So change its extension from the **[Ext Type]** list to _.COM_ for instance. Then you will get the full executable file display with headers and segments:

![image](https://github.com/user-attachments/assets/13cf8705-d754-4f81-8e82-e5a247dd68c3)

So again, don't hesitate to change file extensions from the **[Ext Type]** list to check, verify and display accordingly a file.

#### File unknown or missing extensions

When loading a file with unknown or missing extensions in the Tool (single image file or Atari DOS file in a directory), the process is as follows:
1.	If the loaded file on the Client has as an "image-mime" flag, then force its extension type to Graphic 7 or 8 extensions (_GR7_ or _GR8_),
2.	If not, then check if the file structure matches an _ATR, ATX, PRO and XFD_ disk image, and if OK, force its extension accordingly,
3.	If not, then check the file signature (2 or 4 first bytes of the file), and force type accordingly to following extensions: 
    * _XEX_ if the signature is the $FFFF header and next segment is valid (start address lower than stop address),
    * _PIC_ if the signature is $80FF followed by $C7C9
    * _RIP_ if the signature is $4952
    * _M65_ if the signature is $FEFE
    * _ARC_ if the signature is $081A or $041A
4.	If not, then test if the file is a BASIC source file, and force its extension type to _BAS_ if OK,
5. If not, then test if it is a _LST_ or _TXT_ file according to its content, and force extension accordingly:
    * _LST_ shall contain text BASIC instructions like "REM", "GOTO", or "THEN"
    * _TXT_ shall not have ATASCII control chars, except $9B End-Of-Line (RETURN) 
6.	If not, then finally force extension to _DAT_ to display the hexdump of the file, like for the file "QWERT" below:

![image](https://github.com/user-attachments/assets/8280e6ef-c9f4-4422-b449-7454079c8c44)

In this case, the Tool will display the following information:
* "_INFO: File extension modified to 'DAT' to display the closest file type_"
* "_Hexdump of data in file "QWERT" which extension type is unknown and shown as DAT_"

### 2.4. DOS Sub-Directories

#### MyDOS Sub-Directories

The Tool handles the MyDos subdirectories and MyDOS compatible DOS subdirectories.

They will be displayed like this:

![image](https://github.com/user-attachments/assets/f12a74f6-35f4-4c5f-b1e6-d0740a6e27f3)

The Tool result is close to the original, as in this example, the DOS sub-directories are diplayed like this on a real Atari system:

![image](https://github.com/user-attachments/assets/538dfecf-b87c-42bb-97b8-fb1b76b20a21)

#### SpartaDOS Sub-Directories

The Tool handles the Sparta DOS main and sub directories which are diplayed like this:

![image](https://github.com/user-attachments/assets/cb207561-1d2c-48d0-a562-306754faaaa7)

## 3. The letter  commands

![image](https://github.com/user-attachments/assets/c3935931-7c48-4274-ae01-b257e21b0f8b)

These commands are in the left floater and consist of:
1. the _"Heart"_ char command. When clicked it toggles the virtual Atari ATASCII keyboard with all the 256 chars. When a char is clicked from this keyboard, and an Editor window is open in the Tool, then the char is automatically inserted in the Tool's Editor window.
2. the "O" char command. When clicked, it displays the Open File window on the Client, in order to select an image file to open.
3. the "H" char command. When clicked, it toggles the hexdump display of the selected file.
4. the "I" char command. When clicked, the selected chars in the Editor window are set to inverse chars.
5. the "D" char command. When clicked, it shows the disassembly of the selected chars of the Editor window.
6. the "P" char command. When clicked, it toggles the display of the Option menu.
7. the "E" char command. When clicked, it toggles the display of the Extract and Disassemble menu.
8. the "S" char command. When clicked, it toggles the display of the Search menu.
9. the "M" char command. When clicked it will show the HEX EDITOR to modify the selected file _[this feature is not available yet]_

The command letter is greyed (that is inactive) if the command is not relevant according to the context.

### 3.1. _"Heart"_ command for ATASCII Char keyboard

[1] Click on the _"Heart"_ char command toggles the virtual Atari ATASCII keyboard with all the 256 chars.
From left to right is the $.0 to $.F byte low nibble, from up to down is the $0. to $F. byte high nibble.
See also the [Atari ATASCII wikipedia](https://en.wikipedia.org/wiki/ATASCII) web page. 

![image](https://github.com/user-attachments/assets/8da30f58-68c0-4695-bd11-99f4a30ed8f3)

[2] For example, you need an horizontal bar to make a text border in your code, so put your carret at the position,

[3] and then click on the graphic char $12 for inserting the horizontal bar char in the Editor.

![image](https://github.com/user-attachments/assets/9f816c80-7da6-4d01-9375-55b1a572e824)

This Tool is very usefull when you need to insert Atari graphics chars or control chars in your code without the real Atari keyboard!

Don't forget to save your modifications using the **[Save as Atari LST]** button.

If you want to cancel all modifications, reload the disk image or you may use the **[Download original Atari file]** button.

### 3.2. "O" command for Opening a file on the Client's Tool webpage

When clicked, it displays the Open File window on the Client, in order to select an image file to open and load in the Tool.

### 3.3. "H" command for the file Hexdump

Hexdump display is requested by clicking on the Tool "H" command.
Hexdump display is canceled when:
* changing displayed file
* extract menu is selected.

Example of Hexdump display:

![image](https://github.com/user-attachments/assets/a9ea772b-b533-460d-8579-6da1eebaf8da)

### 3.4. "I" command to Inverse a char in the Editor

Click the "I" command on selected chars in the Editor to replace the chars by their inverse chars. This Tool is usefull as the Client keyboard cannot put an inverse char in the Editor.

![image](https://github.com/user-attachments/assets/8cbdd8fd-8092-4f55-a0cc-909f60005cc9)

[1] For example, you need to inverse some text in your code, so put your carret at the position and select one or more chars,

[2] and then click on "I" command to replace the selected chars by their inverse chars in the Editor.

Don't forget to save your modifications using the **[Save as Atari LST]** button.

If you want to cancel all modifications, reload the disk image or you may use the **[Download original Atari file]** button.

### 3.5. "D" command for disassembling a string of chars

The Tool "D" command should be used to disassemble a string of chars, **especially in a BASIC listing**.

First, select the string in the Editor. Usually the Machine Language code in BASIC is the string between the quotes "", after a X$= instruction.

Then Click on "D", it displays a floater window with the corresponding disassembly.

Example with disassembly of code at Basic line 120 X$="..."

![image](https://github.com/user-attachments/assets/0cfff288-fe08-4569-afe3-7c710ce1c9e6)

_TODO: check with Basic if it is required to consider the End-Of-Line $9B in the X$=" " string_

### 3.6. "P" command to toggle the Display Options

The "P" command allows you to hide and toogle the options menu for:
* _"Dump & Disassembly options"_
* _"Listing display font options"_
* Save listind buttons

![image](https://github.com/user-attachments/assets/1010fd97-4118-46c4-8d64-abcf5169755c)

The goal is to gain display size.

### 3.7. "E" command for the Extract Data Menu

Example of Extract menu for an Atari DOS file:

![image](https://github.com/user-attachments/assets/17a650ad-405a-4fc7-bda8-df4792067acd)

Example of Extract menu for an Atari Disk Image file:

![image](https://github.com/user-attachments/assets/5dae29b4-6825-4239-9f6e-d8321ec42915)

Buttons are greyed, that is inactive, if no extract has been set and launched.
With the Extract Menu active, the hexdump of the file is displayed in the right panel.
To set an extract, fill the input fields for extract parameters:
* the Start Offset or Start Sector
* the End Offset or End Sector
* the byte Offset in the first sector
* the starting disassembly address

And click on **[EXTRACT&DISASSEMBLE]** button to launch the Extract & Disassemble process. Then the disassembly of the selected file data extract is displayed in the right panel window.

Button **[Download extracted data]** => download the extracted data in a file this is named *[curent_filename]_extract.dat*.

Button **[CANCEL extracted data]** => cancel the current extracted data and refresh display.

Please note that the extract is memorised into the file with the extract parameters, so it will be redisplay even after:
* changing displayed file and reselect the file that has the extract
* hide the Extract Menu by clicking the Tool "E" command.

So if you don't want the extract anymore, please don't forget to click on **[CANCEL extracted data]** button.

### 3.8. "S" command for the Search Menu

Click on "S" command to toggle the display of the Search menu. Search menu is **only enable for Font and Graphic / Picture** Atari file type.

So first you have to force (change) the extension type in the **[Ext Type]** list menu to the type you wish to search.
For example, select "Font File (fnt)" for retreiving a font file.

Then click on the "Search Menu" buttons that will shift the memory with the indicated bytes, the new offset in the file data will be displayed accordingly.

#### Example for Font:

Example of a font that is retrieved into the PROTECTO.COM executable file at offset $30E
 
![image](https://github.com/user-attachments/assets/ed5182c0-f1cf-45b0-aee2-a580c80c1646)

#### Example for Pictures:

Example of graphic GR7 pictures found into the SPACON.FLI executable file at offset $8AE

![image](https://github.com/user-attachments/assets/428ca1a5-3cc9-43dd-81c3-9057ffde18ea)

## 4. Tool Limitations and other information

### 4.1. Use of Atari ATASCII Control Chars

Atari Control Chars in ATASCII are the following chars:

![image](https://github.com/user-attachments/assets/233c6dee-bf72-47c5-a842-d92d4790978f)

These chars cannot be displayed in Atari text files, as they control the display of text in the Editor.

In the Atari ATASCII table, there are also normal chars for the alphabet, and Graphic chars, that can be displayed in the Editor.

See also the [Atari ATASCII wikipedia](https://en.wikipedia.org/wiki/ATASCII) web page. 

Happily, the control chars work on Atari, but not on the Tool that is a different system, except the _$9B End-Of-Line EOL (RETURN)_ char that is used by the Tool's Editor to display a line feed, as on the Atari text files.

The Tool's limitation is that the $9B char can not be displayed with its Atari 'E' symbol in a _LST_ file.
Let's figure out that you want to code a BASIC source code like this with the Tool's Editor and Virtual ATASCII keyboard (of chapter 3.1.):

![image](https://github.com/user-attachments/assets/6c17d2eb-0bba-4194-9c6d-c2807a911058)

Then save it as a LST file, and re-open it the Tool, you will get:

![image](https://github.com/user-attachments/assets/2f37e24b-9d67-43e3-93a4-526ebc19fa73)

The _$9B EOL_ char made an unwanted line feed.
Happily, this limitation should not occur often in your code...

### 4.2. Error log when trying to show (display) a file

Example of error display in the right panel if the display of a file goes wrong:

![image](https://github.com/user-attachments/assets/935bc00c-48b5-4104-a12c-46d9653f3303)

The problem should be within the javascript code of the Tool, that is a bug. So please report this to me, I will check and if possible update the code.

Note that the HTML console will show the detailled error code, and please send me the original disk image file in order for me to check.

### 4.3. Empty Disk Image File loading into the Tool

Trying to load an Empty Disk Image File into the Tool HTML page => The file will be loaded in the Tool, but can not be displayed in the right panel…

So an HTML Alert window is displayed. There nothing to do, you can close the image file.

![image](https://github.com/user-attachments/assets/cc5d01f1-10d1-4866-b890-3c95b893b8f1)

### 4.4. Limitation of the Tool disassembly process

When an executable file contains several segments pointing at the same addresses, new data of the last segment will overlap the previous ones and will modify the disassembly flags, so the hyperlinks may appear broken, or wrong code instruction may be considered as valid.

In the following example, the executable loads 2 times the segment $4000-7FFF with different data:

![image](https://github.com/user-attachments/assets/f73d8f1e-128e-48e3-baff-69581b11fcff)



