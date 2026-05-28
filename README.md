About This Forked Repo: This repository is a fork of romandykyi/GamepadMidiController.

Purpose of this fork
--------------------
This project was forked and the compiled Windows executable included (Created via GithubDev AI GPT-5 mini) so that
Musicians and Creative Artistes can easily download and use a prebuilt Windows
EXE without needing to build the project locally. No other changes are intended
to the original project's code or intent.

Contents added in this fork
--------------------------
- A prebuilt Windows x86_64 executable: GamepadMidiController.exe
- mappings.cfg.example

License
-------
This fork preserves the original project's license. See the `LICENSE` file.
## Simple Usage Instructions (Layman's Terms)

- **What this program does:** It listens to your gamepad and sends MIDI messages to a MIDI output (like a virtual port). This lets you play synths or DAWs with your controller.
- **Before you start:** Install a virtual MIDI port on Windows (for example, loopMIDI). Plug in your gamepad.
- **Running the program:** Double-click the executable (GamepadMidiController.exe) or run it from a terminal. It will print available MIDI outputs — type the number of the port you want and press Enter.
- **Basic controls:** Press buttons A/X/B/Y to play notes (default pitches provided). Pull triggers to send control-change (CC) messages for expression. Move the sticks to change chords or send CCs if you mapped them.
- **How to change mappings without rebuilding:** Copy `mappings.cfg.example` to `mappings.cfg` beside the executable and edit it with your desired mappings. The program reads `mappings.cfg` on startup (see example syntax in the example file).

## Example `mappings.cfg` (already included as `mappings.cfg.example`)
See `mappings.cfg.example` for full commented examples. A quick example:

button A note 1 60 100
button B cc 1 21
axis LEFT_STICK_X cc 2 10 -1.0 1.0

Save your edits as `mappings.cfg` in the same folder as the executable and restart the program.

Original Instructions Pre-fork is below:
# GamepadToMidi

GamepadToMidi lets you turn a standard game controller into a playable MIDI instrument. 

It maps gamepad buttons, triggers, and joysticks to MIDI note and control change (CC) messages in real time, allowing you to control your favorite DAW or virtual instrument using a gamepad.

## Features

- Real-time translation of gamepad input to MIDI messages
- Support for both note and control change events
- Interactive selection of available MIDI output ports
- Customizable mappings for:
  - Buttons → MIDI notes
  - Triggers → MIDI control changes
  - Analog sticks → Chord triggering
- Cross-platform architecture (Windows, macOS, Linux)

Uses modern C++20 and lightweight libraries (libremidi, libgamepad).

## How it works

When you launch the program, it lists all available MIDI output ports.
You select one (for example, a loopMIDI virtual port on Windows), and from then on:

| Gamepad Input | MIDI Action | Default Channel | Notes/CC |
|----------------|--------------|------------------|-----------|
| A | Note On/Off | 1 | 36 (C1) |
| B | Note On/Off | 1 | 42 (F#1) |
| X | Note On/Off | 1 | 38 (D1) |
| Y | Note On/Off | 1 | 46 (A#1) |
| Left Trigger | Control Change | 2 | CC 70 |
| Right Trigger | Control Change | 2 | CC 69 |
| Left Stick | Chord selection (low octave) | 2 | 61–69 |
| Right Stick | Chord selection (high octave) | 2 | 73–81 |

## Requirements

- C++20 compatible compiler
- CMake ≥ 3.14
- A virtual MIDI loopback tool such as:
  - [loopMIDI](https://www.tobias-erichsen.de/software/loopmidi.html) (Windows only)

## Instruction (Windows)

1. Create a virtual MIDI port using loopMIDI
2. Run the program:
3. Select your MIDI output port when prompted.
4. Open your DAW or synth and set its MIDI input to the created virtual port.
5. Start playing! Press gamepad buttons to trigger notes. Move triggers or sticks for expressive control.

## Customization 
You can modify the mappings directly in `GamepadMidiController.cpp`:
- Change MIDI note numbers or channels in the button_handler() or axis_handler() functions.
- Adjust the DEADZONE constant for analog stick sensitivity.
- Replace or expand the chord sets in left_notes and right_notes.

## Used libraries
- https://github.com/celtera/libremidi
- https://github.com/univrsal/libgamepad
