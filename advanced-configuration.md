# Advanced configuration

You can configure various parameters of doukutsu-rs in three ways:

* through settings
* through environment variables
* through command line arguments

## Settings

Most parameters can be configured in the `Options` menu on the title screen. But some of them can only be configured by directly editing them in the `settings.json` file (located in [the user data dir](faq.md#where-are-the-saves-settings-logs)) or in the debug menu.

<table><thead><tr><th width="158" align="center">Option name</th><th width="191" align="center">Values</th><th>Description</th></tr></thead><tbody><tr><td align="center"><code>debug_mode</code></td><td align="center"><code>true</code> | <code>false</code> (default)</td><td><p>Enables debug hotkeys and menus.</p><p>This parameter is ignored if the engine was compiled in debug mode.</p><p>For more details, see <a data-mention href="modders-handbook/debugging-and-testing.md">debugging-and-testing.md</a>.</p></td></tr><tr><td align="center"><code>fps_counter</code></td><td align="center"><code>true</code> | <code>false</code> (default)</td><td>Enable FPS and TPS counters in the top right corner.</td></tr><tr><td align="center"><code>more_rust</code></td><td align="center"><code>true</code> | <code>false</code> (default)</td><td><p>Replaces the Sue sprite with Crabby Sue (our mascot) and adds a light blue filter to Sue's face in the text box.</p><p>This setting is always active on 7 July.</p></td></tr></tbody></table>

## Environment variables

You cannot use environment variables to configure gameplay or visual aspects, but you can configure lower-level aspects of the engine. All environment variables have the prefix `CAVESTORY_`.

### CAVESTORY\_DATA\_DIR

**Type**: `string`

This variable specifies the full path to the game data directory. By default, if this variable is missing, the engine searches for game data in the same folder where the engine executable file is located.

### CAVESTORY\_NO\_OPENGL

**Type**: `boolean`

**Possible values**: `1` (true) | `0` (false)

Forces the engine to not use default OpenGL render. This is only supported if the engine is built with the SDL backend (feature `backend-sdl`), for which SDL2 renderer is used, if this option is enabled.

## Command line arguments

All command line parameters are optional, but the application will crash if any of their values are invalid.

Boolean parameters don't accept values and are off by default. String parameters are case-insensetive.

### Window

|          Name         |     Value type    |                                          Values                                          |              Description             |
| :-------------------: | :---------------: | :--------------------------------------------------------------------------------------: | :----------------------------------: |
|   `--window-height`   | `integer` (`u16`) | <p>From <code>0</code> to <code>16535</code>.</p><p>Default value: <code>480</code>.</p> |       Window height in pixels.       |
|    `--window-width`   | `integer` (`u16`) | <p>From <code>0</code> to <code>16535</code>.</p><p>Default value: <code>640</code>.</p> |        Window width in pixels.       |
| `--window-fullscreen` |     `boolean`     |                                             -                                            | Startup the game in fullscreen mode. |

### Logging

|      Name     | Value type |                                                                                                       Values                                                                                                      |                                                                                        Description                                                                                       |
| :-----------: | :--------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| `--log-level` |  `string`  | <p><code>error</code>, <code>warn</code>, <code>info</code>, <code>debug</code>, <code>trace</code>.</p><p>Default value: <code>info</code> or <code>debug</code> (if the engine is built in the debug mode).</p> | <p>The minimum level of records that will be written <strong>to the log file</strong>.</p><p>This parameter doesn't affect the level of records that will be written to the console.</p> |

### Misc

|       Name      | Value type | Values |                                                                                             Description                                                                                             |
| :-------------: | :--------: | :----: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| `--server-mode` |  `boolean` |    -   | <p>Do not create a window and skip audio initialization.</p><p></p><p>It was probably intended for use in online multiplayer, but currenly there's no practical application for this parameter.</p> |
|     `--help`    |  `boolean` |    -   |                                                             Prints a description of all available CLI parameters and exits the program.                                                             |

