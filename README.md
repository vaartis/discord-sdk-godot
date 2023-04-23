<img src="https://github.com/vaporvee/discord-rpc-godot/blob/main/project/assets/Banner_v1.png?raw=true">

# discord-rpc-godot
### This is version 1.0! In future versions there will be lobbies, invites, linux builds etc. very soon!
Don't forget to run the following command **if you clone this project** or the godot-cpp folder will be empty
```sh
git submodule update --init
```
# Addon Usage :rocket:
1. Put the `discord-sdk-gd/` folder in a `addons/` folder in your Godot project
2. Enable the addon in your Project Settings under "Plugins" and "DiscordSDK". (if it doesn't show up reopen the project)
3. Create an Application under https://discord.com/developers/applications and get the Application ID
4. (optional) Set images under "Rich Presence" and "Art Assets" and remember the keys
5. Exporting: You need to copy the `discord_game_sdk.dll` or on linux `discord_game_sdk.so` from `res://addons/discord-rpc-gd/bin/PLATFORM/discord_game_sdk.[dll/.so]` to your exported project in the same directory as `discord_game_sdk_binding_debug.[dll/.so]`
```gdscript
extends Node

func _ready():
	Discord_Activity.app_id = 1099618430065324082 # Application ID
	Discord_Activity.details = "A demo activity by vaporvee#1231"
	Discord_Activity.state = "Checkpoint 23/23"
	
	Discord_Activity.large_image = "game" # Image key from "Art Assets"
	Discord_Activity.large_image_text = "Try it now!"
	Discord_Activity.small_image = "boss" # Image key from "Art Assets"
	Discord_Activity.small_image_text = "Fighting the end boss! D:"
	
	Discord_Activity.start_timestamp = int(Time.get_unix_time_from_system()) # "02:41 elapsed"
	#Discord_Activity.end_timestamp = 2492978400 # "15:41 left" (but currently 31. 12. 2048 in unix time)

	Discord_Activity.refresh() # Always refresh after changing the values!

```
#### Then it should look like this: 
<img src="https://cdn.discordapp.com/attachments/825019604207927326/1099642861256970311/activity.webp">

## Extra Info
- "Step 2" (enabling the addon) is needed to add `Discord_Activity.coreupdate()` to a `_process()` function with a singleton. This function is needed by pretty everything but you can it also just add it yourself.
- The Discord SDK itself doesn't build under Linux for some reason (I don't have a Mac so i don't even know if it's builds under OSX) its not well documented but I try as hard as i can to get it working crossplatform but at the time its only working under Windows... (But feel free to make pull requests btw)
- Its an early release some features aren't implemented only because i need a small amount of time not because it's not possible

<br />
<br />

### Credit
[@Pukimaa](https://github.com/pukimaa) - Logo Design

<br />

*This project is not endorsed or affiliated with Discord Inc. or the Godot Foundation.*
