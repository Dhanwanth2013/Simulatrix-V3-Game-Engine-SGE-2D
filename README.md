# Simulatrix V3 - Ultimate Single-File 2D Simulation Engine (GJK + EPA Polygon Collisions)

**Author:** Dhanwanth.V
**Version:** 3.0
**License:** MIT

---

## Overview

Simulatrix v3 is a high-performance, single-file 2D physics simulation engine written in Python using Pygame. It features advanced collision detection and response for circles and convex polygons using the Gilbert-Johnson-Keerthi (GJK) algorithm combined with the Expanding Polytope Algorithm (EPA) for penetration depth and contact normal calculation.

This version introduces realistic rotational collision response with angular velocity and torque, spatial hash broadphase for efficient collision pair pruning, and flexible integration methods (semi-implicit Euler and Velocity Verlet). It supports object pooling for efficient memory management and includes a debug HUD, grid overlay, frame recording, and example constraints like springs.

---

## Features

* **Collision Detection:**

  * Circle-circle, circle-polygon, polygon-polygon collisions using GJK + EPA.
  * Realistic rotational collision response with angular velocity and torque.
  * Support for convex polygons with arbitrary vertices.

* **Physics Integration:**

  * Semi-implicit Euler integration.
  * Velocity Verlet integration (toggleable at runtime).

* **Broadphase Optimization:**

  * Spatial hash grid for fast broadphase collision detection.
  * Naive broadphase fallback.

* **Memory Management:**

  * Object pooling for short-lived particles to reduce allocation overhead.

* **Rendering & Debugging:**

  * Pygame-based rendering of circles and polygons.
  * Debug HUD showing performance metrics and simulation stats.
  * Grid overlay toggle.
  * Frame recording to PNG sequence.

* **Runtime Controls:**

  * Hotkeys for toggling grid, HUD, integrator, pause, recording, spawning entities, clearing scene, and adjusting gravity.
  * GUI buttons for common actions.

* **Example Constraints:**

  * Spring constraints between entities.

---

## Installation & Requirements

* Python 3.7+
* Pygame (tested with pygame-ce 2.5.3)

Install Pygame via pip:

```bash
pip install pygame-ce
```

## Usage

Run the engine with:

```bash
python simulatrix_v3.py
```

### Controls

* **G:** Toggle grid overlay.
* **H:** Toggle HUD.
* **V:** Toggle integrator (Euler / Verlet).
* **P:** Pause/unpause simulation.
* **R:** Start/stop frame recording.
* **+ / -:** Spawn or remove 100 balls.
* **C:** Clear and respawn 100 balls.
* **Arrow Up/Down:** Increase/decrease gravity.
* **Number keys 3-9:** Spawn regular polygons with corresponding number of sides.

---

## Version Comparison

| Feature / Aspect        | Simulatrix v1                                   | Simulatrix v2                                           | Simulatrix v3 (This Version)                                          |
| ----------------------- | ----------------------------------------------- | ------------------------------------------------------- | --------------------------------------------------------------------- |
| Collision Detection     | Basic circle-circle & AABB collisions using SAT | Polygon collisions with SAT, improved broadphase        | GJK + EPA for robust polygon & circle collisions                      |
| Rotational Physics      | Limited or no angular velocity and torque       | Angular velocity support with simple collision response | Realistic rotational collision response with torque & angular impulse |
| Broadphase Optimization | Naive broadphase                                | Spatial hash broadphase introduced                      | Optimized spatial hash with neighbor caching                          |
| Integration Methods     | Semi-implicit Euler only                        | Euler & Verlet integration (toggleable)                 | Same as v2 with improved stability                                    |
| Memory Management       | No object pooling                               | Object pooling introduced for particles                 | Enhanced object pooling with reset logic                              |
| Rendering               | Basic circle rendering                          | Polygon rendering added                                 | Improved polygon rendering with rotation                              |
| Debugging & HUD         | Minimal debug info                              | Debug HUD and grid overlay                              | Enhanced HUD with profiling & GUI buttons                             |
| Constraints             | None                                            | Basic spring constraints                                | Same with improved integration                                        |
| Code Structure          | Multiple files                                  | Modularized with better separation                      | Single-file, highly optimized for easy distribution                   |
| Performance             | Moderate                                        | Improved with spatial hash                              | Further optimized with minimal temporaries & caching                  |

---

## Code Highlights

* **GJK + EPA Collision Detection:**

  * Robust algorithm for convex shapes, allowing accurate collision detection and penetration depth calculation.

* **Rotational Collision Response:**

  * Impulse applied at contact points updates both linear and angular velocities, simulating torque and realistic rotations.

* **Spatial Hash Grid:**

  * Efficient broadphase reduces collision checks drastically, enabling hundreds of entities at real-time frame rates.

* **Object Pooling:**

  * Reduces garbage collection overhead by reusing entity objects, especially useful for particle systems.

---

## Extending Simulatrix v3

* Add concave polygon support by decomposing into convex parts.
* Implement friction and rolling resistance in collision response.
* Add more constraints (e.g., rods, joints).
* Integrate with a game framework or UI toolkit.
* Add scripting or configuration for scene setup.

---

## Acknowledgments

* Inspired by classic physics engines and tutorials on GJK and EPA.
* Thanks to the Pygame community for support and tools.

---

## License

MIT License

---
