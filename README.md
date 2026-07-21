# Space-Impact-Web
## Introduction
This project is the web version of Nokia 3310's classic game "Space Impact". A 2D shooter game, in which the player flies a spaceship and destroys incoming swarms of enemies spanning across 8 levels. Each level at the end has its own level boss. 

### [Live Demo](https://sidsinr.github.io/Space-Impact-Web)

The objective of the game is to survive and beat the final boss. 

The player has unlimited ammo for the normal bullets. The player also gets one of the three types of different special attacks namely; homing missiles, laser gun and laser wall. These special attacks are limited and can only be replenished from the powerup picked up during a level. The powerup can also provide an extra life.

All the necessary information during the game is available at the top; which include the lives remaining, the type of special attack and the number of attacks remaining, and the score. 
There is also an option to pause the game during the gameplay.

The game is responsive and can be played on a mobile browser. I've added onscreen buttons that can be toggled on/off.

<img src="https://user-images.githubusercontent.com/118676744/224075764-5aaaa42c-de44-4819-afc2-670898da26ff.png" height=70% width=70%/>
<img src="https://user-images.githubusercontent.com/118676744/224077456-e5bc182b-3534-45e7-8c9c-4390fb63949e.png" height=70% width=70%/>
<img src="https://user-images.githubusercontent.com/118676744/224077845-b67fc1f2-04bc-4ef4-b4f2-d01a72d24f1b.png" height="422" width="195"/>

## New Features

### 1. Rapid Fire & Triple Shot Power-ups
Two new temporary buffs added to the power-up pool:
- **Rapid Fire** – Holding Space fires automatically every 150 ms for 6 seconds. A gold "RF" timer bar appears top-right.
- **Triple Shot** – Each fire event spawns 3 projectiles (straight + 10° up + 10° down) for 6 seconds. A cyan "3X" bar appears top-right.
Collecting the same buff again resets its timer.

### 2. Boss Health Bar
When a level boss appears, a colour-coded health bar is shown at the top of the canvas:
- **Green** > 60 % · **Yellow** 30–60 % · **Red** < 30 %
The bar disappears when the boss is defeated.

### 3. Retro Sound Effects (Web Audio API)
A lightweight `SoundManager` generates all sounds with oscillators and noise — no external audio files needed:
- Player shoot, enemy shoot, hit/damage, explosion, power-up pickup, game over, victory, boss low-health warning.
- Master **mute toggle** available in the Settings panel.
- Audio context is lazily initialised on first Play click to comply with browser autoplay policy.

### 4. Difficulty Selector
Choose before pressing Play on the main menu:
| Difficulty | Lives | Enemy HP | Enemy Speed | Fire Rate |
|---|---|---|---|---|
| **Easy** | 6 | ×0.7 | ×0.85 | −30 % |
| **Normal** | 4 | ×1.0 | ×1.0 | normal |
| **Hard** | 3 | ×1.3 | ×1.15 | +40 % |
The selected difficulty is shown in the bottom-right corner of the canvas during play.

### 5. Settings Panel
Click the **⚙ Settings** button on the main menu to open the overlay:
- **Sound On/Off** – mutes/unmutes all Web Audio sounds.
- **Always on Top** *(Tauri desktop only)* – keeps the window on top of other applications.
- **Window Opacity** *(Tauri desktop only)* – slider from 40 % to 100 % opacity.

### 6. Combo System
Destroy enemies quickly to earn a score multiplier:
- Each kill within 1.5 s increments the combo counter.
- Multiplier: **×2** at 2 kills · **×3** at 3 · **×4** at 4 · **×5** at 5+.
- A fading combo indicator and timer bar are drawn at the bottom-right of the canvas.
- The combo resets when the timer expires or the player is hit.

## Desktop App (Tauri v2)
The game ships with a [Tauri v2](https://tauri.app/) desktop wrapper. To build a Windows `.exe` locally:

```bash
# Install prerequisites: Node.js ≥ 18 and Rust stable
npm install
npm run tauri:build
# Installer / .exe appears in src-tauri/target/release/bundle/
```

### Automated Windows Build (GitHub Actions)
Every push to `main` triggers `.github/workflows/build.yml`, which builds the Windows installer on GitHub's servers and uploads it as a downloadable artifact.  
Go to **Actions → Build Tauri Windows App → the latest run → Artifacts** to download `space-impact-windows-bundle`.

## How to run (browser)
Being a complete front-end application, the game can be run on any web browser.

Download the files and open **index.html** in any browser. Make sure the file paths remain the same.

## Software Tools Used
- Adobe Photoshop, to create all the game assets.
- HTML, for laying the foundation of the application.
- CSS, for styling the components of the html document and making it responsive.
- Vanilla JS, for the entire game build.
- **Tauri v2** for the desktop wrapper.

### Acknowledgement
[OpenGameArt](https://opengameart.org) for the onscreen buttons.

## Disclaimer
Space Impact is a trademark of Nokia Inc. All rights reserved with Nokia Inc. This personal project is only for the educational purpose of learning Javascript and HTML Canvas; and it is no way intended for any commercial use or distribution.
