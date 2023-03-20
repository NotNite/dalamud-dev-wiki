+++
title = "Using SamplePlugin"
description = "Setting up a plugin for your own development"
+++

[SamplePlugin](https://github.com/goatcorp/SamplePlugin) is a template C# project for starting to use Dalamud. It is highly suggested to use this as a starting point instead of setting up your own project from scratch.

## Requirements

You will need:

- A text editor, preferably an IDE like Rider or Visual Studio
- .NET 7.0 SDK
- Dalamud installed via your launcher
  - This will automatically work for XIVLauncher users
  - XIVLauncher.Core users must set the `DALAMUD_HOME` environment variable
  - XIV On Mac users will need to [apply this pull request](https://github.com/goatcorp/SamplePlugin/pull/26)
- Git and a GitHub account

## Setting up

First, set up the repository. This guide will assume you want to host it on GitHub - other hosting services will work, but you will need to manuallly create your own repository and (optionally) wipe your commit history.

On the SamplePlugin repository, click "Use this template", then "Create a new repository". Your repository must be public because of Dalamud's licensing. After this, clone the repository to your computer (either with `git clone` or a suitable frontend).

Consider looking at and changing the following files:

- The README.md file
- The .editorconfig
  - You don't need to use this .editorconfig - feel free to bring your own or just not use one
- SamplePlugin.json
  - We'll fix the name and metadata in just a bit

## Renaming the project

Open `SamplePlugin.sln`. You will likely want to use your editor's built in refactoring tool to rename the solution and project. Make sure the `namespace` blocks inside of the C# files match the project name.

Rename `SamplePlugin.json` to match the namespace of your project - if the project was `MyCoolPlugin.csproj`, it would be `MyCoolPlugin.json`. Inside this file, edit the `InternalName` to match your namespace, and change the rest of the fields.

You will want to adjust `Plugin`'s `Name` property, and the namespace passed to the `WindowSystem` constructor.

Consider editing the .csproj's first `PropertyGroup` to match your plugin's information.

## Building and loading in game

After building the project, open the game and go into `/xlsettings`. In the Experimental tab, add the build folder or exact DLL path into the "Dev Plugin Locations" field. Click the plus button, check Enabled, and save.

Now, in the plugin installer (`/xlplugins`), a new Dev Tools tab should appear where you can enable your plugin. Your client might require a restart or clicking the "Scan Dev Plugins" button to see it.

The power icon will let you start this plugin on boot, and the refresh icon will automatically reloadd it when it is rebuilt.
