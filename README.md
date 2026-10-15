# BYOW World Exploration — CS 61B

A Java tile-world exploration project developed for **UC Berkeley CS 61B, Fall 2024**, Project 3: Build Your Own World. This is a cleaned copy of a two-person course project. Individual contributions have not been reconstructed or assigned here.

## Repository map

| Location | Purpose |
| --- | --- |
| [`src/core/`](src/core/) | World generation, movement, menu, and save/load code. |
| [`src/tileengine/`](src/tileengine/), [`src/utils/`](src/utils/), [`src/demo/`](src/demo/) | Retained course rendering, utility, and example code. |
| [`tests/`](tests/) | Original course tests, including unfinished optional checks. |
| [`lib/`](lib/), [third-party notes](THIRD_PARTY.md) | Included rendering dependency and its preserved license. |
| [Verification record](CHECKS.txt) | Completed checks and their coverage limits. |

## Features

- Seeded generation of rooms, connecting hallways, floors, and walls on a 40 × 40 grid.
- Keyboard exploration, a main menu, and saving/loading the seed and avatar position.
- A switchable circular visibility radius and English/Spanish menu text.

The visibility feature reveals tiles by distance; it does not implement wall-occluded line of sight.

## Build and run

Use a desktop Java installation (JDK 17 or later). Compilation was checked with JDK 23. The only runtime dependency, `lib/algs4.jar`, is included from the existing course library. No package installation is needed.

From the repository root on macOS or Linux:

```sh
mkdir -p build/classes
find src -name '*.java' -print > build/sources.txt
javac --release 17 -cp lib/algs4.jar -d build/classes @build/sources.txt
java -cp "build/classes:lib/algs4.jar" core.Main
```

On Windows, use `;` between the two runtime classpath entries. The game needs a graphical desktop; the command above is not a headless mode.

## Controls

| Action | Keys |
| --- | --- |
| Start a new world | `N`, then a nonnegative integer seed within Java's `long` range, then `S` |
| Load the local saved game | `L` in English; `C` in Spanish |
| Switch menu language | `S` on the main menu |
| Quit from the menu | `Q` in either language |
| Move | `W`, `A`, `S`, `D` |
| Toggle the visibility radius | `F` during exploration |
| Save and quit | `:Q` during exploration |

The save file is `save.txt` in the working directory. It is excluded from version control.

## Course framework and attribution

This project builds on the CS 61B BYOW course skeleton and supplied tile-rendering, utility, demonstration, and autograder-support code. These components are retained as course materials, not claimed as original work. The project-specific world and interface code is in `src/core/`. The original comments crediting AI assistance for the visibility extension are retained in `World.java`.

See the [Fall 2024 assignment](https://fa24.datastructur.es/projects/proj3/) and [course policies](https://fa24.datastructur.es/policies/). The dependency and its existing license are described in [THIRD_PARTY.md](THIRD_PARTY.md). No new open-source license is applied to the course project.

## Cleanup and verification

The original files were left unchanged. This copy omits IDE metadata, compiled output, local game saves, platform metadata, and original repository history. Two small fixes were made during cleanup:

1. Store the constructor seed in `World`, so saving retains the seed used to generate the map.
2. Use `Q` for Spanish-menu quitting, resolving its conflict with `S` for switching languages.

The original `tests/WorldGenTests.java` is retained for context. Its visual test relies on the optional `AutograderBuddy.getWorldFromInput` method, which remains unimplemented, and two tests are placeholders. It is not presented as a passing automated suite. See `CHECKS.txt` for the actual checks and remaining limits.

The verification record was produced during archive preparation on **October 14, 2026**. It covers compilation and five-seed headless checks; it does not cover graphical interaction or actual disk save/load. This documentation refresh did not rerun the application or tests.

## Course source and sharing terms

CS 61B's course policy prohibits posting project solutions publicly, including after the semester. Course code, assets, and collaborators' work retain their original attribution and applicable sharing restrictions. Repository visibility does not grant additional redistribution rights.
