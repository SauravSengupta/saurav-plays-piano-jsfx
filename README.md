# REAPER JSFX: Melody Maker & MIDI Note Dropper

Two JSFX scripts for REAPER:

- Melody Maker (melody-maker.jsfx): generative phrase engine with scale/chord awareness, phrasing, velocity dynamics, and optional swing.
- MIDI Note Dropper (midi-note-dropper.jsfx): probabilistically thins incoming MIDI note-on events.

## Install (Windows)
Copy the `.jsfx` files to `%AppData%\REAPER\Effects` and restart REAPER. Insert them via the FX browser under "JSFX".

## Melody Maker — Key Sliders
- Root Note, Scale, Current Chord (Roman Numeral)
- Base Octave, Octave Range, Min/Max Phrase Length
- Use Passing Tones, Density
- Min/Max Velocity, Enable Swing Notes, 8th Note Amount
- Enable Generation, MIDI Channel, Init Jitter

## MIDI Note Dropper — Slider
- Chance to Play %: higher values pass more notes; lower values drop more.

## Notes
- Designed for real-time use; no build steps required.
- Works with REAPER’s JSFX runtime.
