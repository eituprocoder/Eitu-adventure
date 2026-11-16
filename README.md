# Eitu Adventure

A 3D platform adventure starring **Eitu** and his coding companion, **JS Duck**.

Developer name: **Eituprocoder team**  
Version: **1.0.0**

## Story

Eitu is programming with JS Duck while his friends secretly prepare a party for his fifteenth birthday. Suddenly, Hacky, the hacker ghost, kidnaps everyone and corrupts the portals connecting four worlds.

Eitu and JS Duck must recover the code keys, defeat the guardians, and bring their friends home before Hacky finishes his final compile.

All in-game dialogue and story scenes are in English.

## Features

- 80 distinct, deterministic level layouts across four worlds.
- Articulated 3D characters with running, jumping, landing, spinning, talking, and celebration animations.
- Double jump, spin attack, dash, and enemy-stomp mechanics.
- Moving, crumbling, icy, and spring platforms; spikes and timed lasers.
- Three code keys per level, collectible code bits, and checkpoints.
- A rescue every five levels: 16 rescue stages in total.
- Four boss encounters, ending with Hacky.
- Animated 3D story scenes, an opening sequence, and a birthday ending.
- Original synthesized music and sound effects.
- Automatic local progress saving, level unlocking, and star ratings.
- Touch and desktop controls, graphics settings, and sound settings.
- Offline Android and standalone HTML editions.

## Worlds

| World | Levels | Theme |
|---|---|---|
| Bytewood Gardens | 1–20 | Floating gardens, bugs, and springboards |
| Neon Circuit City | 21–40 | Rooftops, moving circuits, and laser gates |
| Frostbyte Peaks | 41–60 | Ice, crystals, snow, and slippery momentum |
| Hacky’s Firewall | 61–80 | Corrupted platforms, lava, and Hacky’s fortress |

## Installation

### Android

1. Download `Eitu-Adventure.apk`.
2. Open it on an Android device and follow the installation prompts.
3. Launch **Eitu Adventure**. The app uses landscape orientation.

Requires Android 8.0 or later and a modern Android System WebView. Game assets are bundled in the APK, so gameplay works offline.

### Desktop

Download `Eitu-Adventure.html` and open it in a modern browser. The file includes the game engine, images, and styles; no server is required for this edition.

## Controls

| Action | Desktop | Touch |
|---|---|---|
| Move | WASD or arrow keys | Left joystick |
| Jump | Space | JUMP |
| Double jump | Press Space again in the air | Tap JUMP again in the air |
| Adjust jump height | Hold or release Space | Hold or release JUMP |
| Spin attack | J | SPIN |
| Dash | K or left Shift | DASH |
| Rotate camera | Q / E | Automatic camera |
| Pause | Escape or P | Pause button |
| Advance dialogue | Enter or Space | CONTINUE |

Sound starts after your first interaction. Touch controls can be set to Auto, On, or Off in Settings.

## How to play

Collect all three golden code keys, then reach the exit portal. Boss stages also require defeating the guardian before the exit opens.

Collecting 20 blue code bits restores one missing heart. Blue flags activate checkpoints. Falling or losing all hearts returns Eitu to the latest checkpoint.

Spin into enemies or jump onto them to defeat them. In boss battles, collect the keys to enable vulnerability windows, dodge the projectiles, and attack when the core glows green.

### Stars and saving

- One star for completing the level.
- One additional star for finishing without dying.
- One additional star for collecting every code bit.

Progress is stored on the current device or browser. Levels unlock sequentially. Clearing app data or browser storage can remove that progress.

## Project files

The source archive includes:

- `index.html` and `style.css`: interface and responsive layout.
- `game.js`: gameplay, physics, camera, story scenes, and interface logic.
- `levels.js`: campaign definitions, layout generation, and dialogue.
- `models.js`: original 3D character and environment geometry.
- `audio.js`: synthesized music and sound effects.
- `software-renderer.js`: CPU rendering fallback when WebGL is unavailable.
- `assets/`: reference images, icon, and Three.js.
- `android/`: Android manifest and WebView activity.
- `tests/`: campaign checks, layout preview, and verification notes.
- `build.mjs` and `build_android.py`: packaging scripts.

## Build the web editions

Requires Node.js. No npm packages are needed.

```bash
node build.mjs
node tests/campaign.mjs
```

The build generates `dist/` and `../output/Eitu-Adventure.html`.

## Build the APK

Requires Java, Eclipse ECJ, Android SDK Platform 35, and Android SDK Build Tools providing `aapt`, `d8`, `zipalign`, and `apksigner`.

```bash
export EITU_BUILD_TOOLS=/path/to/android-sdk/build-tools/35.0.0
export EITU_ANDROID_JAR=/path/to/android-sdk/platforms/android-35/android.jar
export EITU_ECJ=/path/to/ecj.jar
python3 build_android.py
```

Output: `../output/Eitu-Adventure.apk`.

Package identifier: `com.eituprocoder.adventure`.

The source includes a development signing certificate at `signing/eitu-development.keystore`. Its alias is `eitu-adventure`; its development password is `android`. Preserve the certificate to rebuild compatible updates. Use your own private release certificate for distribution.

The Android wrapper serves bundled resources through an intercepted local HTTPS origin. It declares Internet permission for WebView compatibility and blocks external resource hosts and navigation. No camera, microphone, location, or account is used.

## Verification and current limits

- Campaign checks confirmed 80 unique layouts, 240 keys, 1,578 platforms, four bosses, and 16 rescue stages.
- 31 engine checks passed, covering movement, double jump, attacks, dash, keys, exits, checkpoints, respawning, boss vulnerability, and the ending.
- The interface, opening scene, first level, touch controls, and landscape mobile layout received visual checks.
- The APK compiled successfully and its v2 and v3 signatures were verified.

Interactive testing used the CPU rendering fallback because WebGL was unavailable in the test browser. Installation on physical Android hardware and a full manual playthrough of all 80 levels have not been verified.

To run the engine checks from a development server, open `index.html?qa=1` and press **Run engine validation**. The test panel is absent during normal play, and the checks restore the previous saved progress.

## Credits

- Character concepts, reference images, and story premise: supplied by the user.
- Developer name: **Eituprocoder team**.
- Implementation: created with assistance from ChatGPT.
- 3D engine: **Three.js r160**, MIT license; see `THIRD-PARTY-LICENSES.txt` in the source archive.
- Music and sound effects: original procedural synthesis.

Inspired by classic 3D platform adventures, including Pac-Man World. No Pac-Man World game assets or recordings are included.
