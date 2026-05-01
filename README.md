 Pinout

  ┌─────────────┬──────────────────────────────────────┬───────────────┐
  │ Arduino Pin │             Connected To             │     Wire      │
  ├─────────────┼──────────────────────────────────────┼───────────────┤
  │ Pin 2       │ PIR sensor — signal (OUT)            │ Yellow/Orange │
  ├─────────────┼──────────────────────────────────────┼───────────────┤
  │ Pin 3       │ Laser module — signal                │ Red           │
  ├─────────────┼──────────────────────────────────────┼───────────────┤
  │ Pin 9       │ Pan servo — signal                   │ Yellow        │
  ├─────────────┼──────────────────────────────────────┼───────────────┤
  │ Pin 10      │ Tilt servo — signal                  │ Yellow        │
  ├─────────────┼──────────────────────────────────────┼───────────────┤
  │ 5V          │ PIR VCC + both servo VCC + laser VCC │ Red           │
  ├─────────────┼──────────────────────────────────────┼───────────────┤
  │ GND         │ PIR GND + both servo GND + laser GND │ Black         │
  └─────────────┴──────────────────────────────────────┴───────────────┘

  ---
  Components & Placement

  Tilt Servo (Pin 10)
  - Mounts to your stand/base
  - Rotates the entire upper assembly up and down
  - This is the bottom-most moving part

  Pan Servo (Pin 9)
  - Mounts on the arm of the tilt servo
  - Rotates left and right
  - Sits on top of the tilt servo

  HC-SR501 PIR Sensor (Pin 2)
  - Mounts on the pan servo arm, facing forward
  - Moves with the pan servo — this is essential to the design
  - Has two small orange pots on it: set the time pot to minimum (CCW), leave sensitivity where it is

  Laser Module (Pin 3)
  - Mounts next to the PIR on the pan servo arm, also facing forward
  - Put a 100Ω resistor in series on the signal/power line if your module has no onboard resistor
  - Both the laser and PIR must point the same direction

  Stack order, bottom to top:
  [Fixed base/stand]
         ↑
  [Tilt servo]      — Pin 10
         ↑
  [Pan servo]       — Pin 9
         ↑
  [Laser | PIR]     — Pins 3 and 2 (side by side, both forward-facing)

  ---
  One thing to watch

  The PIR dome needs a clear forward view — don't let the servo bracket block it. The dome is sensitive to about 120°
  wide, but since it's sweeping with the laser, the effective detection angle per position is much narrower, which is
  what gives you directional accuracy.













 * Human Tracker - Pan/Tilt Laser System
 * ======================================
 *
 * SAFETY NOTICE:
 *   Use ONLY a Class 1 or Class 2 laser (<1mW red laser diode module).
 *   NEVER aim at eyes, faces, or reflective surfaces.
 *   Always test in a safe, controlled environment.
 *   This is for educational/hobby purposes only.
 *
 * How it works:
 *   The PIR sensor is mounted ON the pan servo alongside the laser —
 *   they move together. The system sweeps until the PIR detects human
 *   heat (IR radiation), then locks the laser at that angle.
 *   A small tilt oscillation keeps tracking vertically.
 *   If the target is lost, it holds briefly then resumes sweeping.
 *
 * Components:
 *   - Arduino Uno or Nano
 *   - 2x SG90 or MG90S servo motors (pan + tilt)
 *   - 1x HC-SR501 PIR motion sensor
 *   - 1x Laser diode module (red, <5mW — use the weakest you have)
 *   - Pan/tilt bracket (3D printed or hobby servo bracket kit)
 *   - 100Ω resistor (series with laser if no built-in resistor)
 *   - Small breadboard + jumper wires
 *
 * Wiring:
 *   Pan Servo    Signal → Pin 9   | VCC → 5V | GND → GND
 *   Tilt Servo   Signal → Pin 10  | VCC → 5V | GND → GND
 *   PIR Sensor   OUT    → Pin 2   | VCC → 5V | GND → GND
 *   Laser Module Signal → Pin 3   | VCC → 5V | GND → GND
 *                (add 100Ω in series if your module has no resistor)
 *
 * Mounting:
 *   1. Tilt servo is the BASE — mounts to your stand, tilts up/down.
 *   2. Pan servo mounts on the tilt servo arm — rotates left/right.
 *   3. Laser + PIR mount on the pan servo arm, side by side.
 *      The PIR should face the same direction as the laser dot.
 *   4. Point the whole assembly at roughly human chest height.
 *
 * Tuning:
 *   - TILT_AIM: adjust until laser hits ~chest height from your mount.
 *   - SWEEP_STEP_MS: lower = faster sweep (may miss slow targets).
 *   - HOLD_MS: how long to hold position after losing detection.
 *   - PIR sensitivity: turn the small pot on the HC-SR501 to suit range.
 */

