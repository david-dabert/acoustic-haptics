# acoustic-haptics 🔊⚡

[![CI](https://github.com/david-dabert/acoustic-haptics/actions/workflows/ci.yml/badge.svg)](https://github.com/david-dabert/acoustic-haptics/actions/workflows/ci.yml)
[![npm version](https://img.shields.io/npm/v/acoustic-haptics.svg?color=blue)](https://www.npmjs.com/package/acoustic-haptics)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Missing-fundamental psychoacoustic sub-bass & noise-penetrating transient cue engine for the Web Audio API.**

Delivers tactile visceral feedback, sub-bass "thumps", and high-contrast acoustic cues through tiny wireless earphone drivers (AirPods) without clipping or distortion—even in 85–92 dBA noisy gym environments.

---

## The Acoustic Problem

1. **Small Transducer Roll-Off:** Smartphone speakers and in-ear monitors physically roll off steeply below 100 Hz. Attempting to play pure 40–80 Hz sine waves causes speaker distortion, clipping, or complete silence.
2. **Broadband Gym Masking:** Commercial gyms run background music and metal plate impacts at 85–92 dBA. Standard pure-tone sine beeps or speech synthesis get completely drowned out.

## The Psychoacoustic Solution

`acoustic-haptics` solves physical transducer limits using auditory neurobiology:

### 1. Missing Fundamental Illusion (Virtual Pitch)
When two higher harmonic frequencies $f_1 = 2f_0$ and $f_2 = 3f_0$ (e.g. 160 Hz and 240 Hz) are played together with phase alignment, the human auditory cortex automatically reconstructs the perceived fundamental pitch $f_0 = 80\text{ Hz}$.

This produces a perceived deep tactile "sub-bass thump" that feels physical in the ear, while remaining strictly within the linear operating range of the physical driver!

### 2. Dirac Transient Attack (Auditory Precedence)
A high-frequency $3-5\text{ ms}$ impulse at $2.8\text{ kHz}-3.2\text{ kHz}$ precedes the cue. Human auditory onset detectors trigger on rapid risetimes, allowing cues to cleanly pierce through dense background EDM and clanking weights without increasing overall volume.

### 3. Intelligent Collision Prevention
Automatically manages cue priority (Form Deficit > Rep Success > Velocity Loss > Turnaround > Cadence) and enforces a minimum $75\text{ ms}$ inter-cue spacing to prevent acoustic distortion or buzzing.

---

## Installation

```bash
npm install acoustic-haptics
```

## Quick Start

```typescript
import { hapticResonanceAudio, HapticResonanceAudioService } from 'acoustic-haptics';

// 1. Rep Completed: Ascending perfect fifth (C5 -> G5) + 80 Hz virtual thump + 3 kHz click
hapticResonanceAudio.playRepSuccess();

// 2. Velocity Loss (>20% fatigue drop): Tritone descent (620 Hz -> 415 Hz)
hapticResonanceAudio.playVelocityLossWarning(0.25);

// 3. Turnaround inflection: Tactile sub-bass thump at inflection depth
hapticResonanceAudio.playTurnaround();

// 4. Biomechanical Breakdown / Injury Risk: Dissonant 27.7 Hz acoustic beating
hapticResonanceAudio.playFormDeficitAlert();

// 5. Raw Missing Fundamental Thump
hapticResonanceAudio.playMissingFundamentalThump(80 /* virtual f0 */, 0.08 /* duration */, 0.35 /* gain */);
```

---

## Features

- **100% Client-Side Synthesis:** Zero audio samples, zero MP3/WAV assets, zero network fetch.
- **Sub-5ms Latency:** Native Web Audio oscillator and exponential envelope synthesis.
- **Earbud-Safe:** Bypasses low-frequency roll-off without speaker excursion damage.
- **Anti-Pop Gain Ramping:** Exponential decay curves eliminate click artifacts.
- **Headless-Safe:** Gracefully falls back in SSR/Node.js testing environments without errors.

---

## License

MIT © [David Dabert](https://github.com/david-dabert)
