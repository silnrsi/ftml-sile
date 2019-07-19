# ftml-sile

A SILE class for typesetting FTML format data.
See https://github.com/silnrsi/ftml for details on FTML (Font Test Markup Language).

## Usage

sile -I ftml test.xml

where "ftml" is the SILE class (defined by ftml.lua and ftml.sil from the classes folder) and "test.xml" is the FTML input file.
In this case the font used in the test is specified by the *fontsrc* element in the FTML input.
Output is to a PDF file "test.pdf".

sile -e "SILE.scratch.ftmlfontlist={'Andika New Basic Italic','Andika New Basic Bold'}" -I ftml AndikaSample.xml

In this case *-e* is used to execute Lua code to initialize the list of fonts.
Because there is no "." in the names, they are assumed to be installed fonts.

sile -e "SILE.scratch.ftmlfontlist={'Scheherazade-Regular.ttf'}" -I ftml ScheherazadeSample.xml

In this case *-e* is used to execute Lua code to initialize the list of fonts.
Because there is a "." in the name, it is assumed to be the name of a font file.

## Known issues

The FTML *background* attribute, for both the *testgroup* and *test* elements, intended to change the background color, is not implemented.

The FTML *em* element is intended to allow a portion of the test string to be emphasized.
This may not produce the desired result when used with a script such as Arabic.

At the moment Arabic script (and probably other right-to-left scripts) do not render correctly.