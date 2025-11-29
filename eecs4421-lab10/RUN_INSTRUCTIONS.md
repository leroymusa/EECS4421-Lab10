# Running the Boids Simulation and Preparing Media

## Current status
- I was able to download the `boids_py` source code, but this environment currently lacks a usable Python interpreter and `pip`. As a result I could not actually run the simulation or record the eight clips.

## Step 1: Install Python + dependencies
1. Install Python 3 (Windows installer from https://www.python.org/downloads/ usually works). Make sure the installer enables the “Add Python to PATH” option so that `python` and `pip` are available from PowerShell.
2. From the project root (where `main.tex` lives), install the runtime dependency:

   ```powershell
   py -m pip install pygame
   ```

3. (Optional) Delete `boids_py.zip` and `boids_py-master/` if you prefer to redo the clone from scratch by running `git clone https://github.com/meznak/boids_py.git`.

## Step 2: Run the eight parameter settings
Run `boids_py-master/main.py` with the following parameter combinations. Each command should be executed in the `boids_py-master` directory. The CLI now exposes the relevant boid parameters via `--max_force`, `--perception`, and `--crowding`, so there is no need to edit `boid.py`.

- **Clip 01:** `py main.py --geometry 1280x720 --number 120 --max_force 1 --perception 12.582 --crowding 16`
- **Clip 02:** `py main.py --geometry 1280x720 --number 120 --max_force 1 --perception 12.582 --crowding 232`
- **Clip 03:** `py main.py --geometry 1280x720 --number 120 --max_force 1 --perception 258 --crowding 16`
- **Clip 04:** `py main.py --geometry 1280x720 --number 120 --max_force 1 --perception 258 --crowding 232`
- **Clip 05:** `py main.py --geometry 1280x720 --number 120 --max_force 32 --perception 12.582 --crowding 16`
- **Clip 06:** `py main.py --geometry 1280x720 --number 120 --max_force 32 --perception 12.582 --crowding 232`
- **Clip 07:** `py main.py --geometry 1280x720 --number 120 --max_force 32 --perception 258 --crowding 16`
- **Clip 08:** `py main.py --geometry 1280x720 --number 120 --max_force 32 --perception 258 --crowding 232`

If the CLI does not expose `max_force`, `perception`, or `crowding`, modify `boid.py` to set the static class attributes before creating the boids (e.g., assign values to `Boid.max_force` etc. prior to `add_boids()`), or wrap the configuration in a small launcher script.

## Step 3: Capture the clips
1. Use `ffmpeg` (or any screen recorder) to capture a 10–15 second clip while the simulation is running. An example command for Windows with `ffmpeg`:

   ```powershell
   ffmpeg -f gdigrab -framerate 60 -i title="BOIDS!" -t 15 clip01.mp4
   ```

   - Replace `clip01.mp4` with a descriptive name for each of the eight runs.
   - The `title="BOIDS!"` argument tells `ffmpeg` to grab the window that the simulation creates.
2. For each clip, export or screenshot a representative frame (e.g., pause at a visually interesting moment and take a screenshot). Name them `setting_01.png` through `setting_08.png` and place the files into `figures/` or `imgs/` so that the LaTeX placeholders pick them up.
3. Create title slides (e.g., in PowerPoint or by using `ffmpeg` filters) that note your name/student number/course/lab and the parameter settings. Concatenate the title slide, the clip, and the setting-specific title slide into a single deliverable video.

## Step 4: Rebuild the report
1. Once the image files exist, run:

   ```bash
   pdflatex main.tex
   pdflatex main.tex
   ```

   to embed the new figures into `main.pdf`.
2. Verify that `setting_01.png`, `setting_04.png`, and `setting_08.png` (and others, if you choose to expand) show up in the report. The `\imgorplaceholder` macro will print a helpful missing-file notice if any are absent.

## Notes
- Since the environment lacks Python, `pip`, and GUI support, I could not complete the captures myself. Once Python is available you can run the commands above and replace the placeholder graphics/videos in the report.

