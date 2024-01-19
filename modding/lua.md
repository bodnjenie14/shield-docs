---
description: Lua / Lui modding instructions
---

# Lua

## Lua Config ( Found In ProjectBo4.json)

The added configs are:

```
{
    "lua": {
        "info": false,
        "error": false,
        "allow_unsafe_function": false
    },
}
```



## Register Lua&#x20;

To register a Lua script it's like with the GSCs, inside the metadata.json file,Using another method to hook.

The hook can be done before or after another script using either the config `hooks_pre` or `hooks_post`.

```
{
    "name": "Lua test",
    "data": [
        {
            "type": "luafile",
            "name": "ui/shield/testhud",
            "path": "test.luac",
            "hooks_post": [
                "x64:fedcba9876543210"
            ],
            "hooks_pre": [
                "x64:0123456789abcdef"
            ]
        }
    ]
}
```

***

## Hook Points

```
x64:2b23cf5ef446c848 (Zombies / Hud)
x64:57d27ab8e2f7a9d0 (Others / Hud)

x64:4a3eb94d551ddf71 (Frontend)
x64:46f417a74d9ab424 (Zombies)
x64:7f750379a77f3190 (Warzone)
x64:4fb12287640e989a (Multiplayer/Warzone)
```

***

## To Compile Lua

[https://github.com/ate47/hksc/tree/test\_t8](https://github.com/ate47/hksc/tree/test\_t8). The Lua in BO4 is adding a new custom datatype `xhash` compared to bo3.

***

###
