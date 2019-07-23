# ftml-sile

A SILE class for typesetting FTML format data.
See https://github.com/silnrsi/ftml for details on FTML (Font Test Markup Language).

## Installation

This repository contains the files needed to implement a SILE class named "ftml". You will need [SILE](https://github.com/simoncozens/sile) to use it.

The simplest way to use this class is to copy the *classes* folder from this repository to your working folder, then SILE will look in that folder for the files it needs.
If you run all your SILE FTML files from that working folder, everything should work fine.

If you want to process FTML files in different folders, then you will need to
- Find your SILE installation folder
- Copy the contents of the *classes* folder from this repository to the *sile/classes* folder in your SILE installation

## Usage

sile -I ftml test.xml

where "ftml" is the SILE class (defined by ftml.lua and ftml.sil from the classes folder) and "test.xml" is the FTML input file.
In this case the font used in the test is specified by the *fontsrc* element in the FTML input.
Output is to a PDF file "test.pdf".

sile -e "SILE.scratch.ftmlfontlist={'Andika New Basic Italic','Andika New Basic Bold'}" -I ftml AndikaSample.xml

In this case *-e* is used to execute Lua code to initialize the list of fonts.
Because there is no "." in the names, they are assumed to be installed fonts.

NB: When running this sample, you may get a message such as "! Error loading language vi: no support for this language".
SILE is warning you that it doesn't have language support information (such as hyphenation rules) for Vietnamese (which is used in this example).
The PDF output is created correctly and shows the way that multiple diacritics are displayed in Vietnamese text.

sile -e "SILE.scratch.ftmlfontlist={'Scheherazade-Regular.ttf'}" -I ftml ScheherazadeSample.xml

In this case *-e* is used to execute Lua code to initialize the list of fonts.
Because there is a "." in the name, it is assumed to be the name of a font file.

## Samples

The samples folder contains sample FTML files which can be processed with the command lines in the preceding section, assuming (for the first) that 'Andika New Basic Italic' and 'Andika New Basic Bold' fonts are installed and (for the second) that the file 'Scheherazade-Regular.ttf' (version 2.100) is present in the same folder as the FTML input. These fonts are available from https://software.sil.org/andika/download/ and https://software.sil.org/scheherazade/download/ respectively.

## Known issues

The FTML *background* attribute, for both the *testgroup* and *test* elements, intended to change the background color, is not implemented.

The FTML *em* element is intended to allow a portion of the test string to be emphasized.
This may not produce the desired result when used with a script such as Arabic.

At the moment Arabic script (and probably other right-to-left scripts) do not render correctly.