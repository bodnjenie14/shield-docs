---
description: Troubleshooting Errors.
---

# Troubleshooting

> **I get this `Debug Error!` everytime I close the game, how do I fix?**

![Debug Error](https://github.com/WrekLess/shield-docs/assets/9027113/a61e46b9-8457-4f60-a2b8-fa25ad416ed8)

&#x20;⁠ This is known and expected behavior. There is no fix at this time.

> **I get this `ERROR_Connection to the Battle.net servers could not be established. Error code: BLZBNTBGS000003E9` when I try joining a public match.**

![Bnet Error](https://github.com/WrekLess/shield-docs/assets/9027113/5695182a-ae45-4c48-b052-4c2e152fb298)

&#x20;⁠ This is likely due to Windows Defender or your antivirus deleting the d3d11.dll file that the bo4-launcher installs to the root of your bo4 game directory. To resolve this, either add an exception for the file or the game directory to avoid future deletions. Then, restore the file from the Recycle Bin and try again.

