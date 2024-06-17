---
description: Extra mod notes.
---

# Extra Modding Notes

### BGCache

To sync the GSC and the LUA scripts, `eventstring` is used, they need to be cached on both side by the host and the clients. To allow that,  a `cache` section in the  metadata.json  to register elements inside the cache.

```
{
    "name": "Cache test",
    "cache": [
        {
            "type": "eventstring",
            "name": "custom_event_string_name",
            "mode": [
                "mp"
            ],
            "map": [
                "mp_seaside"
            ],
            "gametype": [
                "tdm"
            ]
        }
    ]
}
```

&#x20;A custom element can be defined with a type, name and the hooks.

The list of the available types is available [here](https://github.com/Dylbin/t8-atian-menu/blob/master/docs/notes/bgcache.csv).&#x20;

`eventstrings`will be required for custom models, weapons, strings, etc.

The hooks are via the mode, the map or the gametype, the available modes are `"mp"`, `"wz"`,`"zm"` or `"cp"`.

The GSC api function `precache(type, hash)` is to allow adding elements to the cache, it's not working with multiplayer, but it allows to quickly test things.

***

#### Separator in stringtables

For the stringtable custom assets (CSV) there is an option in the metadata.json to select the separator. It can be useful with files with a lot of comas. Example with a TSV:

```
{
    "name": "Sep test",
    "data": [
        {
            "type": "stringtable",
            "name": "gamedata/shield/test.csv",
            "path": "demo.tsv",
            "separator": "\t"
        }
    ]
}
```



***

#### Localized entries

Localizeentry xasset

```
{
    "type": "localizeentry",
    "name": "shield/custom_message_test",
    "value": "custom message text"
}
```

With the cache it can be used between players, it can be used to create custom trigger messages.

Note: You only need the cache for things asking for a client-server connection. they are also not needed if its only for Frontend.

***

#### XAsset redirects

Simply change the name of an asset at runtime, it allows to use another asset by replacing the asked name. ([here the list of the pools](https://github.com/Dylbin/t8-atian-menu/blob/master/docs/notes/xassetpools.csv))

Using the `redirect` field in the metadata config.

```
{
    "name": "redirect test",
    "redirect": [
        {
            "type": "asset type",
            "origin": "origin name",
            "target": "new name"
        }
    ]
}
```



***

#### GSC/CSC ShieldToJson/ShieldFromJson functions

This allow for things to be saved from game using GSC/CSC.

Functions :

```
// save object into a json file, if object is undefined, the file is deleted
ShieldToJson(string name, object object = undefined);
// get an object from a json, if the file doesn't exist, the function returns undefined
ShieldFromJson(string name) -> object;
// delete a json
ShieldRemoveJson(string name);
```



Json File Name

The json filename is `project-bo4/saved/{server/client}/{name}.json`, name can't contain a `/` or a `\` (for obvious reasons)



The json locations are vm dependent, so if the a script executed by the client vm can't see the jsons from the server vm.



Small Note :&#x20;

If used in `csc` > Saved to client folder

if used in `gsc` > Saved to server folder

***

#### GSC stacktrace and hash lookups

The game shows the stacktrace when a GSC error occurs, because everything is hashed, theres a map to store the hashes.

The names in the mods are loaded automatically, other hashes can be add by reading a hash file using one of these 3 formats:

* `"string"`, each line is a string, better for fast add/remove, but less accurate, it is the format used in my gsc [decompiler](https://github.com/ate47/atian-cod-tools).
* `"common"`, each line is `<hash>,<string>`, it is used by the [greyhound package indexindex](https://github.com/Scobalula/GreyhoundPackageIndex).
* `"serious_compiler"`, each line is `0x<hash>, <string>`, it is generated automatically by the [serious' t8-compiler](https://github.com/shiversoftdev/t7-compiler).

The dll will load the default files:

* `project-bo4/strings.txt` (string format)
* `project-bo4/hashes.csv` (common format)

But a mod can register custom files in the metadata using

```
{
    "name": "hashes test",
    "data": [
        {
            "type": "hashes",
            "path": "hashes.txt",
            "format": "serious_compiler"
        }
    ]
}
```


***

#### LUA Reading and Writing JSON

This allow for things to be saved from game using LUA with Dvars (Engine Execute Command).

Functions :

```
-- reads and return to specified dvar (Arg in () are optional, use section = "" for no section)
readjson <dvar> <section/subsection> <key> <type> (defaultvalue) (readonly=true) (path/file.json)

-- writes to json, types are: string, bool, int32_t, uint32_t, int64_t, uint64_t. It will auto fix json if bad type or missing
writejson <section/subsection> <key> <value> <type> (path/file.json)
```

Note: if path is not specified, it will use project's/shield's json instead.

Example Usage:

```
Engine[@"exec"](Engine[@"getprimarycontroller"](), "readjson shield_username identity name string")
Engine[@"exec"](Engine[@"getprimarycontroller"](), "readjson shield_ui_color lua ui_color uint64_t 0")

Engine[@"exec"](Engine[@"getprimarycontroller"](), "writejson identity name test_username string")
Engine[@"exec"](Engine[@"getprimarycontroller"](), "writejson demonware ipv4 test_ip string")
```
