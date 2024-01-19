---
description: Modding guide.
---

# Getting Started With Modding

## Supported Types

For now it supports these types:

* `scriptparsetree` - scripts (.gsc/.csc/.gsic/.csic) for replacement and auto linking
* `rawfile` - raw file
* `luafile` - compiled Lua HKS (only replacement)
* `stringtable` - csv file (.csv)

***

## Setting Up Folder For Mods

Create a directory in the Black Ops 4 install `project-bo4/mods`

***

## Creating "metadata.json"

Create a directory with a json file `metadata.json` in it.

For example `project-bo4\mods\demo_mod\metadata.json`.

The format of this json is:

```
{
    "name": "Demo mod",
    "data": [
        {
            "type": "asset type",
            "name": "path in game",
            "path": "path from the mod dir or absolute"
        }
    ]
}
```

More configs are available in the script config.

***

### Scripts

It is possible to load script file with the support of GSIC file, a custom format from the T8-Compiler to replace script functions from the game.

To inject a script, 2 ways are possible, to replace an already existing one or to inject a new one. To tell the game when an injected script should be loaded, a hook script config is available. When a hook script is loaded, the injected script will be loaded.

The hooks of a script are defined with the `"hooks": [ "hook.gsc" ]` config. For example the script demo.gsc loaded when the script zm\_common/load.gsc is loaded.

```
{
    "name": "Demo mod",
    "data": [
        {
            "type": "scriptparsetree",
            "name": "scripts/shield/demo.gsc",
            "path": "compiled.gsic",
            "hooks": [
                "scripts/zm_common/load.gsc"
            ]
        }
    ]
}
```

***

### String tables

The game is using "compiled" csv files, these files have the cell values compiled instead of storing the string values. For example with [zm\_mansion\_weapons.csv](https://github.com/ate47/bo4-source/blob/main/gamedata/weapons/zm/zm\_mansion\_weapons.csv), the table to tell the weapon loaded by a map, the weapon names are hashes.

To create custom table, I've made a code to load the CSV with the first line used to tell the type of the columns. These types are:

* string
* int
* hash
* float
* undefined (gsc)

For example with all the available types:

```
string,int,hash,bool,float,undefined
aaa,123,ar_accurate_t8,true,6.7,
bbb,456,hash_123456789,false,13.823,
ccc,789,ar_accurate_t8,true,12.6,
```

***

## Commands

`reload_mods` for the console to reload at runtime the mods, it only works if the user is in the UI level to avoid reloading scripts in game.
