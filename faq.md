# F.A.Q
 Before saying something doesn't work, check if your problem is handled below.

## Mod Users

### "Failed to initialize D3D11Device"  Error
The game is using DX12 yet UML is designed to work with DX11 only.<br>
- Option 1: Open the `ModLoaderInfo.ini` file set `DX12` to `1`.<br>
- Option 2: Add `-dx11` into the game's launch parameters.
<br><br>
### Stuck on 'waiting for game window'
Try running as administrator.
<br><br>
### UML not locating the game
Make sure you have the corresponding `.profile` file inside `Profiles`.
<br> Usually, it has to match with the game's exe or process name, `game-Win64-Shipping.profile`.
<br><br>
### How to create `.profile` file for my game?
If your game is not yet supported, you can try running with "default" profile:
- Create a new `.profile` file inside `Profiles` folder.
- Name it to match the game's binary exe, or how it is shown in Task Manager.
- - For example: `MyGame-Win64-Shipping.profile`.
- Add the following lines and save.
```ini
#Games Basic Information
[GameInfo]
UsesFNamePool=1
IsUsingFChunkedFixedUObjectArray=1
```
- Try and see if that hooks up to the game without issues.
- - Doesn't work? well, then you should try a different tool called [UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) (a newer, heavy-duty and advanced tool).
- - Or ask someone with UE4 reverse engineering experience to get memory addresses for the custom profile file.

<br><br>
### Is it safe? Antivirus is not happy...
The modloader works by injecting a custom dll into the game's process, allowing it to load and execute custom modders logic inside the game.<br>
Which is the main reason why antivirus may alert you _(UE4SS does the same thing)_.<br>

<br><br>
## Modders

### UML fails to locate ModActor
Make sure: 
- You have 2 custom events in ModActor, named `PreBeginPlay` and `PostBeginPlay`. <br>
- Ensure the ModActor is located in `/Content/Mods/ModName/`.
- Pak file must match with ModName as in the editor.
- - Pak: `MyMod.pak`, Editor: `/Cotent/Mods/MyMod/...`

### Mod not loading
Make sure the pak file is located in LogicMods folder within the game's Paks folder: `.../Paks/LogicMods`.


<br><br>