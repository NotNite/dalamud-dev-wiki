+++
title = "Using plugin services"
description = "Services provided by Dalamud to plugins"
+++

Dalamud's plugin system provides a number of services to plugins. Services are classes that are instantiated by Dalamud and passed to plugins when they are loaded. Several services exist for things like commands, chat, configuration, client state, and more. These services can be accessed in one of two ways.

## Using constructor injection

By inserting the service into your plugin's constructor, Dalamud will automatically inject the service when it gets called:

```cs
public Plugin([RequiredVersion("1.0")] DalamudPluginInterface pluginInterface)
```

## Using the PluginService attribute

By using the `[PluginService]` attribute like so, Dalamud will automatically inject the service into your IDalamudPlugin:

```cs
[PluginService] public static DalamudPluginInterface PluginInterface { get; private set; }
```
