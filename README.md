# GBForth

## Features
The flavor of FORTH that this cross-compiler supports has the following features:
- Quotations and quotation based conditional words
- Array objects and literals
- Ability to include binary files
- Ability to embed compile-time Ruby and runtime GBZ80 code
- Comments via `(` and `)`
- Recursion
- Named constants and variables
- Inline words

## Caveats
Due to the nature of FORTH cross-compilers, it's not practically feasible to write
compile-time semantics in FORTH. Because of this, words defined in Ruby have a 
key named `compile` that contain a lambda that is executed at compile-time when
the word is encountered in a source file.

## Planned features
- Predefined constants and words for the Gameboy hardware
- Coroutines
- Add commandline arguments to `make.sh`

## Prerequisites
- RGBDS (I've only tested with 6.1, older versions probably work as well)
- Ruby (version 2.7+)

## Using the compiler
`./make.sh`
This will compile `test.ft` and generate the following:
- An assembly source file (.asm)
- A symbol list file (.sym)
- An object file (.o)
- And the header-fixed ROM file (.gb)

The recommended emulator to use while debugging programs written in gbforth
is [SameBoy](https://sameboy.github.io/) since it will automatically detect and load
the symbol table generated by RGBDS, along with decent debugging features in general.

Right now the `make.sh` script is hardcoded to compile `test.ft` but
a future commit will add commandline argument support for arbitrary
filenames.

## Credits
The included font was created by Jeremy Oduber (@JeremyOduber on twitter) and was downloaded from [here](https://jeremyoduber.itch.io/fonts-for-gb-studio).
