# PaperTTY

**The original repo can be found [here](https://github.com/joukos/PaperTTY), forked to specifically run a terminal on the v3 2x1.3 inch waveshare display**

## Overview

PaperTTY is a simple Python module for using affordable SPI e-ink displays as a computer monitor, with a Raspberry Pi being the typical computer interfacing with the display.

Driver included is for the 2x1.3inch v3 display, other drivers can be found [over on the Waveshare github](https://github.com/waveshareteam/e-Paper/tree/master/RaspberryPi_JetsonNano/python/lib/waveshare_epd)

Things it can display on the e-ink:
| Subcommand | Description                             |
| ---------- | --------------------------------------- |
| `terminal` | Linux virtual console (`/dev/vcs[au]X`) |

## Usage

PaperTTY is currently packaged using Poetry, however it can be installed via pip too. The instructions here are for Raspberry Pi (please open an issue if you need support for another platform).

**You need to enable SPI first:**
- `sudo raspi-config`
  - `Interfacing Options -> SPI -> Yes`
- May want to reboot just in case

**Then, you also need some system dependencies:**

- `sudo apt install python3-venv python3-pip libopenjp2-7 libtiff5 libjpeg-dev`

### Install with Poetry

The "correct" way to set up PaperTTY is using Poetry. This gives you the most flexibility and handles the virtualenv creation automatically.

**First you need to install Poetry, refer to their [instructions](https://python-poetry.org/docs/#installation).**

Then:

```bash
git clone https://github.com/joukos/PaperTTY.git
cd PaperTTY
poetry install  # if you change something with the deps, do a `poetry update`
poetry run papertty --help
```

To get a direct path for the script (which will be run in the virtual environment with all the dependencies), run in the directory: `echo $(poetry env info -p)/bin/papertty`. Append any options you need and this is what you want to start in a SystemD unit or so, possibly with `sudo` depending on the OS configuration and the feature you wish to use.
