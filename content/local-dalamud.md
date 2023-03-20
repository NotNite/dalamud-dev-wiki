+++
title = "Running Dalamud locally"
description = "Running Dalamud locally for development"
+++

<div class="warning">
  <h2>Warning</h2>
  If you are not a developer, you shouldn't be on this page. Dalamud is automatically installed and set up for you by XIVLauncher.

  If your goal is to circumvent safety measures and load Dalamud early on patch days, you will be given no support. You will likely experience bugs, crashes, other issues, and potentially risk your account if unsafe data is sent to the server.
</div>

## Requirements

- Dalamud cloned locally (the repository is located [here](https://github.com/goatcorp/Dalamud))
- .NET 7.0 SDK
- C++ build tools

## Building

Dalamud uses Nuke for its build system. After cloning the repository, run the build project:

```
dotnet run --project build
```

## Injecting

`Dalamud.Injector.exe` will be output into your `bin/Debug` folder. You can either launch the game with it, or inject Dalamud into an already running process.

```
# Inject into a running process
./Dalamud.Injector.exe inject <pid>
# Inject into all running FFXIV processes
./Dalamud.Injector.exe inject -a

# Launch the game with fake arguments (this will load the game with an invalid session ID, so you can't log in)
./Dalamud.Injector.exe launch -f

# Launch with your own game arguments
./Dalamud.Injector.exe launch -- DEV.TestSID=42069
```

By default, Dalamud.Injector will use the game path from your XIVLauncher config - you can specify the path to `ffxiv_dx11.exe` with `-g`/`--game`.

You can specify custom paths for Dalamud directories like so:

```
$injector_exe launch \
--dalamud-working-directory="$injector_dir" \
--dalamud-configuration-path="$dalamud_dir/dalamudConfig.json" \
--dalamud-plugin-directory="$dalamud_dir/installedPlugins" \
--dalamud-dev-plugin-directory="$dalamud_dir/devPlugins" \
--dalamud-asset-directory="$dalamud_asset_dir"
```

Note that these arguments are optional and default to your XIVLauncher install. Providing them will allow you to effectively create a portable Dalamud installation.

You can also pass the `UserPath=` argument to the game to use a different game config directory - this allows you to do something like have a development environment that launches in windowed, while your normal environment launches in fullscreen.
