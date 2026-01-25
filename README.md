# Saurav Plays Piano JSFX

A collection of custom JSFX plugins for **Reaper**, designed and developed by [Saurav Plays Piano](https://sauravplayspiano.com).

This is a collection of Reaper plugins I wrote to help me with some of my ambient / neo-classical piano productions. I am releasing them as open-source for other Reaper users to explore, modify, and use in their own creative work.

> ⚠️ **Note:** This repository is currently in **Alpha**. The code is experimental, parameters may change. Use with caution in critical projects.

## The Plugins

| Plugin | Description |
|--------|-------------|
| [MIDI Note Dropper](docs/midi-note-dropper.md) | Randomly drop notes for thinning patterns and adding controlled chaos |
| [Phrase Maker](docs/phrase-maker.md) | Generative melody engine with chord awareness and piano roll visualization |
| [Chord Timing Meter](docs/chord-timing-meter.md) | Practice tool to visualize chord timing and velocity accuracy |

## Installation

### Option 1: ReaPack (Recommended)

1. In Reaper, go to **Extensions → ReaPack → Import repositories...**
2. Paste this URL (raw index):

   ```
   https://github.com/SauravSengupta/saurav-plays-piano-jsfx/raw/refs/heads/main/index.xml
   ```

3. Click OK and ReaPack will download the latest versions automatically.
4. Browse available plugins via **Extensions → ReaPack → Browse packages**. Searching for **Saurav** will bring up all my plugins.
5. Right-click the ones you want to install, and select **Install <version>**.

### Option 2: Manual Install

1. Download this repository (Code → Download ZIP).

2. Extract the files to your Reaper Effects folder:
   * **Windows:** `%AppData%\REAPER\Effects\SauravPlaysPiano`
   * **Mac:** `~/Library/Application Support/REAPER/Effects/SauravPlaysPiano`

3. Restart Reaper or run "Scan for new plugins."

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

You are free to use these in your own music, modify the code, and share them. I only ask that you keep the copyright notice attributing **Saurav Plays Piano**.

---

Maintained by **Saurav Sengupta**.
