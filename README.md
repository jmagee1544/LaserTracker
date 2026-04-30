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
