# OCA's A1 Evo Acoustica

This edit is specifically for multi-sub configurations. 

** IF YOU DON'T LIKE THE RESULTS AFTER THE FIRST PASS, LOAD THE PRE-PROCESSED MEASUREMENTS, IN ALL SPL WINDOW, APPLY NO MORE THAN 1/24th SMOOTHING, SAVE, AND RELOAD IT AND RE-RUN THE OPTIMISATION. I'VE FOUND THAT THIS EQUALISES THE VOLUMES MUCH BETTER **

Differences - 

1. The raw imported IRs from Audyssey are now windowed with Tukey windows, and a frequency-dependent windowing. This provides a more robust estimation of the actual frequency response of the speaker. No other downstream windowing is changed or affected.
2. C is back to not being treated with L/R
3. Phase unwrapping is performed for all analysis steps
4. During inter-sub alignment, flatness of response in the 20-120Hz band, group delay and phase cohererence are optimised along with SPL
5. The same optimisations are also applied for the sub-L/R integration
6. During these alignments, fMax is reduced to 150 instead of 250 Hz. This specifically assumes reference grade subwoofers.
7. And therefore, all crossovers are capped at 120Hz to avoid bass localisation. This of course assumes atleast bookshelf sized speakers.
8. The inverse room response filter now starts a bit before the computed optimal crossover-frequency for that speaker (pair). This avoids double-dipping below the Xover.
9. A second pass of volume equalisation is performed on the predicted, final EQ'd speaker responses. However, I haven't gotten around to fixing the printed message, because in the 2nd pass, there's no "filter hack" equalisation
10. Definitely bump down your subs volume by around -3dB in the AVR menu after transfer. I haven't gotten around to fixing this yet.
11. ----IMPORTANT----
12. The tunable parameter weights are in alignFronts() and optimizeSubs(). Play with them.

** A1Evo_Alt.html **

This particular version filters FL/FR starting at 16Hz as in OCA's original, but creates the filters for the rest of the speakers starting at customCrossover. Then in generateRoll(), FL and FR are not rolled at their custom crossover, but at 16Hz. This allows you to post-hoc set Fronts to "Full Range" in the AVR Menu, Subwoofer to LFE+Main, and Bass Extraction Freq to the crossover assigned for your Fronts. The integration is seamless and the bass is full. 

This is purely a hobby thing, and so this will remain independent from the main fork, and not be updated regularly.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# A1 Evo Acoustica
Audyssey-based Sound Optimization Tool for Denon/Marantz AVRs.

Harnessing the power of [REW](https://www.roomeqwizard.com/) and proprietary algorithms, A1 Evo aims to produce world-class room correction for MultEQ, MultEQ XT, and XT32 AVRs. Improvements remain worthwhile for basic MultEQ, but improve further with more capable XT & XT32 hardware.

AVRs must be compatible with MultEQ Mobile app (~2016 onward), though the app itself is not required.

### Key Resources
* [YouTube Guide](https://www.youtube.com/watch?v=wQHF0-MOMMY)
* [Downloads](https://drive.google.com/drive/folders/1O-KcP9jfBYZePW9lGPE2sbqrx_x96Vrr)
* [Discussion thread](https://www.avsforum.com/threads/acoustica-latest-and-greatest-from-oca-for-denon-marantz-only.3324025/)
* [Quick Guide Windows](./docs/quick-guide-windows.md)
* [Quick Guide Mac](./docs/quick-guide-mac.md)

### Local Build & Development

#### Prerequisites

- [Git](https://git-scm.com/downloads) - Version control system
- [Node.js](https://nodejs.org/) - JavaScript runtime (v18 or later recommended)
- [npm](https://www.npmjs.com/) - Package manager (included with Node.js)

##### Linux Installation Example (Debian/Ubuntu)

```bash
# Update package lists
sudo apt update

# Install Git
sudo apt install git

# Install Node.js and npm using NodeSource repository
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

# Verify installations
git --version
node --version
npm --version
```

#### Clone the Repository

```bash
git clone https://github.com/ObsessiveCompulsiveAudiophile/A1EvoAcoustica.git
cd A1EvoAcoustica
```

#### Install Dependencies

```bash
npm ci
```

#### Start the Program

```bash
npm start
```

This will launch the A1 Evo Acoustica tool.

#### Build Executables

```bash
npm run build
```

Or for a specific platform ([available options](./package.json))

```bash
npm run build-windows
```

[LICENSE](./LICENSE)
