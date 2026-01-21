# Saurav Plays Piano JSFX

A collection of custom JSFX plugins for **Reaper**, designed and developed by [Saurav Plays Piano](https://sauravplayspiano.com).

This is a collection of Reaper plugins I wrote to help me with some of my ambient / neo-classical piano productions. I am releasing them as open-source for other Reaper users to explore, modify, and use in their own creative work.

> ⚠️ **Note:** This repository is currently in **Alpha**. The code is experimental, parameters may change, and features are being tested in my studio workflow. Use with caution in critical projects.

## Installation

### Option 1: ReaPack (Recommended)

Coming soon. *(I am currently finalizing the `index.xml` for one-click installation via ReaPack.)*

### Option 2: Manual Install

1. Download this repository (Code → Download ZIP).

2. Extract the files to your Reaper Effects folder:
   * **Windows:** `%AppData%\REAPER\Effects\SauravPlaysPiano`
   * **Mac:** `~/Library/Application Support/REAPER/Effects/SauravPlaysPiano`

3. Restart Reaper or run "Scan for new plugins."

## The Tools

### MIDI Note Dropper

**[midi-note-dropper.jsfx](midi-note-dropper.jsfx)**

A simple but powerful tool that probabilistically drops incoming MIDI note-on events. Think of it as a "MIDI gate" based on random chance rather than velocity or other parameters.

#### Parameters

- **Chance to Play %** (0-100): Percentage chance that each note-on event will be allowed through
  - `100%` = all notes pass (no effect)
  - `50%` = roughly half the notes are randomly dropped
  - `0%` = all notes are blocked

#### Use Cases

- **Thin dense patterns**: Take a busy arpeggio or sequence and randomly thin it out for a less mechanical feel
- **Create space**: Drop notes from sustained chords to create movement and breathing room
- **Generative rhythms**: Feed in a steady stream of notes and let randomness create interesting rhythmic patterns
- **Ambient textures**: Combine with delay/reverb to create unpredictable, evolving soundscapes
- **Live improvisation**: Add controlled chaos to your playing

#### Technical Notes

- Only affects MIDI note-on messages (status `0x90` with velocity > 0)
- All other MIDI data passes through unchanged (note-offs, CC, pitch bend, etc.)
- Uses per-note randomization, so results vary with each playback
- Works on all MIDI channels

---

### Phrase Maker

**[phrase-maker.jsfx](phrase-maker.jsfx)**

Generative phrase engine with scale/chord awareness, phrasing, velocity dynamics, and optional swing for melodic composition.

*(Documentation coming soon)*

---

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

You are free to use these in your own music, modify the code, and share them. I only ask that you keep the copyright notice attributing **Saurav Plays Piano**.

---

Maintained by **Saurav Sengupta**.
