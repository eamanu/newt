# Newt — a tiny python-inspired language for embedded computing

![](https://i.imgur.com/C4MA4eN.gif)

Newt is a tiny embeddable language targeting processors with only a
few kB of flash and ram. Think of something that would have been
running BASIC years ago and you'll have the idea. These processors are
too small to run [MicroPython](https://micropython.org/).

## Newt Capabilities

Newt borrows semantics and syntax from python, but only provides a
tiny subset of that large language. The goal is to have Newt programs
able to run in a full Python (version 3) implementation so that any
knowledge gained in learning Newt will transfer directly to learning
Python.

### Datatypes

To keep things simple, Newt does not support Python objects at
all. Inspired by BASIC, Newt provides only a single numeric data
type, 32-bit floats. In addition, there are lists, tuples, strings and
functions. True and False are just syntax for 1 and 0. None doesn't
exist at all.

### Programming constructs

For expressions, newt includes the usual arithmetic (+, -, *, /, %,
//), relational (<=, <, ==, >, >=, !=) and logical (or, and, not)
operators.

Newt implements 'if', 'while' and 'for' control flow, along with
'break', 'continue' and 'return'.

### Functions

You can define new functions in Newt; parameters and local variables
have lexical scope, and you can refer to global variables with the
'global' statement (just like python).

## To Do list

I think the basic Newt language is pretty complete at this point, but
there are always improvements that can be made.

 * Custom lexer. The flex generated one is rather large; a custom one
   could be signficantly smaller

 * Custom table-driven LL parser. I've got an LL parser generator, and
   I think the language is pretty close to usable. This should be much
   smaller than the bison parser, and shouldn't be any more difficult
   to use.

 * Documentation. We should be able to crib from existing Python
   documentation where it applies, but it would be good to have a
   comprehensive reference manual for the existing language

 * Port to a microcontroller. Mostly to demonstrate that this is
   possible.

 * Develop a standard API for GPIOS, timers etc. I'm thinking
   something similar to Lego Logo might actually work out pretty well?
   It's pretty stateful, which seems “wrong”, but that does reduce the
   amount of typing. Having something with more knowledge about the
   hardware would be good; the Arduino API requires a lot of setup for
   which pins are connected to what.

## A complete Newt system

I'd like to allow Newt systems to support local development, instead
of relying on a larger remote system for editing and storing
programs. That means creating a tiny IDE of some kind. I think what I
want is a text-mode system with two panes — an editor pane containing
the active Newt code and an interactive pane where you can type
interactive Newt commands to run. With that and some builtins to
save/load projects the system should be usable through a terminal
emulator running on another host, or through a local text interface.

## Build and Run!

### Dependencies
To build Newt you need the next dependencies:

  * [Meson](https://mesonbuild.com/)
  * [Flex](https://github.com/westes/flex)
  * [Bison](https://www.gnu.org/software/bison/)

### Building and install
In the source of the project run:

```
$ meson build && cd build
$ ninja
```

### Running

```
$ ./newt
```
Then, just enjoy!

### Examples

There are examples provided which work with both Python and Newt.

## Contributions

I'd love to receive more contributions in the form of patches,
suggestions and bug reports. Please feel free to send mail or use the
github process. If we get enough participation, I can host a mailing
list easily enough.
