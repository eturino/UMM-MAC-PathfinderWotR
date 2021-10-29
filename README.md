# UnityModManager changed files for Pathfinder Wrath of the Righteous version 1.1 for MacOS

Repo and instructions in <https://github.com/eturino/UMM-MAC-PathfinderWotR>

We get this files by applying the Assembly option in Windows. This was done with the following versions

- UnityModManager version: `0.24.0a`

## Game Versions

The following versions have been tried successfully:

- `1.1.0k` (original version when the files were modified)

## Older versions

You can access the version developed for the v1.0.x versions of the game in <https://github.com/eturino/UMM-MAC-PathfinderWotR/tree/1-0>

## Download and unzip

Download and unzip the `UMM-modified-pathfinder-wotr.zip` file. For the rest of this README, we'll assume that the contents are now in the `~/Downloads/UMM-modified-pathfinder-wotr/` folder.

## In Steam

First of all, ensure that you don't have a patch already applied. You can do that by using Steam's Verification of local files, to restore all local files.

The base folder, unless otherwise specified, will be `~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/`

In that base folder, we need to create a new `Mods` folder. This is where we need to unzip the different mods that we download, like [Toy Box](https://www.nexusmods.com/pathfinderwrathoftherighteous/mods/8)

```sh
mkdir ~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/Mods
```

Now we'll make a backup of the dll file that we will replace later:

```sh
cd ~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/Wrath.app/Contents/Resources/Data/Managed
cp -a UnityEngine.UIModule.dll UnityEngine.UIModule.dll.original_
```

If we already have a UnityEngine.UIModule.dll.original_ file, overwrite it.

After that, we need to add the UnitedModManager folder into the app.

```sh
cp -a ~/Downloads/UMM-modified-pathfinder-wotr/Unity* ~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/Wrath.app/Contents/Resources/Data/Managed
```

This will copy:

- the UnityModManager folder
- `UnityEngine.UIModule.dll` (replace with the one that is there)

When asked if you want to replace files, say yes.

### Symlink

The UMM log is expected to be in `Wrath.app/Contents/Managed/UnityModManager/Log.txt`, but that Managed folder does not exist, it is placed in `Wrath.app/Contents/Resources/Data/Managed`. To help with this, we can make a symlink.

```sh
cd ~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/Wrath.app/Contents
ln -s Resources/Data/Managed
```

this will create a symlink to `Wrath.app/Contents/Resources/Data/Managed` into `Wrath.app/Contents/Managed`

note: we should probably make the log itself a symlink and actually palce it in another folder outside of Wrath.app

## How?

I followed the same procedure of https://github.com/ThyWoof/UMM-MAC-PathFinderKingMaker by applying UnityModManager in windows and checking the changed files.