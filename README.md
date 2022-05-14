# MITH (aka Mapping Is Too Hard)

[![This version of 'mith' @ Cloudsmith](https://api-prd.cloudsmith.io/v1/badges/version/fabricistooeasy/mith/maven/mith/1.6.4-MITE+build.202205141529/a=noarch;xg=io.github.fabricistooeasy/?render=true)](https://cloudsmith.io/~fabricistooeasy/repos/mith/packages/detail/maven/mith/1.6.4-MITE+build.202205141529/a=noarch;xg=io.github.fabricistooeasy/)

MITH is a set of open, unencumbered Minecraft mappings, free for everyone to use under the Creative Commons Zero license. The intention is to let 
everyone mod Minecraft freely and openly, while also being able to innovate and process the mappings as they see fit.

MITH is a fork of yarn.

To see the current version being targeted, check the branch name!

## Usage
To use MITH-deobfuscated Minecraft for Minecraft modding or as a dependency in a Java project, you can use [loom](https://github.com/fabricmc/fabric-loom) Gradle plugin. See [fabric wiki tutorial](https://fabricmc.net/wiki/tutorial:setup) for more information.

To obtain a deobfuscated Minecraft jar, [`./gradlew mapNamedJar`](#mapNamedJar) will generate a jar named like `<minecraft version>-named.jar`, which can be sent to a decompiler for deobfuscated code.

## Contributing

Please remember that copying and pasting mappings from alternate projects under more restrictive licenses (such as MCP, Spigot's or Mojang's obfuscation maps)
is **completely forbidden** without explicit permission from the owners of said mappings to distribute the names under the CC0 license.
This includes using the names from those mappings for inspiration. Discussing the naming approaches used in said projects
is also not welcome - you have been warned. However, it is a good idea to consult name changes with other people - use pull requests or our community spaces to ask questions!

Please have a look at the [naming conventions](/CONVENTIONS.md) before submitting mappings.

### Getting Started

1. Fork and clone the repo
2. Run `sh ./yarn` (Linux, macOS) or `yarn.bat` (Windows) and select the Minecraft version, to open [Enigma](https://github.com/FabricMC/Enigma), a user interface to easily edit the mappings
3. Commit and push your work to your fork
4. Open a pull request with your changes

## Gradle
Yarn uses Gradle to provide a number of utility tasks for working with the mappings.

### `yarn`
Runs [`setupYarn`](#setupYarn) and downloads and launches [Enigma](https://github.com/FabricMC/Enigma) automatically configured to use the merged jar and the mappings.

Compared to launching Enigma externally, the gradle task adds a name guesser plugin that automatically map enums and a few constant field names.

### `build`
Build a GZip'd archive containing a tiny mapping between official (obfuscated), [intermediary](https://github.com/FabricMC/intermediary), and yarn names ("named") and packages enigma mappings into a zip archive..

### `mapNamedJar`
Builds a deobfuscated jar with yarn mappings and automapped fields (enums, etc.). Unmapped names will be filled with [intermediary](https://github.com/FabricMC/Intermediary) names.

### `decompileCFR`
Decompile the mapped source code. **Note:** This is not designed to be recompiled.

### `download`
Downloads the client and server Minecraft jars for the current Minecraft version to `.gradle/minecraft`

### `mergeJars`
Merges the client and server jars into one merged jar, located at `VERSION-merged.jar` in the mappings directory where `VERSION` is the current Minecraft version.

### `setupYarn`
[`download`](#download) and [`mergeJars`](#mergeJars)
