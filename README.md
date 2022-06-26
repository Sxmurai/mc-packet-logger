# mc-packet-logger
A new version of the minecraft packet logger to packet log things.

## Use cases

1. You want to find out how a paid client does something
2. You want to learn the exact vanilla game packets for bypasses

If the first reason is why you're using this, I do not take liability for any lost client licenses because of the use of this tool. You are on your own.

Example of how to view packets (Vanilla game):

![image](https://user-images.githubusercontent.com/57580886/175831448-18846da2-3fcc-4de0-b7df-337400453400.png)

## Building

1. Download zip or `git clone https://github.com/Sxmurai/mc-packet-logger/` in a terminal
2. Open the folder that it downloaded or unzip the contents into a folder
3. Open a terminal in that folder
4. Type the following commands in: `gradlew setupDecompWorkspace`, `gradlew clean`, `gradlew build` (Note: if you are on windows, you'll need to add a ./ before the gradlew command.
5. Your build jar will be in build/libs.

Don't want to do that? Open the releases tab and download the pre-compiled jar.

This does require forge and Java 8. Gradle should automatically download for you. If not, open it in IntelliJ or download Gradle yourself.

## Configuration File

You can find the file in your .minecraft directory under the file `packet_logger_config.json`

For example, on windows it is at `%APPDATA%/.minecraft/packet_logger_config.json` (Disclaimer: you have to run the game with this mod loaded for this file to be created by the mod)

This JSON file allows you to customize if you see clientPackets, serverPackets, and it also allows you to set an array of allowed packets. These are the remapped stable mapping names of these packets, so no need to dig through SRG mappings. 

Note: For inner class packets (ex: CPacketPlayer.Position, CPacketPlayer.Rotation), you must put the inner class name without the class the inner class is in. For example, instead of adding to the array `CPacketPlayer$Position` or `CPacketPlayer.Position` you must put `Position`.

Example config file:

```json
{"clientPackets":true,"serverPackets":false,"allowedClientPackets":["CPacketPlayer", "Position", "PositionRotation"],"allowedServerPackets":[],"bind":157}
```

## Credits

- Seppuku, while I wrote the "Mixins" myself, I needed help with the custom transformers and what not, so that's where I got that from
