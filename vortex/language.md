# Adding localization files

1. Create sh_*language*.lua file in vortex-*version*/languages/
2. Copy content from vortex-*version*/languages/sh_english.lua
3. Make needed changes in sh_*language*.lua
4. In vortex-*version*/autorun/vortex.lua replace vortex.loadFile("sh_english.lua", "vortex/languages/") to vortex.loadFile("sh_*language*.lua", "vortex/languages/")
