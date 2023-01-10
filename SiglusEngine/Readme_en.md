# SiglusEngie Tools
## Function Description
### Decryption Key

- Secret keys for packing and unpacking `Scene.pck` and `Gameexe.dat`, with comma-separated hexadecimal format.

- When the first item in the drop-down menu is selected, the program will try to search for the secret key automatically when packing and unpacking `Scene.pck`.

- When `KeyList.txt` exists, known secret keys can be selected in the drop-down options.

### Find Key

- It is used to search for the secret key while lauching the game. This item will not appear when `skf.exe` is not found.

- After lauched the game, clice the `Find Key` item and wait for a while for the prompt information of if the secret key is found.

- Found secret keys will be saved in `Last use`.



### Unpack Scene
- Unpack the `Scene.pck` file.

- You can tick the `Find key only` box and click the `start` button to search for the secret keys and save them in `Last use` only(without unpacking the scene files). 

### Pack Scene 

- Pack the `ss` file into `Scene.pck`.

- The `Compression Level` ranges from 2 to 27, 17 is recommended. Specially, Enter 0 to use pseudo-compression (files will be larger than before compression).
### Decrypt Gameexe

- Decrypt the `Gameexe.dat` file.
### Encrypt Gameexe
- Pack the `Gameexe.dat` file.

- The secret key will only work after ticking the `Double Encryption` option. It is not always necessary to tick that option.
### Dump ss
Export texts from `ss` file.  
- Copy text：Copy the texts to the translated lines.
- Export as xlsx：Export as `xlsx` files.  
- Use single xlsx：Export all the texts to one single `xlsx` file.  
- Count words：Add a word counting sheet while exporting as a single `xlsx` file.
- No dump：Do not filter any text. 
- Smart dump：Filter out only plain English lines. 
- Full dump：Filter out all lines containing English.  
### Pack ss
Import the translated texts back into the `ss` file.

- Have Excel text：Tick this when importing from a `xlsx` file.

    `txt` files will be searched regardless of ticking this box or not. When both `txt` and `xlsx` files are found, the program will import the `txt` first, and then the contents of `xlsx` will  overwrite it.

- Bilingual display It is only optional when importing `xlsx` files, and only the mobile version can take effect for double-line display.

- Change quotation marks：Replace the Japanese quotation marks in the dialogue with the Chinese idiom.  
### Dump dbs

Export data from `dbs` file.

- Export all data：Export all data, no content filtering is performed.

- Export as xlsx：Export all data to `xlsx` files, and the table format is compatible with the official `CSV2DBS.exe`.
### Pack dbs
- Import data from `txt` files back to `dbs` files.
### Create dbs
- Converts `xlsx` files to `dbs` files. Unicode encoding is recommended, but some special files may not be recognized.

### Unpack pck / Pack pck
- Unpack and pack the `pck` file dedicated to the mobile version.
### Cut OMV header
- Delete the file header of the `OMV` file and convert it to an `ogv` video file. 

- `OMV` videos with transparency cannot be played with ordinary players.
### Pack OMV
- Will not appear when `siglusomv.exe` is not found. 

- Convert `ogv` video to `OMV` file. `ogv` video must be in `yuv444p` format.
***
## Command line Usage:
```
SceneUnpacker.py <Scene.pck> [Scene\] [-n] [-d] / [-f]
 -n Export ss without decompression
 -d Use default key
 -f Find key only

ScenePacker.py <Scene.pck> <Scene\> [Scene.pck2] [-c [2~17]/-f] [-d]
 -c 2~17 Compression level (Default level 2, level 17 if only input -c)
 -f Do fake compression
 -d Use default key

GameexeUnpacker.py <Gameexe.dat> [Gameexe.ini]

GameexePacker.py <Gameexe.ini> [Gameexe.dat2] [-p] [-c [2~17]/-f]
 -c 2~17 Compression level (Default level 2, level 17 if only input -c)
 -f Do fake compression
 -p Double encryption

ssDumper.py <Scene\> [text\] [-d] [-a/-w] [-x [-s [-c]]]
 -d Copy text to translation line
 -a Export all text without dump
 -w Dump all text with half-width characters
 -x Save text as xlsx files
 -s Save all text in one xlsx file
 -c Add a statistics sheet in single xlsx

ssPacker.py <Scene\> <text\> [output\] [-x [-b]] [-q]
 -x Import from xlsx file (Always import from txt files first)
 -b Import both orignal text and translated text (Bilingual display only effect in mobile version)
 -q Change quotation marks from Japanese custom to Chinese custom

dbsDecrypt.py <dbs file> [-a/-x]
 -a Export all data without dump
 -x Save all data as xlsx file （Compatible with official CSV2DBS.exe if save as csv file)
 
dbsEncrypt.py <dbs.out> [dbs.txt] [-c [2~17]/-f]
 -c 2~17 Compression level (Default level 2, level 17 if only input -c)
 -f Do fake compression
 
dbsBuilder.py <xlsx folder\> [dbs folder\] [-u] [-c [2~17]/-f]
 -u Encrypt dbs file with Unicode (Default is GBK)
 -c 2~17 Compression level (Default level 2, level 17 if only input -c)
 -f Do fake compression

pckUnpacker.py <pck file> [output folder\]
pckPacker.py <data folder\> [output file]

omvCuter.py <omv file> [output file]

siglusomv.exe <ogv file(must be YUV444p)> <omv file>

skf.exe (Just run it and start the game)
```

 
