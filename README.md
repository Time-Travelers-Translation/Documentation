# Documentation
Documents every external resource and various other information for this fan translation.

All resources will be explained and referenced in the sections below. For a full collection of all the resources explaiend below, navigate [here](https://mega.nz/folder/YxZj3BxB#ID5ADOkYwHCIceplQi_gpA).

## Code Patches
Our code patches were written as ARM assembly instructions as an [.asm file](https://mega.nz/folder/p54ynbgJ#K05B3nJNTHuUBX4td8l7OQ).

We made code patches to the game to patch texts located inside the code.bin, patch the cpk loading routine, and patch all manner of line and image positions.
To apply the code changes in the .asm file we used `armips.exe` by Kingcom [here](https://github.com/Kingcom/armips) or [here](https://mega.nz/folder/g0QXhZrK#xpE0pwrGkRTp1j068CclBQ).

For research in general, we used IDA 7.7 and its features to output pseudo code (F5) for certain routines.
And for some of the assembly instructions in the .asm file we used the [Capstone Dis-/Assembler](https://shell-storm.org/online/Online-Assembler-and-Disassembler/) to get their binary representation, since armips doesn't support all of the ARM instructions.

## File Patches
We made patches to various archives, images, fonts, texts, scripts, and scene descriptions. Most of the relevant tools, that either work with those files or modify them, we created ourselves. Those tools will be referenced in later parts of this documentation, where applicable.

To extract cpk files, we used a [QuickBMS script](https://mega.nz/folder/osZUhSCC#NMRfYlOjuJgNBCUAJcXxVw).<br>
Files are put back into a cpk for the patch by [TimePatchApply](https://github.com/Time-Travelers-Translation/TimePatchApply).

To create a patch file for distribution, we created [TimePatchCreate](https://github.com/Time-Travelers-Translation/TimePatchCreate).<br>
And to inspect the patched files after they were distributed, one can use [TimePatchExtract](https://github.com/Time-Travelers-Translation/TimePatchExtract).

For most basic operations, like opening all sorts of archives, images, or quickly modifying them, we used an older version of [Kuriimu2](https://mega.nz/folder/hpoAyCSb#KmQbdjMhptPY2JWruBrMRQ).<br>
On newer versions, some images were not properly encoded and either blacked out in-game or looked distorted.

For modifying the menu layouts, we used [Level5RessourceEditor](https://github.com/onepiecefreak3/level5ressourceeditor).<br>
While this tool also originated from this project, it can be used by pretty much any 3DS Level5 game (and maybe other platforms too) and long predated this organization. It is therefore kept in its original repository.

## Translation
This game was largely translated by hand, as it started way before modern machine translation tools and AI existed.<br>
However, there are some parts that were only translated in 2024 and 2025, shortly before release. At that time the translators of this project were already occupied by other projects or with their personal life, which left those tiny parts to people that were only rudimentary knowledgable in the japanese language.

For example, the movies between chapters were OCR'ed and then translated by a combination of ChatGPT and DeepL for a basic understanding. Based on the context of the movie and perspectives, those translations were then either completely rewritten or adjusted as needed to fit space and tone.

We used [ScanDoc](https://2ocr.com/online-ocr-japanese/) and [SljFaq](https://kanji.sljfaq.org/draw-old.html) for OCR.

We store our translation on a Google Spreadsheet and tools like [TimeTravelersSheetBridge](https://github.com/Time-Travelers-Translation/TimeTravelersSheetBridge) and [ScnNavigator](https://github.com/Time-Travelers-Translation/ScnNavigator) directly read from and write to those sheets. This allowed us to work on all of the text simultaniously from anywhere that had internet access.

If you want to create your own translation, we recommend you copy our [spreadsheet](https://docs.google.com/spreadsheets/d/1TRyRSCSVl4nOwI7Gvm89FAiVoWteFzo_A96ZSkyVnXA/edit?usp=sharing) to be able to use our tools properly and manage your team.

## Font Patches
We decided to deploy a new font for this game mainly for space efficienty, but also because the latin glyphs of the original font didn't look good.<br>
We created a new font from "Roboto Condensed" with a very old version of [Kuriimu2 Wpf](https://mega.nz/folder/w1gQjBjT#BMYApH-FWWmgG1IfOwISNg) that had basic font support.<br>
With this, open a .xf from the game, click "Open Font Generator", load one of the [font profiles](https://mega.nz/folder/tlwlWJgL#nKMq27NJNj7VfJSPMIW9XQ), adjust it to your needs, click "Generate", and then use the save icons at the top left to persist the new .xf.

We then had additional, very game-specific requirements for the font, that were not intended for that version's font support and were instead realized by [FontPatcher](https://github.com/Time-Travelers-Translation/FontPatcher).

## Script Editing
To edit the games script format .stb (short for Storyboard), we use [Backstab](https://github.com/Time-Travelers-Translation/Backstab) originally by `Neobeo` and adjusted by us to allow for injection.

Storyboards are usually a list of function calls and arguments.<br>
First a storyboard sets up all the assets, like models, images, animations, texts, and so on. They then execute showing those assets in a given time frame, denoted by time stamps like so `time = [Number];`.<br>
As far as we understand, those are frame counts, and reaching that time stamp will immediately dispose of assets from the previous time stamp and load in assets setup for the next time stamp.

As the name `Storyboard` implies, it's easier to think of those files as a list of instructions key-framed to certain time stamps, instead of a scripting language and code.

## Image Editing
To open and inject images, we used an older version of Kuriimu2, referred in [File Patches](https://github.com/Time-Travelers-Translation/Documentation?tab=readme-ov-file#file-patches).

We also created an [ImageExtractor](https://github.com/Time-Travelers-Translation/ImageExtractor), that can extract all image assets referenced by storyboards of a given chapter.<br>
This way, we could extract all image assets of the chapter we currently worked on and could filter out the image assets that needed translation.<br>
This tool will come in handy for other languages, since we didn't translate all image assets with text on them, as some were either too complex, already fit their purpose, or were already in english.

To edit images after extraction, we used Adobe Photoshop 25.9 and GIMP 2.10.8.

We offer all of our GIMP and PS work files [here](https://mega.nz/folder/11oTTTJK#IvQIuCt96syOnHHSRCy3tQ). All of them work on a cleaned base image and with proper layers to make sure text can easily be updated.

Along with those work files, we also provide all of the fonts used in them [here](https://mega.nz/folder/B45yjYTQ#wdFuttdV1jz8XsP3v9UG4g), so they can be installed for use in those work files.

We created one .otf font ourselves on basis of the Time Travelers logo, called "ChunChunMaru" (KonoSuba reference for some reason). It was created with the online tool Glyphr and its project file is provided too.

## Movie Editing
To convert moflex files into mp4, we used [Mobius](https://mega.nz/folder/loYnzCoJ#rpMaYRIw6MXutoKnHLGWJQ) by `Neobeo`. It has the best quality of the available decoding tools for moflex.

We edited the movies with Adobe After Effects 25.1 and also provide our full work files for them [here](https://mega.nz/folder/Z4xWRJ7R#KWfYAP2Ijvb_idGn144jqg), along with their respective mograph for use in Nintendo's Mobiclip Multicore Encoder.

Along with those work files, we also provide all of the fonts used in them [here](https://mega.nz/folder/B45yjYTQ#wdFuttdV1jz8XsP3v9UG4g), so they can be installed for use in those work files.

To convert edited video files back, we used Nintendo's official Mobiclip Multicore Encoder. A working version with instructions can be found on [Internet Archive](https://archive.org/details/3ds-moflex-encoder-tools) or [here](https://mega.nz/folder/sog2UDTY#nckZ1qpSn6Ul3PpJhAKnVA).
