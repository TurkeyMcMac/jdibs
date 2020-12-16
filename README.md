# Jude's Drop In Build Script

**Before using this, see if
[build-objects](https://github.com/TurkeyMcMac/build-objects) would work**. It
is the successor to this project, and I consider it to be better.

This is a dependency-aware build system for simple C/C++ projects that
integrates with Makefiles. Unlike a plain Makefile, it naturally allows builds
of multiple optimization levels at once, e.g. 'debug' and 'release'. I have
written it so that no external dependencies other than Perl are required; just
put the file `compile` into your project root. The system unfortunately only
works on Unix.

## Usage

You can use `./compile -h` for help. I have used the build system as an example
with my other project TS3D. The example branch is
[here](https://github.com/TurkeyMcMac/ts3d/tree/jdibs-example).

## Assumptions

The build system requires some things of the project structure:

 * All sources are in a flat source directory.
 * Few special characters in file names. This may include non-ASCII characters.
   File names probably shouldn't start with dashes.
 * Compilation units (non-header source files) are not included in other files.

## Disadvantages

This build system is by no means perfect. Header dependencies are not cached,
and scanning for them can take a bit. However, compilation units that have
changed do not need to be scanned for dependencies. They can be compiled in
parallel with the dependency scan.
