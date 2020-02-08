# Jude's Drop In Build Script

This is a dependency-aware build system for simple C/C++ projects. Unlike a
Makefile, it naturally allows builds of multiple optimization levels at once,
e.g. 'debug' and 'release'. I have written it so that no external dependencies
other than Perl are required; just put the file `compile` into your project
root. The system unfortunately only works on Unix.

## Assumptions

The build system requires some things of the project structure:

 * All sources are in a flat source directory.
 * Few special characters in file names. This may include non-ASCII characters.
   File names probably shouldn't start with dashes.
 * Compilation units (non-header source files) are not included in other files.

## Disadvantages

This build system is by no means perfect:

 * Header dependencies are not cached, and scanning for them can take a bit.
   However, compilation units that have changed do not need to be scanned for
   dependencies. They can be compiled in parallel with the dependency scan.
 * If files are being auto-generated, integrating the build system with a
   Makefile is not completely intuitive.
