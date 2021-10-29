# UnityModManager changed files for Pathfinder Wrath of the Righteous for MacOS

We get this files by applying the Assembly option in Windows. This was done with the following versions

- UnityModManager version: `0.23.5b`

## Game Versions

The following versions have been tried successfully:

- `1.0.9c`
- `1.0.8d`
- `1.0.7f`
- `1.0.6d`
- `1.0.4d`
- `1.0.3d`
- `1.0.2f`
- `1.0.2b`
- `1.0.1c` (original version when the files were modified)

## Download and unzip

Download and unzip the `UMM-modified-pathfinder-wotr.zip` file. For the rest of this README, we'll assume that the contents are now in the `~/Downloads/UMM-modified-pathfinder-wotr/` folder.

## In Steam

The base folder, unless otherwise specified, will be `~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/`

In that base folder, we need to create a new `Mods` folder. This is where we need to unzip the different mods that we download, like [Toy Box](https://www.nexusmods.com/pathfinderwrathoftherighteous/mods/8)

```sh
mkdir ~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/Mods
```

After that, we need to add the UnitedModManager folder into the app.

```sh
cp -a ~/Downloads/UMM-modified-pathfinder-wotr/Unity* ~/Library/Application\ Support/Steam/steamapps/common/Pathfinder\ Second\ Adventure/Wrath.app/Contents/Resources/Data/Managed
```

This will copy:

- the UnityModManager folder
- `UnityEngine.UIModule.dll` (replace with the one that is there)
- `UnityEngine.UIModule.dll.original_` (backup from the original)

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
