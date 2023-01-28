# GBForth

## Features
The flavor of FORTH that this cross-compiler supports has the following features:
- Quotations and quotation based conditional words
- Comments via `(` and `)`
- Recursion
- Constants
- User defined words

## Caveats
Due to the nature of FORTH cross-compilers, it's not practically feasible to write
compile-time semantics in FORTH. Because of this, words defined in Ruby have a 
key named `compile` that contain a lambda that is executed at compile-time when
the word is encountered in a source file.

## Planned features
- Seamless manipulation of HERE at both compile-time and runtime
- Predefined constants and words for the Gameboy hardware

## Prerequisites
- RGBDS (I've only tested with 6.1, older versions probably work as well)
- Ruby

## Using the compiler
`./make.sh`
This will compile `test.ft` and generate the following:
- An assembly source file (.asm)
- A symbol list file (.sym)
- An object file (.o)
- And the header-fixed ROM file (.gb)

Right now the `make.sh` script is hardcoded to compile `test.ft` but
a future commit will add commandline argument support for arbitrary
filenames.

