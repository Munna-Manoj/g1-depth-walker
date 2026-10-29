# G1 Depth Walker — WYS v4 course

**[Launch the interactive demo](https://munna-manoj.github.io/g1-depth-walker/)** · previous version (E1 policy, terrain hub only): [e1/](https://munna-manoj.github.io/g1-depth-walker/e1/)

Drive a simulated Unitree G1 humanoid through the Watch Your Step hub and 17 added capability courses (stepping stones,
stone stairs, planks, twin rails, an elevated course, stairs, platforms, gaps, a ramp, boxes, rough ground) with a
depth-based walking policy. Each visitor runs and controls an independent simulation in their browser.

## Controls

| Control | Action |
| --- | --- |
| W | Walk forward (hold; up to 1 m/s) |
| Q / E | Turn left / right in place |
| S | Stop |
| F | Toggle forward walking at 0.6 m/s with heading hold |
| R | Back to the hub centre |
| M | Course map: click a course on the map or in the list to stand in front of it; Share makes a result card |
| O | Drop an obstacle: pick a size, tap the ground 1–3 m ahead of the robot (R clears them) |
| P | Autopilot: the robot walks to the start of the picked course (or the one it stands on) and the policy runs it; any drive key takes over (no medal) |
| T | Tour every course the autopilot can clear (also *Tour* in the map); any key ends it |
| L | Replay the last timed run (Space play / pause, ← / → 2 s, 0.5× / 1× / 2×, Esc back to live); ↻ in the map list replays your best run on a course |
| 1–9, Shift+1–8, [ / ] | Courses 8–16, 17–24, previous / next |
| Space | Pause or resume |
| H | Help and display options (depth inset, course signs, graphics) |
| Drag / wheel / pinch | Orbit / zoom the camera |

On-screen buttons provide the same controls on phones and tablets. Sideways and backward walking are not trained in this
policy. After a fall the robot goes limp and restarts at the hub centre after 2 s.

The map: courses 0–7 are the Watch Your Step hub around the start (grey); 8–24 were added for this project (blue, red =
the hard pair), each reachable from the floor over its own stairs. Every course has a numbered sign in the 3D view and
the minimap (bottom left) shows where the robot is.

## Challenge, obstacles, sharing

Walk into any course from its start end and a timer runs (simulation time, so a slow device or a pause changes nothing);
reach the far end without falling or leaving the course for more than 2 s. Par is the time the policy's own autopilot
(F) takes: beat it by 5 % for gold, within 1.3x for silver, any finish for bronze; the one course the autopilot cannot
clear (stepping stones) is marked expert. Best times and a ghost of your best run (replayed on the minimap and in the
view) stay in this browser only. Share (course map, or after a clear) draws a 1200 x 630 card with your path and bests
to download, plus post text to copy.

Obstacles: a 10, 15 or 20 cm step-up or a 0.4 m wide, 40 cm tall block, placed on the open floor (never on a course or
during a timed run), up to 6 at once. Each size is labelled with what this policy did when it walked at it on flat
ground: it stepped over every step-up in 6 / 6 tries and stopped in front of the block in 6 / 6.

Autopilot and replay: ▶ in the course list (or P) lets the policy's own autopilot run a course for you; autopilot runs and runs
you take over from are timed but never give a medal. Every timed run is recorded (full robot pose at 25 Hz): L replays the last
one, ↻ your best run on that course (kept in this browser). The live robot waits where it was during a replay.

After 20 s without input the page tours four courses by itself; any key or tap gives control back (`?attract=0` turns
this off, e.g. for embedding).

## Running the demo

Use a current browser with WebAssembly, WebGL, Web Workers and gzip decompression support (Chrome / Edge 80+, Safari
16.4+ / iOS 16.4+, Firefox 113+). The self-contained page is about 10.1 MB; open it directly or host the folder as a
static site (GitHub Pages publishes the root of the branch; `.nojekyll` is included). Choose **Low power** graphics (H)
on slower laptops; **Auto** steps the resolution down by itself when the frame rate stays low.

Physics (MuJoCo 3.14, WebAssembly, 200 Hz) and the policy (50 Hz) run in a background worker; the speed row of the HUD
shows when the device runs slower than real time. A hidden tab pauses the simulation. The demo runs entirely on the
visitor's device and controls a simulated robot: no installation, account or connection to a physical robot.

## Credits

- Physics: [MuJoCo](https://github.com/google-deepmind/mujoco), Apache 2.0; see [license](licenses/MuJoCo-Apache-2.0.txt).
- Rendering: [three.js](https://github.com/mrdoob/three.js), MIT; see [license](licenses/three.js-MIT.txt).
- Robot description: [Unitree Robotics G1](https://github.com/unitreerobotics/unitree_ros/tree/master/robots/g1_description), BSD 3-Clause; see [license](licenses/Unitree-BSD-3-Clause.txt).
- Terrain hub (courses 0–7) adapted from the [Watch Your Step web demo](https://leggedrobotics.github.io/watch-your-step/) by Matthias Heyrman, Chenhao Li, Ioannis Dadiotis and Marco Hutter. Upstream [code](https://github.com/leggedrobotics/foothold-prediction-model) is MIT-licensed; see [license](licenses/Watch-Your-Step-MIT.txt).

The embedded G1 depth walking policy (S2, iteration 9000; weights stored as float16) is separate from the Watch Your Step
foothold-prediction policy. Third-party licenses apply to their respective components.

Build: policy s2_stones_beams_15k_it9000, index.html sha256 fd2b3db75812
