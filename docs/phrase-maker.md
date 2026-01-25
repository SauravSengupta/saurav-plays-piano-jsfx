# Phrase Maker

**[phrase-maker.jsfx](../jsfx/phrase-maker.jsfx)**

A generative phrase engine that tries to create melodic phrases based on simple musical theory. It understands scales and chords, and tries to generate natural-sounding melodies that follow a chord progression. It features a **real-time piano roll visualization** and a basic built-in **chord progression sequencer**.

If music theory isn't your strong suit, you may find this helpful to create something that can serve as a starting point that you can then build on. I mostly use this to record a long track, listen to the generated phrases, and then pick some to work on further.

## Limitations

- It still mostly sounds like computer generated music, and probably always will

## Parameters

### Musical Settings

- **Root Note** (C-B): The root of the musical key (all melodies stay within this key)
- **Scale** (Major / Minor / Lydian): Choose the tonal character
  - *Major*: Bright, happy, traditional
  - *Minor*: Dark, sad, introspective
  - *Lydian*: Dreamy, bright, floating

### Range Settings

- **Base Octave** (C1-C6): The starting octave for phrase generation
- **Octave Range** (1-4): How many octaves the melody can span above the base octave

### Phrase Settings

- **Min Phrase Length** (2-8): Shortest phrase length in notes
- **Max Phrase Length** (3-20): Longest phrase length in notes

### Progression Sequencer

- **Loop Length** (1-8): Number of chords in the loop
- **Prog Chords 1-4** (I-vi, II): Define your chord progression (includes Major II)
- **Measures Per Chord** (1-8): Duration of each chord
- **Continuous Mode** (Off/On): When enabled, minimizes rests between phrases for a continuous flow
- **Playback Speed** (0.5x - 8x): Scales the playback speed relative to the project tempo

### Performance

- **Min Velocity** (1-127): Minimum MIDI velocity for generated notes
- **Max Velocity** (1-127): Maximum MIDI velocity (random between min/max)
- **Sustain Pedal Modeling** (Off/On): Intelligent sustain pedal automation. It holds the pedal for chord tones to create resonance, but automatically lifts and re-pedals when non-chord tones create too much harmonic dissonance ("mud").

### System

- **Enable Generation** (Off/On): Toggle phrase generation on/off
- **MIDI Channel** (1-16): Output channel for generated notes (pass-through MIDI keeps its original channel)

## How It Works

1. **Scale Awareness**: Melodies stay within the selected scale and root note
2. **Chord Prioritization**: Chord tones of the "Current Chord" setting are weighted heavily in note selection
3. **Voice Leading**: The engine tracks recent notes and penalizes repetition to create smooth, varied melodies
4. **Look-Ahead Resolution**: Phrases are aware of upcoming chord changes and will try to resolve to a target note that fits the *next* chord if the phrase crosses a boundary
5. **Phrase Building**: Each phrase starts and ends on musically sensible notes
6. **Pedal Modeling**: (Optional) Simulates a pianist's foot, sustaining chord tones for richness while clearing the pedal to avoid muddiness when changing harmonies or playing passing tones.

## Visualization

![Phrase Maker UI](../assets/images/phrase-maker-ui.png)

The plugin includes a custom UI that displays:
- **Current & Next Chord**: Large, clear display of the harmonic context (e.g., C, Am)
- **Piano Roll**: Continuous scrolling visualization showing history and upcoming notes
- **Status**: Visual feedback when the engine is resting between phrases

## Use Cases

- **Generative composition**: Create full melodic sequences automatically, then edit or re-roll
- **MIDI sketch ideation**: Quickly generate phrase ideas to inspire further composition
- **Ambient soundscapes**: Long, sparse phrases create meditative, evolving textures
- **Harmonic framework**: Play chord progressions separately while this generates fitting melodies on top
- **Filling gaps**: Generate fills or connecting phrases between your own musical ideas

## Technical Notes

- Generates MIDI note-on events with random velocities between min/max
- Sends note-offs itself before triggering the next note to avoid hangs
- Sends MIDI CC 64 (Sustain) messages when Pedal Modeling is enabled
- All other MIDI data passes through unchanged
- Phrase length and note selection are randomized for variation
- Performance is tuned for real-time generation without latency
- Sometimes notes slightly outside the octave range might be selected to try and keep the phrase melodic

### Timing Model

- Notes are scheduled on an 8th-note grid; phrases advance by 8ths and align back to quarter-note boundaries when needed
- After a phrase finishes, the plugin inserts a short rest (in quarter notes) before starting the next phrase (unless Continuous Mode is enabled)

## Audio Demo

Here's a short audio [clip](https://sauravplayspiano.com/audio/phrase-maker-lydian.mp3) that shows the plugin in action.
