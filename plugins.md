# Plugins

This client supports plugins too, they will be loaded in the directory `project-bo4/plugins`&#x20;

The dlls can export these functions, none of them are mandatory, for example if we simply want to load a dll.

```cpp
#define EXPORT extern "C" __declspec(dllexport)

// Get the plugin name (for the logger)
EXPORT const char* PBO4_GetPluginName();

// All the different events from the component
EXPORT void PBO4_PreStart();
EXPORT void PBO4_PostUnpack();
EXPORT void PBO4_PreDestroy();
```

Here is an example [prozject](https://github.com/ate47/atian-cod-tools/blob/367a27ceb58d09354cca39832daf28422a916ec7/src/shield-plugin/main.cpp)
