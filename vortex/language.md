# Adding localization files

1. Create sh_\*your_language\*.lua file in vortex-\*version\*/languages/
2. Copy content from vortex-\*version\*/languages/sh_english.lua to vortex-\*version\*/languages/sh_\*your_language\*.lua
3. Make needed changes in vortex-\*version\*/languages/sh_\*your_language\*.lua
4. To change localization file you need to make a replacement:

In vortex-\*version\*/autorun/vortex.lua replace 
```
vortex.loadFile("sh_english.lua", "vortex/languages/") 
```
to 
```
vortex.loadFile("sh_*your_language*.lua", "vortex/languages/")
```
