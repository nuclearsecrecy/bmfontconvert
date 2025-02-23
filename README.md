# BitFontMaker2 to Bitmap Text Font converter

This tool is for converting fonts made with [BitFontMaker2](https://www.pentacom.jp/pentacom/bitfontmaker2/) into the `FNT` and `PNG` files needed to use them as true [Bitmap Text](https://docs.phaser.io/phaser/concepts/gameobjects/bitmap-text) font that can be used with things like the [Phaser](https://phaser.io/) game engine.

The "normal" way to do this kind of thing is to convert a TrueType font to a Bitmap Text font with [BMFont](https://www.angelcode.com/products/bmfont/). I find this really tedious when trying to make Bitmap Fonts for pixel-art games, because it is usually overkill and also requires a lot of fine-tuning for the final XML output. I am also using this for very small fonts like the ones created by BitFontMaker2.

This tool was developed by [Alex Wellerstein](https://github.com/nuclearsecrecy) in 2024-2025 for his own use. You are free to use it however you want. I do not claim any copyright on it. It is provided for your use with no warranties, guarantees, etc. Use at your own risk. I have no connection to the creators of BitFontMaker2 or Phaser. It does not take full advantange of the Bitmap Text file format -- it just tries to get the job done. So each font is assumed to have a single page, using all channels, etc. 

## Using the tool

You can clone or download the code from this repo, or you can just use the a hosted version of it at **[https://nuclearsecrecy.github.io/bmfontconvert/src/](https://nuclearsecrecy.github.io/bmfontconvert/src/)**. 

It is written entirely in Javascript and is just embedded in some HTML.

## Instructions

1. Create or open a copy of a font from the [BitFontMaker2](https://www.pentacom.jp/pentacom/bitfontmaker2/) website. 

For example, [here](https://www.pentacom.jp/pentacom/bitfontmaker2/gallery/?id=14201) is one that I made with the exciting name of "FiveByFour" (its characters are based around an assumption of being five pixels tall and four pixels wide).

<img src="https://nuclearsecrecy.github.io/bmfontconvert/src/images/tutorial1.jpg" style="max-width: 30em;" alt="Screenshot of the BitFontMaker2 entry for the font FiveByFour"/>

