
# 🎵 Fusion FX! Editor Documentation 

*Brought to you by EBsoft Studio (2025) for Fusion-C SDK 2.0*

Welcome to the wonderful world of bleeps, bloops, and mind-blowing sound effects for your retro systems! Fusion FX! Editor is your passport to creating awesome audio for the AY-3-8910 & YM2149 sound chips found in classic systems like MSX, Amstrad CPC, ZX Spectrum, Atari ST, and more!

![Fusion FX! Editor](https://i.imgur.com/placeholder.png)

## 🚀 Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Main Interface](#main-interface)
4. [Creating Sound Effects](#creating-sound-effects)
5. [Selection Mode & Erase Mode](#-selection-mode--erase-mode)
6. [Piano Controls](#piano-controls)
7. [Working with WAV Files](#working-with-wav-files)
8. [File Operations](#file-operations)
9. [Advanced Features](#advanced-features)
10. [Keyboard Shortcuts](#keyboard-shortcuts)
11. [Technical Details](#technical-details)
12. [File Formats](#file-formats)
13. [Detailed Import FX Data Format](#-detailed-import-fx-data-format)

## 🎹 Introduction

Fusion FX! Editor is a smart AY Sound Effect Editor designed to help retro developers create amazing sound effects for their games and applications. Whether you're making a space shooter that needs explosive laser sounds or a platformer that requires cute jumping effects, this tool has got you covered!

Created with love for the Fusion-C SDK 2.0, this editor makes it easy to harness the unique charm of those classic 8-bit sounds we all know and love.

## 🎮 Getting Started

When you first launch Fusion FX! Editor, you'll be greeted with a welcome modal offering to import sample sound effects. These are great examples to get you started and understand what's possible.

The editor works with the concept of "banks" - collections of sound effects that you can use in your retro games. Each bank can contain multiple effects, and you can easily switch between them, edit them, or create new ones.

## 🖥️ Main Interface

Let's break down the main interface so you can find your way around:

### Left Panel

- **FX Bank Management**: Import/export banks of effects
- **FX Name / Selection**: Name your effect and switch between effects in the bank
- **Piano Controls**: Interactive piano for note input
- **WAV Controls**: Settings for importing/exporting WAV files
- **Import FX**: Paste effect data to import
- **Waveform Visualizer**: Real-time visualization of your sound effect

### Editor Canvas

This is where the magic happens! The central canvas shows a graphical representation of your sound effect with five primary rows:

1. **T line (Red)**: Tone toggle ON/OFF
2. **N line (Green)**: Noise toggle ON/OFF
3. **Tone line (Blue)**: Tone frequency value (0-4095)
4. **Noise line (Yellow)**: Noise frequency value (0-31)
5. **Volume line (Cyan)**: Volume level (0-15)

### Bottom Controls Panel

Quick access buttons for:
- Playback controls (Play/Stop)
- Navigation between effects
- Editing tools (Selection mode, Copy/Paste)
- Import/Export options
- Bank management

## 🎛️ Creating Sound Effects

Creating a sound effect in Fusion FX! Editor is like painting with sound! Here's how to get started:

### The Canvas Explained

The editor canvas represents your sound effect over time (255 frames from left to right). Each vertical slice represents a single frame of your sound effect:

* **T line**: When active (red), tone generation is enabled
* **N line**: When active (green), noise generation is enabled
* **Tone line**: Controls the frequency of the tone - higher values = lower pitch
* **Noise line**: Controls the frequency of the noise - different values = different noise characters
* **Volume line**: Controls how loud the sound is at that moment

### Basic Editing

1. **Left-click and drag** on any of the five rows to draw values
2. **Right-click and drag** to erase/reset values
3. Use the **white cursor line** to mark your current position in the effect
4. Use the **frame input fields** below the canvas to precisely set values

### Building Your First Effect

Let's create a simple laser sound:

1. Enable the **T line** (red) by clicking on it for the first 40-50 frames
2. Set a high **Tone value** (around 800) at the beginning
3. Gradually lower the tone value (to around 400) to create a descending pitch
4. Set the **Volume line** to maximum (15) at the start and gradually decrease it
5. Click the **Play button** to hear your creation!

### Manual Frame Editing

For precise control over individual frames:

1.  Click on a frame in the canvas to position the cursor
2.  Use the input fields below the canvas to directly edit:
    -   Frame number (0-254)
    -   Tone value (0-4095)
    -   Noise value (0-31)
    -   Volume value (0-15)
    -   T and N flags (checkboxes)
3.  Changes are applied immediately to the current frame

### Waveform Visualizer

The Waveform Visualizer is not just eye candy – it's a valuable tool for understanding your sound effect in real-time:

-   **Tone Waveform**: Shows the actual square wave generated by your tone settings
    -   You can see the frequency and amplitude visually represented
    -   Higher frequency = more wave cycles visible
    -   Higher volume = taller waves
-   **Noise Pattern**: Displays the pseudo-random noise pattern
    -   Different noise values create visibly different patterns
    -   More regular patterns for lower noise values
    -   More chaotic patterns for higher noise values
-   **Parameter Display**: Shows the exact values for the current frame:
    -   T status (on/off)
    -   Tone value (and equivalent frequency in Hz)
    -   Volume value
    -   N status (on/off)
    -   Noise value

The visualizer updates in real-time as you move the cursor or play your effect, making it perfect for:

-   Understanding the relationship between numeric values and actual sound
-   Fine-tuning frequency values with visual feedback
-   Diagnosing issues (e.g., why a certain frame sounds different than expected)
-   Creating visually distinctive waveforms for specific sound types

While not necessary for basic editing, the visualizer provides a deeper understanding of how the AY chip generates sound, which can help you create more precise and effective sound effects.


## 🔍 Selection Mode & Erase Mode

### Selection Mode

The Selection Mode is one of the most powerful features of Fusion FX! Editor, allowing you to perform bulk operations on ranges of frames.

#### Activating Selection Mode

1. Click the **Selection Mode** button (looks like a pointer) in the Edition section
2. The cursor will change to a selection pointer
3. The interpolation toolbar will appear at the bottom of the editor canvas

#### Making Selections

1. Click and drag on the canvas to select a range of frames
2. The selected area will be highlighted with a yellow semi-transparent overlay
3. You can adjust your selection by clicking and dragging again

#### Working with Selections

Once you have a selection, you can:

- **Copy**: Click the Copy button to store the selected frames
- **Paste**: Position your cursor where you want to insert and click Paste
- **Bulk Editing**: Use the + and - buttons that appear on the sides of the canvas:
  - **+/- for Tone**: Located beside the Tone track, these modify the tone values
  - **+/- for Volume**: Located beside the Volume track, these modify the volume values

#### The X Flag

When working with selections, you'll notice an "X" checkbox in the Flags section:

- When **unchecked**: Changes apply to all frames in the selection
- When **checked**: Changes only apply to frames that already have volume or tone values > 0
  
This is incredibly useful when you want to preserve the shape of your effect while modifying only the active parts!

#### Interpolation Tools

Selection Mode unlocks the interpolation toolbar, which offers powerful ways to create smooth transitions:

For **Volume**:
- **Linear Up**: Creates a straight line from low to high values
- **Linear Down**: Creates a straight line from high to low values
- **Parabolic**: Creates a bell curve (starts low, peaks in the middle, ends low)
- **Inverse Parabolic**: Creates a U shape (starts high, dips in the middle, ends high)
- **Flat Normalize**: Sets all values to the average of the start and end points

The same options are available for **Tone** as well.

#### Empty Area Behavior

When applying interpolation to an area with all zeros, the editor intelligently creates an appropriate pattern based on the interpolation type:
- Linear Up creates a gradual rise from zero
- Linear Down creates a gradual fall to zero
- Parabolic creates a bell curve from zero
- Inverse Parabolic creates a U shape from zero

#### Exiting Selection Mode

Click the Selection Mode button again to return to normal editing mode.

### Clear Mode

Clear Mode provides a quick way to erase specific parameters across your effect.

#### Activating Clear Mode

1. Click the **Clear Mode** button (looks like an eraser) in the Interface section
2. The cursor will change to an eraser icon

#### Using Clear Mode

- **In normal editing mode**: Click on any of the five tracks to clear all values for that parameter across the entire effect
- **With a selection active**: First make a selection in Selection Mode, then activate Clear Mode - now when you click a track, it will only clear values within your selection

For example:
- Click on the Tone track to set all tone values to 0
- Click on the T line to disable tone generation across all frames
- Click on the Volume track to silence the entire effect

#### Targeted Clearing

Clear Mode is useful for situations like:
- Removing noise while keeping tone intact
- Silencing specific sections of an effect
- Creating gaps in the tone or noise patterns
- Quickly disabling T or N flags across multiple frames

#### Exiting Clear Mode

Click the Clear Mode button again to return to normal editing mode.

Pro tip: Selection Mode and Clear Mode are extremely powerful when used together! You can select a specific section of your effect, switch to Clear Mode, and then selectively erase just one parameter in that section.

## 🎹 Piano Controls

The Piano Controls section is your friend for inputting musical notes:

### Piano Features

- **Octave selector**: Choose from octaves 1-8
- **Volume control**: Set the volume for the played notes (0-15)
- **T/N toggles**: Enable/disable Tone and Noise when inserting notes
- **Piano keyboard**: Click on keys to hear and insert notes at the cursor position
- **Step**: Number of frames to advance the cursor after inserting a note
- **Fill**: Number of frames to fill with the same note



### Using the Piano

1. Position your cursor where you want to insert a note
2. Select your desired octave and volume
3. Check T and/or N as needed
4. Click a piano key
5. The note will be inserted at the cursor position and the cursor will advance by the "Step" value

The  **Step**  and  **Fill**  parameters are particularly powerful:

-   **Step**: Controls how many frames the cursor jumps forward after inserting a note
    -   Example: With Step = 4, each time you press a key, the cursor will jump 4 frames ahead
    -   Great for creating rhythmic patterns where notes are evenly spaced
    -   Use smaller values (1-2) for dense melodies and larger values (4-8) for sparser rhythms
-   **Fill**: Controls how many consecutive frames will contain the same note
    -   Example: With Fill = 3, each note you press will be copied to 3 frames in a row
    -   Perfect for creating sustained notes or drones
    -   Combine with Step for complex patterns (e.g., Fill = 3, Step = 4 creates notes with a gap between them)

Practical examples:

-   For a rapid arpeggio: Set Step = 1, Fill = 1, and quickly press different notes
-   For a sustained melody: Set Step = Fill (e.g., both = 4) so notes connect perfectly
-   For a "staccato" effect: Set Fill = 1 and Step = 3 to create space between notes
This is perfect for creating melodic patterns or rhythmic sequences!

## 📊 Working with WAV Files

Fusion FX! Editor allows you to import and convert WAV files to AY sound effect format, which is super handy!

### WAV Import Controls

In the WAV Controls panel (click to expand), you'll find:

- **Volume Scale**: Adjust the amplitude of the imported sound (1.0-5.0)
- **Pitch Threshold**: Fine-tune the pitch detection sensitivity (0.05-0.3)
- **Noise Sensitivity**: Adjust how much noise is detected (1-100)

### Exporting as WAV

When exporting, you can choose:
- **Sample Rate**: 44.1 kHz, 22.05 kHz, 11 kHz, or 8 kHz
- **Export Format**: 
  - WAV Standard (with header)
  - PCM 8-bit (raw data, no header)
  - ADPCM 4-bit compressed (raw data, no header)

### Converting WAV to FX

1. Click the **Import WAV** button
2. Select your WAV file
3. Wait for conversion (the editor will analyze the waveform)
4. Adjust the result as needed in the editor

This is great for converting recorded sounds or samples from other sources!

## 💾 File Operations

### Bank Operations

- **Import Bank**: Load a .afb file containing multiple effects
- **Export Bank**: Save all effects as a .afb file

### Effect Operations

- **Load .afx**: Import a single effect from a .afx file
- **Save .afx**: Export the current effect as a .afx file
- **Copy to Clipboard**: Copy the current effect's data as a comma-separated list
- **Paste FX Data**: Insert effect data from the text area below

### WAV Operations

- **Export as WAV**: Save the current effect as a WAV file
- **Import WAV**: Convert a WAV file to the current effect

## 🧙‍♂️ Advanced Features

### Interpolation Tools

In Selection mode, you'll see interpolation buttons that help create smooth transitions:

- **Linear Up**: Create a rising slope
- **Linear Down**: Create a falling slope
- **Parabolic**: Create a bell curve (up then down)
- **Inverse Parabolic**: Create a U shape (down then up)
- **Flat Normalize**: Set all values to the average

These can be applied to both Volume and Tone parameters!

### Live Mode

Toggle the **Live Mode** button to hear changes as you draw them - instant feedback!

### Clear Mode

The **Clear Mode** button lets you quickly erase specific parameters across the entire effect or just the selected range. Check out the [Selection Mode & Erase Mode](#-selection-mode--erase-mode) section for detailed instructions on using this powerful feature.

### 50Hz / 60Hz Toggle

Switch between 50Hz (PAL) and 60Hz (NTSC) playback speeds to hear how your effect will sound on different systems.

### Zoom

Use the **Zoom buttons** to adjust the width of frames in the editor (4px to 8px per frame).

## ⌨️ Keyboard Shortcuts

Speed up your workflow with these handy shortcuts:

| Key | Action |
|-----|--------|
| Space | Play/Stop |
| Left/Right Arrow | Move cursor |
| Ctrl+C | Copy selection |
| Ctrl+V | Paste selection |
| Delete/Backspace | Clear selected frames or all frames |

## 🔧 Technical Details

### AY-3-8910 / YM2149 Sound Chip

The AY-3-8910 (and its sibling YM2149) are programmable sound generators used in many classic 8-bit computers and game consoles. They offer:

- 3 tone channels (we're working with one here)
- 1 noise generator
- Volume control
- Envelope control (not used in this editor)

### Key Sound Parameters

- **Tone**: 12-bit value (0-4095) that determines the frequency
  - Formula: Frequency = 1773400 / (16 * tone)
  - Lower tone values = higher frequencies
  - Higher tone values = lower frequencies

- **Noise**: 5-bit value (0-31) that determines the noise frequency
  - Different values create different "colors" of noise

- **Volume**: 4-bit value (0-15) that determines the amplitude
  - 0 = silence, 15 = maximum volume

- **T flag**: Enables/disables the tone generator
  - When disabled, you'll only hear noise (if enabled)

- **N flag**: Enables/disables the noise generator
  - When disabled, you'll only hear tone (if enabled)

### Frame Rate

Effects are played back at either 50Hz (PAL) or 60Hz (NTSC), meaning there are 50 or 60 frames processed per second. The editor supports up to 255 frames per effect, giving you a maximum duration of about 5.1 seconds at 50Hz or 4.25 seconds at 60Hz.

## 📁 File Formats

### .afb (AY FX Bank)

The .afb format is a binary format that stores multiple sound effects in a single file. The structure is:

```
Offset  Description
------  -----------
0x0000  Number of effects in the bank (1 byte)
0x0001  Offset table (2 bytes per effect)
...     Effect data (variable length)
...     Effect names (null-terminated strings)
```

### .afx (AY FX Single Effect)

The .afx format stores a single sound effect. The structure is similar to the data part of .afb:

```
Offset  Description
------  -----------
0x0000  Effect data (variable length)
...     Effect name (null-terminated string, optional)
```

### Effect Data Format

Each frame in the effect is stored as a variable number of bytes:

```
Byte 0: Control byte
  Bit 0-3: Volume (0-15)
  Bit 4: T flag (0 = on, 1 = off)
  Bit 5: Tone change flag (1 = tone data follows)
  Bit 6: Noise change flag (1 = noise data follows)
  Bit 7: N flag (0 = on, 1 = off)

If bit 5 is set:
  Next 2 bytes: Tone value (12-bit, little-endian)

If bit 6 is set:
  Next byte: Noise value (5-bit)
```

The effect data is terminated by the sequence `0xD0 0x20`.

## 🔢 Detailed Import FX Data Format

The "Import FX" feature allows you to paste a comma-separated list of bytes that represent your sound effect. Understanding this format enables you to create or modify effects manually or programmatically.

### Basic Structure

The data consists of a sequence of bytes for each frame, terminated by the end marker `0xD0, 0x20`. The number of bytes per frame varies depending on what parameters change:

```
[frame 1 data],[frame 2 data],...,[frame n data],208,32
```

### Frame Data Encoding

Each frame starts with a **control byte** that packs multiple parameters:

```
Control byte: XXXXXXXX (binary)
              ||||||||
              |||||||└─ Volume bit 0 (LSB)
              ||||||└── Volume bit 1
              |||||└─── Volume bit 2
              ||||└──── Volume bit 3 (MSB)
              |||└───── T flag (0 = ON, 1 = OFF)
              ||└────── Tone change flag (1 = tone data follows)
              |└─────── Noise change flag (1 = noise data follows)
              └──────── N flag (0 = ON, 1 = OFF)
```

After the control byte, additional bytes may follow depending on the flags:

1. If the Tone change flag (bit 5) is set:
   - Next 2 bytes: Tone value (12-bit, little-endian)
   
2. If the Noise change flag (bit 6) is set:
   - Next byte: Noise value (5-bit)

The editor optimizes the data by only storing tone and noise values when they change, reducing file size.

### Creating Frame Data Manually

To create data for a single frame manually:

1. **Calculate the control byte**:
   - Start with the volume (0-15) in the lowest 4 bits
   - If tone is OFF, add 16 (set bit 4)
   - If tone value is changing, add 32 (set bit 5)
   - If noise value is changing, add 64 (set bit 6)
   - If noise is OFF, add 128 (set bit 7)

2. **Add tone data** (if tone is changing):
   - Add the low byte of the tone value (0-255)
   - Add the high byte of the tone value (0-15, typically)

3. **Add noise data** (if noise is changing):
   - Add the noise value (0-31)

### Example Breakdown

Let's break down a simple example:
```
175,194,0,175,0,0,174,35,1
```

Frame 1: `175,194,0`
- 175 = 10101111 in binary
  - Volume = 15 (1111)
  - T flag = OFF (1)
  - Tone change = YES (1)
  - Noise change = YES (1)
  - N flag = ON (0)
- 194,0 = Tone value of 194 (low byte = 194, high byte = 0)
- No noise value (it's 0 by default)

Frame 2: `175,0,0`
- 175 = 10101111 in binary
  - Same flags as frame 1
- 0,0 = Tone value of 0
- Noise value of 0

Frame 3: `174,35,1`
- 174 = 10101110 in binary
  - Volume = 14 (1110)
  - T flag = OFF (1)
  - Tone change = YES (1)
  - Noise change = YES (1)
  - N flag = ON (0)
- 35,1 = Tone value of 291 (low byte = 35, high byte = 1)
- No explicit noise value (remains the same as previous frame)

### Termination

The sequence must end with the bytes `208,32` (0xD0, 0x20) to mark the end of the effect data.

### Optional Name Data

After the effect data, you can include the effect name as a sequence of ASCII character codes, terminated by a zero:
```
[effect data],208,32,[name byte 1],[name byte 2],...,0
```

For example, to add the name "LASER" after the effect data:
```
[effect data],208,32,76,65,83,69,82,0
```

### Tips for Manual Editing

1. **Start small**: Begin with just a few frames to understand the format
2. **One change at a time**: Modify one parameter at a time to see its effect
3. **Use a calculator**: Convert between decimal, binary, and hexadecimal as needed
4. **Reference**: Keep this format guide handy when creating or editing effects
5. **Copy existing effects**: Use the "Copy" button on existing effects to see their encoding

With this knowledge, you can create effects in any text editor or generate them programmatically for your games!

## 🎉 Final Notes

Fusion FX! Editor is a labor of love for the retro gaming community. The more you experiment with it, the more awesome sounds you'll discover! Don't be afraid to play, tweak, and have fun - those weird glitchy sounds might be exactly what your game needs!

If you create some cool effects, consider sharing them with the community. There's a download link in the About section for additional banks and effects to inspire you.

Happy bleeping and blooping! 🎧

---

*Created by Eric Boez with the help of Claude AI - EBsoft Studio © 2025*  
*Creative Commons CC BY-SA 4.0*
