# G1 Depth Walker

Drive a simulated Unitree G1 humanoid through stairs, ramps, gaps and obstacles using a depth-based walking policy. Each visitor runs and controls an independent simulation in their browser.

**[Launch the interactive demo](https://munna-manoj.github.io/g1-depth-walker/)**

## Controls

| Control | Action |
| --- | --- |
| W | Walk forward |
| Q / E | Turn left / right |
| S | Stop the forward command |
| F | Toggle forward walking with heading hold |
| R | Respawn at the terrain hub |
| Space | Pause or resume |
| Mouse drag / wheel | Orbit / zoom the camera |

On-screen buttons provide the same controls. Sideways and backward walking are not trained in this policy. The robot automatically respawns after a fall.

## Running the demo

Use a current browser with WebAssembly, WebGL, Web Workers and gzip decompression support. The self-contained page is approximately 14.7 MB; initial loading depends on the connection and device. Choose **Low power** graphics for slower laptops.

Physics and policy inference run in a background worker. Graphics quality adapts to rendering performance. Physics advances at 200 Hz and the policy at 50 Hz of simulated time; the speed indicator shows when the device runs slower than real time. Physics initialization reserves approximately 300 MB of WebAssembly memory, with additional memory used by rendering and the browser.

The demo runs entirely on the visitor's device and controls a simulated robot. No installation, account, or connection to a physical robot is required.

GitHub Pages publishes the root of the `main` branch.

## Credits

- Physics: [MuJoCo](https://github.com/google-deepmind/mujoco), Apache 2.0; see [license](licenses/MuJoCo-Apache-2.0.txt).
- Rendering: [three.js](https://github.com/mrdoob/three.js), MIT; see [license](licenses/three.js-MIT.txt).
- Robot description: [Unitree Robotics G1](https://github.com/unitreerobotics/unitree_ros/tree/master/robots/g1_description), BSD 3-Clause; see [license](licenses/Unitree-BSD-3-Clause.txt).
- Terrain hub adapted from the [Watch Your Step web demo](https://leggedrobotics.github.io/watch-your-step/) by Matthias Heyrman, Chenhao Li, Ioannis Dadiotis and Marco Hutter. Upstream [code](https://github.com/leggedrobotics/foothold-prediction-model) is MIT-licensed; see [license](licenses/Watch-Your-Step-MIT.txt).

The embedded G1 depth walking policy is separate from the Watch Your Step foothold-prediction policy. Third-party licenses apply to their respective components.
