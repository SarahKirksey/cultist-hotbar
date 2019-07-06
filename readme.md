# Cultist Hotbar

This is a mod for Cultist Simulator that adds the ability to select Situations with the numeric keys.

Download the latest release [here](https://github.com/RoboPhred/cultist-hotbar/releases/).

## Usage

Once the mod is installed, pressing the number keys (1 to 9) will select a Situation based on the order they are layed out on the table.

The order the Situations are selected in is determined by the order you have placed them on the table, starting with the far left and moving to the right.
For example, pressing `1` will select the left-most Situation, `2` will select the second-to-left Situation, and so on.
Any time Situations are reordered, their hotkeys will be updated to reflect this.

Note that by default, the game binds keys `1`, `2`, and `3` to Zoom Level 1, Zoom Level 2, and Zoom Level 3.  For best results, change these bindings so they
do not conflict with this mod.  You can do so by selecting the Input tab on the Cultist Simulator launcher.

## Installation

This mod uses BepInEx 5.0.  You must install BepInEx to use this mod.

### Setting up BepInEx 5.0
You must use the [version 5.0 RC1](https://github.com/BepInEx/BepInEx/releases/tag/v5.0-RC1) or later, as earlier versions rely on Harmony.

Once you install BepInEx 5.0, you need to shut off harmony support, or no plugins will load.  To do this, edit `Cultist Simulator/BepInEx/config/BepInEx.cfg` and set `ApplyRuntimePatches` to false:
You may have to run Cultist Simulator once after installing BepInEx to generate the config file.
```
[Preloader]
ApplyRuntimePatches = false
```

### Installing the mod to BepInEx

Place the CultistHotbar.dll file in `Cultist Sumulator/BepInEx/Plugins`

### Troubleshooting

If the mod isn't working, you can turn on the BepInEx logs to see what is going on.

Open your BepInEx config file at `Cultist Simulator/BepInEx/config/BepInEx.cfg` and enable the console by changing the `Enabled` key of `[Logging.Console]` to `true`.
```
[Logging.Console]
Enabled = true
```

Doing this will create a terminal window when you launch cultist simulator.  If you do not see this new window open, then BepInEx is probably not installed correctly,
or the config file is misconfigured.

Once you get the window, check its output after you hit the play button on the Cultist Simulator launcher.  You can either drag the terminal window to another
monitor, or tab out of Cultist Simulator to check it after launch.

If BepInEx is installed and configured properly, you should see messages similar to the following:
```
[Message:   BepInEx] BepInEx 5.0.0.0 RC1 - cultistsimulator
[Message:   BepInEx] Compiled in Unity v2018 mode
[Info   :   BepInEx] Running under Unity v2019.1.0.2698131
[Message:   BepInEx] Preloader started
[Info   :   BepInEx] 1 patcher plugin(s) loaded
[Info   :   BepInEx] Patching [UnityEngine.CoreModule] with [BepInEx.Chainloader]
[Message:   BepInEx] Preloader finished
```

If you do not see these messages, and your terminal window remains blank, then you probably forgot to turn off `AllowRuntimePatches`.  Read the section on Installing again.

Once you have confirmed BepInEx is installed properly, look for the mod loading message.  Once you start the game from the launcher, the terminal window should contain:
```
[Info   :   BepInEx] Loading [CultistHotbar 0.0.1]
```
and
```
[Info   :CultistHotbar] CultistHotbar initialized.
```

If you do not see these lines, then the mod isn't in the correct folder.  Check the Installation instructions for details on where to put the mod.

If you have confirmed all of the above and still are having trouble, try looking at the terminal for lines starting with `[Error  :CultistHotbar]`.  The mod will
try to log errors when it cannot do it's job properly.  Create a github issue with any CultistHotbar error messages you find, and I will try to help you further.

## Development

### Dependencies

Project dependencies should be placed in a folder called `externals` in the project's root directory.
This folder should include:
- BepInEx.dll - Copied from the BepInEx 5.0 installation under `BepInEx/core`
- Assembly-CSharp.dll - Copied from `Cultist Simulator/cultistsimulator_Data/Managed`
- UnityEngine.CoreModule.dll - Copied from `Cultist Simulator/cultistsimulator_Data/Managed`
- UnityEngine.dll - Copied from `Cultist Simulator/cultistsimulator_Data/Managed`

### Compiling

This project uses the dotnet cli, provided by the .Net SDK.  To compile, simply use `dotnet build` on the project's root directory.
