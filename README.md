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

A basic generative phrase engine that tries to create melodic phrases based on musical theory. It understands some basic scales and chords, and tries to generate natural-sounding melodies. If music theory isn't your strong suit, you may find this helpful to create something that can serve as a starting point that you can then build on. I mostly use this to record a long track, listen to the generated phrases, and pick some that I like to play with.

#### Limitations

- It still mostly sounds like computer generated music
- I haven't figured out how to make it random, it will play the same set of phrases each time you restart the plugin
- The phrases don't quite resolve to the chords. For example, in the key of C, I don't hear much difference when the chord is I (C) vs. IV (F)

#### Parameters

**Musical Settings**

- **Root Note** (C-B): The root of the musical key (all melodies stay within this key)
- **Scale** (Major / Minor / Dorian): Choose the tonal character
  - *Major*: Bright, happy, traditional
  - *Minor*: Dark, sad, introspective
  - *Dorian*: Jazzy, bittersweet, modal
- **Current Chord** (I-vii, i-v): The harmonic context. The engine prioritizes chord tones when playing over this chord (e.g., if set to "V", chord tones of V are favored)

**Range Settings**

- **Base Octave** (C1-C6): The starting octave for phrase generation
- **Octave Range** (1-4): How many octaves the melody can span above the base octave

**Phrase Settings**

- **Min Phrase Length** (2-8): Shortest phrase length in notes
- **Max Phrase Length** (3-20): Longest phrase length in notes
- **Use Passing Tones** (Off/On): Allow chromatic passing tones between scale tones
- **Density** (0.1-1.0): How busy the phrase is (sparse → packed with notes)
- **8th Note Amount** (0-1.0): Proportion of quick 8th-note figures in the phrase

**Performance**

- **Min Velocity** (1-127): Minimum MIDI velocity for generated notes
- **Max Velocity** (1-127): Maximum MIDI velocity (random between min/max)

**System**

- **Enable Generation** (Off/On): Toggle phrase generation on/off
- **MIDI Channel** (0-127): Output channel (0 = all channels)

#### How It Works

1. **Scale Awareness**: Melodies stay within the selected scale and root note
2. **Chord Prioritization**: Chord tones of the "Current Chord" setting are weighted heavily in note selection
3. **Voice Leading**: The engine tracks recent notes and penalizes repetition to create smooth, varied melodies
4. **Passing Tones**: When enabled, chromatic tones can connect scale tones naturally
5. **Phrase Building**: Each phrase starts and ends on musically sensible notes (usually chord tones or scale roots)
6. **Randomization**: I'm still working on seeding the random number generator. For now, it will play the same set of phrases each time you restart the plugin

#### Use Cases

- **Generative composition**: Create full melodic sequences automatically, then edit or re-roll
- **MIDI sketch ideation**: Quickly generate phrase ideas to inspire further composition
- **Ambient soundscapes**: Long, sparse phrases create meditative, evolving textures
- **Harmonic framework**: Play chord progressions separately while this generates fitting melodies on top
- **Learning**: Understand how melody works within harmonic/scalar constraints
- **Filling gaps**: Generate fills or connecting phrases between your own musical ideas

#### Technical Notes

- Generates MIDI note-on events with random velocities between min/max
- Note-offs are handled by the Reaper MIDI engine
- All other MIDI data passes through unchanged
- Phrase length and note selection are randomized for variation
- Performance is tuned for real-time generation without latency
- Sometimes notes slightly outside the octave range might be selected to try and keep the phrase melodic

---

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

You are free to use these in your own music, modify the code, and share them. I only ask that you keep the copyright notice attributing **Saurav Plays Piano**.

---

Maintained by **Saurav Sengupta**.
