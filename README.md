# Shattered Pixel Dungeon seed finder

Application to find seeds for Shattered Pixel Dungeon given constraints (e.g. wand of disintegration +2 and ring of evasion in the first 4 floors).
It can also display items found on a specific seed.

In this repository I will contribute to Shattered Pixel Dungeon v2.0.0 and above. To view releases from previous seedfinder versions, see https://github.com/alessiomarotta/shpd-seed-finder

# How to use

## setup
- obtain a copy of the newest version of the seedfinder. It can be downloaded as a zip from the [releases tab](https://github.com/Elektrochecker/shpd-seed-finder/releases).

[Older versions](https://www.reddit.com/r/PixelDungeon/comments/13bpjv4/how_to_use_alessiomarottas_seedfinder_for/) might only offer the .jar file as a download.

![downloading the seedfinder](https://lemmy.world/pictrs/image/f4ddd9a4-a372-4831-8b71-f081d6568564.png)

- make sure Java is installed on your device
- if you want to use the multithreading script, [nodejs](https://nodejs.org/en) must also be installed
- (optional) Visual studio code to make the Use of the seedfinder more convenient

Extract the zip archive (or place the jar file in an empty folder). This Folder will be the working directory for the seedfinder.

In order to use the seedfinder, commands must be executed in the directory of the seedfinder. Open a command prompt as follows:
- vscode installed: open the folder in vscode and launch an integrated terminal
- windows: hold `shift `and right-click your folder. choose `open a powershell window here`.
- linux: linux users know how to open a termial
- apple: please google how to open a terminal on your OS

Commands can be executed by typing them in this window and pressing `Enter`. You can test your Java installation by running the following command:
```
java -version
```

## scouting seeds
Search items for a known dungeon seed by running the following command(s):

#### seeded runs
```
java -jar seed-finder.jar <floors> <seed>
```
where `<floors>` is the number of floors to scan and `<seed>` is the seed to scan.

example: `java -jar seed-finder.jar 4 SEE-EEE-EED`

#### daily runs
```
java -jar seed-finder.jar <floors> daily<offset>
```
where `<floors>` is the number of floors to scan and `<offset>` is an integer preceded by `+` or `-`.

examples:

- todays daily:         `java -jar seed-finder.jar 24 daily`
- yesterdays daily:     `java -jar seed-finder.jar 24 daily-1`
- tomorrows daily:      `java -jar seed-finder.jar 24 daily+1`
- last weeks daily:     `java -jar seed-finder.jar 24 daily-7`

## finding seeds
Using the seedfinder to generate specific seeds:
- create a new text file in your directoy (in this example called `seeditems.txt`). It will contain a list of items the seedfinder should search for.
- edit your item textfile and put in the items you are looking for. Make a new line for every item. Make sure that every item is spelled correctly (for example assassin's blade instead of assassins blade).

Open your terminal and start the seedfinder using the following command:
```
java -jar seed-finder.jar <floors> <mode> <item file name> [output file name]
```
where `<floors>` is the number of floors to scan, and  `<mode>` is either:
- `any` (find seeds that contain any one of the specified items)
- `all` (find seeds that contain all of the specified items).

When seeds are found they will be saved to `out.txt` or, if specified, your custom output file. Depending on the complexity of your item list, seeds will be found quickly, slowly or be near impossible to generate.

## configuration
Many features such as challenges and seed generation setting can be changed by editing the `seedfinder.cfg` file.

Some challenges might change level generation (most notably `forbidden runes`), therefore i provide options to turn them on or off.

## the multithreading script a.k.a. turbo mode
Using the script to start and control multiple seedfinders simultaneously will greatly increase generation speed, especially for beefy computers. Usage is similar to the seed finding mode. Syntax:
```
node . <floor> <mode> <seed item file> [number of processes]
```
This will start a number of seedfinders equal the provided argument (4 if left blank).  Make sure that sequential mode is disabled in the config file, there would be no point using it with multiple seedfinders. Don't overdo it with the number of seedfinders, since the program will take all the resources it can.

# How to build

1. Clone the [Shattered Pixel Dungeon](https://github.com/00-Evan/shattered-pixel-dungeon) repository.

```
git clone https://github.com/00-Evan/shattered-pixel-dungeon
```

2. Download the patch (changes.patch) into the local repository.


3. Apply the patch to the repository.

```
git apply changes.patch
```

4. Compile the application with the following command:

```
./gradlew desktop:release
```
