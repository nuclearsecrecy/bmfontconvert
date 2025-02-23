# BitFontMaker2 to Bitmap Text Font converter

This tool is for converting fonts made with [BitFontMaker2](https://www.pentacom.jp/pentacom/bitfontmaker2/) into the `FNT` and `PNG` files needed to use them as true [Bitmap Text](https://docs.phaser.io/phaser/concepts/gameobjects/bitmap-text) font that can be used with things like the [Phaser](https://phaser.io/) game engine.

The "normal" way to do this kind of thing is to convert a TrueType font to a Bitmap Text font with [BMFont](https://www.angelcode.com/products/bmfont/). I find this really tedious when trying to make Bitmap Fonts for pixel-art games, because it is usually overkill and also requires a lot of fine-tuning for the final XML output. I am also using this for very small fonts like the ones created by BitFontMaker2.

This tool was developed by [Alex Wellerstein](https://github.com/nuclearsecrecy) in 2024-2025 for his own use. You are free to use it however you want. I do not claim any copyright on it or its output. It is provided for your use with no warranties, guarantees, etc. Use at your own risk. I have no connection to the creators of BitFontMaker2, BMFont, or Phaser. 

## Using the tool

You can clone or download the code from this repo, or you can just use the a hosted version of it at **[https://nuclearsecrecy.github.io/bmfontconvert/src/](https://nuclearsecrecy.github.io/bmfontconvert/src/)**. 

It is written entirely in Javascript and is just embedded in some HTML.

## Instructions

\1. Create or open a copy of a font from the [BitFontMaker2](https://www.pentacom.jp/pentacom/bitfontmaker2/) website. 

For example, [here](https://www.pentacom.jp/pentacom/bitfontmaker2/gallery/?id=14201) is one that I made with the exciting name of "FiveByFour" (its characters are based around an assumption of being five pixels tall and four pixels wide).

<img src="https://nuclearsecrecy.github.io/bmfontconvert/src/images/tutorial1.jpg" style="max-width: 30em;" alt="Screenshot of the BitFontMaker2 entry for the font FiveByFour"/>

\2. Click "Copy & Edit" to open it in the editor:

<img src="https://nuclearsecrecy.github.io/bmfontconvert/src/images/tutorial2.jpg" style="max-width: 30em;" alt="Screenshot of the BitFontMaker2 editor"/>

\3. Click the the little icon that looks like a file with two triangles, which opens the "Data Import / Export" window:

<img src="https://nuclearsecrecy.github.io/bmfontconvert/src/images/tutorial3.jpg" style="max-width: 30em;" alt="Screenshot of the BitFontMaker2 editor with the Data Import / Export tab open"/>

The font data is all of that JSON code of numbers and symbols. Copy it to the clipboard (or download it and then copy it later).

\4. Now open the [bmfontconvert tool](https://nuclearsecrecy.github.io/bmfontconvert/src/) (this script), and paste that JSON code into the text area in the **INPUT** section, replacing all existing data there (some data is populated there by default just to illustrate how it works). If the JSON is valid a little green "JSON OK" should pop up at its upper right corner. If there is a problem, it will say "JSON invalid" -- try erasing the existing data and pasting it in again, or copying it again from the source.

\5. You can probably ignore the **SETTINGS** section for now. The default settings seem generally good and anything that is missing-but-necessary will be inferred from the font itself. If the results are messed up in some way, you might tweak the settings then. You can hover your mouse over the names of each of them to learn what they are.

\6. Click the **Convert** button in the tool. This will generate the <code>PNG</code> and <code>FNT</code> data and put them in the <b>OUTPUT</b> section. You can then download them manually (right-click and save, or copy-and-paste into a text file), or click the two **Download** buttons to save them to your computer.

\7. If you are using Phaser, you will then need to import the Bitmap Font files into your project to use them. Refer to the Phaser documentation on [Bitmap Text](https://docs.phaser.io/phaser/concepts/gameobjects/bitmap-text).

The code here is nothing fancy, and does not try to do any complicated "packing" algorithms for maximum efficiency: it will simply sort characters by their maximum height and then put them into the file line by line.

## Notes

The tool only supports XML as the `FNT` format. Phaser apparently can support JSON fonts but it isn't clear to me how they should be structured so I have just ignored that (there is some remnants of a function that tries to convert the data to JSON, but I have not tested it at all in Phaser, and so it is disabled).

The tool definitely does not take full advantange of the Bitmap Text file format -- it just tries to get the job done. So each font is assumed to have a single page, using all channels, etc. If you want something more complicated, use [BMFont](https://www.angelcode.com/products/bmfont/). 

The tool is designed specifically for BitFontMaker2, and so shares its limitations (e.g., grid size of 16x16). In theory if you had a hacked version of BitFontMaker2 that could support larger grids, it you could tweak the settings and use other grid sizes. 

BitFontMaker2 does not provide a "space" character, but does provide a "letterspace" property if you explicitly set one. If you do not set one, the code will try to infer it from the size of certain letters. 

If you set a "monospace width" in either BitFontMaker2 or in the settings, it will override a number of other space settings so that it behaves like monospace does in BitFontMaker2. The tool ignores BitFontMaker2 settings relating to the base font, and the ascender/descender properties, which don't seem to do anything.