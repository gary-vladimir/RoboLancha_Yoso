# Lancha Robot V1 — Implementation Plan

**Project:** Remote-Controlled Surface Robot for Lechuguilla Harvesting  
**Version:** V1 (Fully Remote-Controlled, No Autonomy)  
**Date:** April 2026  
**Target Environment:** Swampy reservoir with heavy surface vegetation

---

## 1. System Overview

The Lancha Robot is a slow, stable, waterproof RC surface vessel that navigates a weed-choked reservoir, grabs lechuguilla plants with a hydraulic arm, stores them in an onboard container, and returns to shore — all piloted by a human operator via radio control with live FPV video.

**Five core subsystems:**

1. Hull & Flotation Platform
2. Propulsion (differential thrust)
3. Hydraulic Robotic Arm (3-DOF)
4. Power System (battery)
5. Control, Video & Electronics

---

## 2. Hull & Flotation Platform

### 2.1 Design: Catamaran with Recycled Pontoons

We use a **twin-pontoon catamaran layout**. This gives us maximum stability (critical when the arm is lifting weight off to one side), a wide flat deck for the cargo container, and simple construction.

**Pontoons — Option A (Preferred): Recycled 200L (55-gal) Plastic Drums**

- Source: 2× used HDPE plastic drums (food-grade preferred — they're clean and cheap). These are available for ~$10–15 USD each at recycling yards or industrial surplus.
- Each drum displaces ~200L = ~200 kg of buoyancy. Two drums = **~400 kg total buoyancy**. After subtracting the robot's own weight (~40–50 kg estimated) and payload (30 kg), we have a massive safety margin. The drums will sit very high in the water.
- Seal the drum bungs with silicone + threaded caps. Add a bead of marine silicone around every cap as insurance.
- Optionally fill the bottom 5 cm of each drum with closed-cell spray foam — if a drum ever cracks, it won't fully flood.
- Mount drums horizontally, lengthwise, parallel to each other, spaced ~1.0–1.2 m apart (center to center).

**Pontoons — Option B (Backup): PVC Pipe Pontoons**

- 2× PVC pipes, 250 mm (10") diameter, ~2 m long, capped and sealed at both ends.
- Less buoyancy than drums (~98L each) but more hydrodynamic.
- Use PVC cement + primer on end caps for watertight seal.

**Recommendation:** Go with the drums. They're cheaper, have more buoyancy, and the robot doesn't need to be fast — hydrodynamics don't matter at 4 km/h.

### 2.2 Frame / Deck

- **Material:** 1" square aluminum tubing OR (cheaper) 1.5" schedule-40 PVC pipe frame.
- Build a rectangular frame (~1.5 m long × 1.2 m wide) that sits across both pontoons.
- Attach pontoons to frame using U-bolts + rubber padding (to avoid cracking the drums), or ratchet straps through 3D-printed saddle clamps.
- Deck surface: a sheet of 12 mm marine plywood, or a recycled plastic cutting board / HDPE sheet screwed onto the frame. This gives a flat surface to mount everything.

### 2.3 Cargo Container

- **Simplest solution:** A large **recycled plastic laundry basket** or **plastic crate** (~60L–80L) zip-tied or bolted to the deck center.
- Must have drainage holes (or drill them) so water drains out as wet plants are loaded.
- Dimensions: approximately 60 cm × 40 cm × 35 cm tall. This comfortably holds 50 lechuguilla plants.
- Mount it slightly aft of center to counterbalance the arm (which mounts at the front).

### 2.4 Weed Deflectors

- Mount **angled PVC pipe "cowcatchers"** at the front of each pontoon — V-shaped deflectors that push floating vegetation aside before it reaches the propellers at the rear.
- Simple: two ~50 cm PVC pipes per pontoon, angled forward at ~30° in a V-shape, attached with pipe clamps.

---

## 3. Propulsion System

### 3.1 Motor Selection

- **2× brushless DC trolling motors** (or repurposed bilge pump motors / drill motors).
- **Budget option (recommended):** 2× 775-class brushless DC motors (12V, ~3000 RPM, ~150W each). These are extremely common, cost ~$5–10 each, and have plenty of power for a slow vessel.
- Each motor drives a propeller on one side of the hull (port and starboard), mounted at the stern of each pontoon.

### 3.2 Propellers

- **3D-print weed-shedding propellers.** This is a key custom part.
- Design: 3-blade, ~80 mm diameter, with **swept-back blades and smooth leading edges** (no sharp nooks where weeds can wrap). Thick blade roots.
- Material: PETG filament (better water/UV resistance than PLA). Print at 100% infill for strength.
- Attach to motor shaft via 3D-printed coupler + set screw, or use a standard RC boat prop adapter.
- **Weed guard:** 3D-print a ring shroud around each propeller — a cylindrical duct with a cross-bar grid at the inlet (~2 cm spacing). This prevents long weeds from reaching the blades. Think of it as a cage around the prop.

### 3.3 Motor Mounting

- Each motor sits inside a **3D-printed motor pod** that bolts to the underside of the frame at the stern of each pontoon.
- The pod should angle the motor shaft ~5–10° downward so the prop is submerged ~5–8 cm below waterline.
- Seal the motor shaft exit with a **rubber lip seal** (or a silicone gasket pressed around the shaft). The motor itself can be slightly above waterline inside the pod.
- **Cable routing:** Motor power wires run through the PVC frame tubes (using them as conduit) back to the electronics box on deck.

### 3.4 Motor Control

- **2× 30A brushless ESCs** (Electronic Speed Controllers) — standard RC car/boat ESCs, ~$8–12 each.
- These accept standard PWM signal from the RC receiver and drive the motors forward/reverse.
- Differential steering: left stick controls left motor, right stick controls right motor (tank-style), OR mixed via the RC transmitter's mixing function.

---

## 4. Hydraulic Robotic Arm (3-DOF)

This is the most complex subsystem. The key insight: **all electric components (pump, valves, motor) stay sealed inside the electronics box on deck.** Only passive hoses and the arm's metal/printed structure are exposed to the elements.

### 4.1 Hydraulic Power Unit (HPU)

- **Pump:** A small 12V DC hydraulic gear pump. These are sold for truck tailgates and dump trailers. Look for a ~1.5–2.0 GPM, 12V unit with a built-in reservoir (~1–2L). Cost: ~$40–80 on Amazon/AliExpress.
- **Fluid:** Standard hydraulic oil (AW-32 or AW-46). ~1–2 liters total system volume.
- **Valves:** 3× small 12V DC solenoid-operated directional control valves (4-way, 3-position, spring-centered). One per cylinder. These are the most expensive hydraulic components — look for 12V mini hydraulic solenoid valves (~$20–40 each). Alternatively, use **manual-style cable-operated spool valves** actuated by small servos for a cheaper approach.
- The pump, reservoir, and valves all mount **inside the sealed electronics box** on deck.

### 4.2 Cylinders

- **3× small hydraulic cylinders** (double-acting, ~20 mm bore, 100–200 mm stroke). These are available as "micro hydraulic cylinders" on AliExpress for ~$10–25 each.
- Cylinder assignment:
  - **Cylinder 1 — Lift/Lower:** Mounted at the arm's shoulder joint. Raises and lowers the entire arm. Stroke: ~150–200 mm.
  - **Cylinder 2 — Rotate/Swivel:** Mounted at the base. Pushes a lever arm to rotate the arm left/right (~90° sweep is sufficient). Stroke: ~100–150 mm.
  - **Cylinder 3 — Gripper Open/Close:** Mounted on the claw mechanism at the arm's end. Stroke: ~50–100 mm.

### 4.3 Arm Structure

- **Main boom:** ~80 cm long. Made from **1.5" square aluminum tube** or (cheaper) **1" schedule-40 steel pipe**. Needs to handle ~5 kg at full extension (a wet lechuguilla plant).
- **Base mount:** A vertical post (pipe flange bolted to the deck) with a thrust bearing or lazy susan bearing at the top for rotation. The arm pivots on this bearing. Mount at the **front of the deck**, slightly off-center to keep the operator's camera view clear.
- **Lift pivot:** A hinge/pivot point ~15 cm above the base post, with Cylinder 1 pushing up on the boom.
- **Rotation mechanism:** Cylinder 2 connects from the deck frame to a lever arm welded/bolted to the rotating base. It pushes the arm left or right.

### 4.4 Gripper / Claw

- **3D-print the gripper.** This is where 3D printing truly shines.
- Design: A simple **two-finger parallel gripper** with wide, textured grip pads. Each finger ~15 cm long, ~5 cm wide. Think of it like a pair of salad tongs.
- Material: PETG at 80–100% infill for strength. Add **TPU rubber pads** on the grip surfaces (print separately, glue on) for better plant grip.
- Cylinder 3 mounts on the back of the gripper and pushes/pulls a linkage that opens/closes the fingers.
- The gripper opening should be ~20–25 cm to grab a lechuguilla rosette.
- **Drainage:** Add slots/holes in the gripper fingers so water drains as the plant is lifted.

### 4.5 Hydraulic Hose Routing

- Use **6 mm (1/4") nylon hydraulic hose** — flexible, cheap, and rated for low-pressure systems.
- Each cylinder needs 2 hoses (extend + retract) = 6 hoses total running from the electronics box to the arm.
- Bundle hoses together with zip ties along the arm boom.
- At the rotation joint, leave enough hose slack for the arm's full rotation arc. Coil the excess and secure with a loose zip-tie loop.
- Use **push-to-connect (push-fit) fittings** on the cylinders and valves for easy assembly/disassembly.

### 4.6 Estimated Arm Cost Breakdown

| Component | Est. Cost (USD) |
|---|---|
| 12V hydraulic pump w/ reservoir | $50–80 |
| 3× solenoid directional valves | $60–120 |
| 3× micro hydraulic cylinders | $30–75 |
| Hydraulic hose + fittings (10m) | $20–30 |
| Hydraulic fluid (2L) | $5–10 |
| Arm structure (pipes, bearing, hardware) | $20–40 |
| 3D-printed gripper + mounts | $5–10 (filament) |
| **Subtotal** | **~$190–365** |

### 4.7 Alternative Budget Option

If the hydraulic solenoid valves are too expensive or hard to source, an alternative is to use **3× cheap high-torque servo motors** (e.g., MG996R, ~$4 each) to mechanically actuate manual spool valves. The servos stay inside the sealed box and push/pull the valve spools via short linkages. This is hacky but functional and saves ~$40–80.

---

## 5. Power System

### 5.1 Battery Selection

- **12V LiFePO4 battery, 20Ah–30Ah.** LiFePO4 is preferred over Li-ion because it's safer (no thermal runaway), more cycle-stable, and tolerates abuse better — critical in a wet, vibrating environment.
- A 12V 20Ah LiFePO4 battery provides 240Wh. Estimated system draw:
  - Propulsion motors (cruise): ~100W combined (half throttle)
  - Hydraulic pump (intermittent): ~100W (only runs during arm operation, maybe 20% duty cycle → ~20W average)
  - Camera + transmitter: ~10W
  - RC receiver + ESCs standby: ~5W
  - **Total average draw: ~135W**
  - **Runtime at 240Wh: ~1.8 hours.** Exceeds the 1-hour requirement with margin.
- A 12V 20Ah LiFePO4 costs ~$50–80 on Amazon/AliExpress.
- If budget allows, go 30Ah for ~2.5 hours runtime (~$80–120).

### 5.2 Charging

- Standard LiFePO4 charger (14.6V) — usually included with the battery or costs ~$10–15.
- Charge between missions. ~2–3 hours to full charge from depleted.

### 5.3 Power Distribution

- Battery sits inside the sealed electronics box.
- Use a **main power switch** (waterproof toggle switch mounted on the box lid) as the master on/off.
- Add a **simple fuse or circuit breaker** (20A–30A) on the positive line right after the battery for safety.
- All 12V loads (ESCs, pump, valves, camera, RC receiver) connect to a common 12V bus (terminal strip inside the box).
- If camera or RC receiver need 5V, use a small **12V-to-5V buck converter** (~$2).

---

## 6. Control, Video & Electronics

### 6.1 The Sealed Electronics Box

This is the "brain" of the robot. Every electronic component goes inside one sealed box.

- **The box:** A large **food-grade airtight container** — something like a Sistema or IKEA 365+ container (~10L capacity) with a snap-lock rubber-gasket lid. Cost: ~$5–10. Alternatively, a **waterproof ammo can** (surplus, ~$10–15) works great and looks rugged.
- Everything inside: battery, RC receiver, 2× ESCs, 3× hydraulic solenoid valves (or valve servos), hydraulic pump, 12V-to-5V converter, fuse, wiring terminal strip.
- **Cable pass-throughs:** Drill holes in the box wall and use **PG7/PG9 cable glands** (~$0.50 each) for every wire/hose that exits the box. These compress a rubber gasket around the cable for a watertight seal.
  - 2× glands for motor power cables (to propulsion motors)
  - 6× glands for hydraulic hoses (or bundle through larger PG13.5 glands)
  - 1× gland for camera power cable
  - 1× gland for RC antenna cable (or mount antenna externally through a gland)
  - 1× gland for main power switch wiring
- Apply **silicone sealant** around every gland as extra insurance.
- Add a few **silica gel packets** inside the box to absorb any residual moisture.

### 6.2 RC Transmitter & Receiver

- **Transmitter (operator holds):** A standard **2.4 GHz RC transmitter** with at least **6 channels** (we need 7 for full control, but most 6-channel radios have aux switches).
- **Recommendation:** FlySky FS-i6X (~$45–50). It has 10 channels, long range (~1.5 km stock), and is very popular/cheap. It supports mixing for tank steering.
- **Receiver:** FlySky FS-iA10B (included with the transmitter usually). Mounts inside the sealed box. Route the antenna wire out through a cable gland and tape/zip-tie it to a vertical stick on the deck for best reception.

**Channel assignment:**

| Channel | Control | Transmitter Input |
|---|---|---|
| CH1 | Left motor speed (fwd/rev) | Left stick vertical |
| CH2 | Right motor speed (fwd/rev) | Right stick vertical |
| CH3 | Arm lift / lower | Left stick horizontal (or aux knob) |
| CH4 | Arm rotate L/R | Right stick horizontal |
| CH5 | Gripper open / close | 2-position switch (SWA) |
| CH6 | Camera tilt (optional future) | Aux knob (VRA) |

### 6.3 Range Extension (to reach ~2 km)

- The stock FlySky system reaches ~1.5 km. To push to 2 km+:
  - Replace the stock receiver antenna with a **longer wire antenna** (31 mm for 2.4 GHz quarter-wave — the stock is usually fine, but proper positioning matters).
  - Mount the antenna **as high as possible** on the robot — top of a ~50 cm vertical PVC mast on the deck.
  - On the transmitter side, some FlySky models support an **external antenna mod** or you can get a transmitter module with a higher-gain antenna.
  - Alternatively, consider upgrading to **ExpressLRS (ELRS) at 900 MHz** — these modules cost ~$15–25 per pair and reach **10+ km** easily. They plug into the FlySky transmitter's module bay.

### 6.4 FPV Camera System

The operator needs a live video feed. We use a standard **analog FPV system** (proven, cheap, low-latency).

- **Camera:** A small FPV camera (e.g., RunCam Phoenix 2 or any 1200TVL mini cam), ~$15–25. Mount at the front of the deck on a short mast, facing forward and slightly down to see the water and the arm.
- **Video Transmitter (VTX):** A 5.8 GHz VTX with **600mW–1W output** for range. Something like an AKK X2 Ultimate (1W, ~$20). Mount inside the sealed box, route the antenna out through a cable gland to an external **cloverleaf/pagoda antenna** on the mast.
- **Receiver / Monitor (operator side):** A 5.8 GHz FPV receiver with a **7" LCD monitor** or FPV goggles. A cheap all-in-one monitor/receiver combo costs ~$40–60 and works well for this. Alternatively, FPV goggles like EV800D (~$50–60) with a built-in receiver.
- At 1W VTX power with a directional patch antenna on the receiver side, range of 2+ km is easily achievable with clear line-of-sight.

### 6.5 Electronics Cost Breakdown

| Component | Est. Cost (USD) |
|---|---|
| Sealed container (electronics box) | $5–15 |
| Cable glands (PG7/PG9, pack of 10) | $5–8 |
| RC Transmitter + Receiver (FlySky FS-i6X) | $45–55 |
| FPV Camera | $15–25 |
| Video Transmitter (1W 5.8 GHz) | $15–25 |
| FPV Monitor/Goggles (receiver side) | $40–60 |
| 12V LiFePO4 Battery (20Ah) | $50–80 |
| 2× ESCs (30A) | $16–24 |
| 2× 775 Brushless Motors | $10–20 |
| 12V-to-5V buck converter | $2–3 |
| Fuse holder + fuse | $2–3 |
| Wiring, connectors, terminal strips | $10–15 |
| Silica gel + silicone sealant | $5–8 |
| **Subtotal** | **~$220–340** |

---

## 7. 3D-Printed Parts List

All parts to be printed in **PETG** filament unless noted otherwise. PETG is mandatory for any part exposed to water or sun (UV-resistant, water-resistant, stronger than PLA).

| Part | Qty | Material | Notes |
|---|---|---|---|
| Propeller (weed-shedding design) | 2 (+ 2 spares) | PETG, 100% infill | ~80mm dia, swept-back blades |
| Propeller shroud/weed guard | 2 | PETG, 50% infill | Ring with cross-bar grid |
| Motor pod housing | 2 | PETG, 60% infill | Angled mount, lip seal groove |
| Pontoon saddle clamps | 4–6 | PETG, 80% infill | U-shaped, fits drum curvature |
| Arm gripper (2 fingers + frame) | 1 set | PETG, 100% infill | Wide fingers, linkage for cylinder |
| Gripper rubber pads | 2 | TPU (flexible) | Glue onto PETG fingers |
| Hydraulic hose clamps/guides | 8–10 | PETG, 50% infill | Snap-on clips for arm boom |
| Camera mount bracket | 1 | PETG, 60% infill | Adjustable angle, mast clamp |
| Antenna mast top bracket | 1 | PETG, 50% infill | Holds antenna + camera mast |
| Cable gland drill template | 1 | PLA (one-time use) | Jig for marking holes on the box |

**Estimated total filament: ~500g PETG + 50g TPU = ~$15–20 in materials.**

---

## 8. Full Bill of Materials — Summary

| Subsystem | Estimated Cost (USD) |
|---|---|
| Hull (drums, frame, deck, hardware) | $40–80 |
| Propulsion (motors, ESCs, propellers, mounts) | $40–65 |
| Hydraulic Arm (pump, valves, cylinders, hoses, structure, gripper) | $190–365 |
| Power (battery, charger, distribution) | $60–100 |
| Control & Video (RC, FPV, electronics box, wiring) | $130–200 |
| 3D-Printed Parts (filament) | $15–20 |
| Misc (fasteners, zip ties, silicone, epoxy, spare wire) | $20–30 |
| **TOTAL ESTIMATED** | **$495–860** |

**Target realistic budget: ~$600–700 USD** with careful sourcing and some recycled materials.

---

## 9. Assembly Sequence

Follow this order. Each phase should be tested independently before proceeding.

### Phase 1: Hull (Days 1–2)

1. Acquire 2× 200L plastic drums. Inspect for cracks. Clean thoroughly.
2. Seal all bungs with silicone. Optionally add spray foam to the bottom 5 cm interior.
3. Build the frame from PVC pipe or aluminum tubing. Cut, assemble, and attach cross-members.
4. Mount drums to frame using saddle clamps + U-bolts. Ensure tight and symmetric.
5. Attach deck surface (plywood/HDPE sheet) to the frame.
6. Mount cargo basket to deck (center-aft position).
7. **Test:** Place hull in water. Load 30 kg of dead weight. Verify stability, waterline, and that it floats level. Adjust pontoon spacing or ballast if needed.

### Phase 2: Propulsion (Days 3–4)

1. 3D-print motor pods, propellers, and weed guards.
2. Install motors into pods. Install shaft seals.
3. Mount pods to the stern of the frame (one per pontoon, submerged position).
4. Attach propellers and weed guards.
5. Wire ESCs to motors (run cables through frame tubes).
6. Temporarily connect ESCs to a receiver + battery on deck.
7. **Test:** In-water propulsion test. Verify forward, reverse, and differential steering. Test at full speed with 30 kg load. Check for weed clogging by dragging through vegetation.

### Phase 3: Electronics Box & RC (Days 5–6)

1. Drill cable gland holes in the sealed container. Install all cable glands.
2. Mount RC receiver, ESCs, buck converter, fuse, and terminal strip inside the box.
3. Wire everything per the wiring diagram (see Section 10).
4. Route motor cables through glands, connect to ESCs.
5. Mount antenna on external mast. Route coax through gland.
6. Install battery in box. Connect main switch.
7. Seal the box. Apply silicone to any suspicious gland.
8. **Test:** Full RC control test on water. Drive the robot around. Verify range by walking ~500 m away, then 1 km, then 2 km if possible. Check for signal dropouts.

### Phase 4: FPV Video (Day 7)

1. Mount FPV camera on front mast.
2. Mount VTX inside electronics box. Route antenna through gland.
3. Wire camera + VTX to 12V bus (through buck converter if camera is 5V).
4. Set up operator-side monitor/goggles.
5. **Test:** Drive the robot via FPV only (no line-of-sight). Verify image quality, latency, and range.

### Phase 5: Hydraulic Arm (Days 8–12)

1. Build the arm boom structure (cut pipe, weld/bolt the shoulder pivot and base rotation bearing).
2. Mount base to the front of the deck.
3. Install 3× hydraulic cylinders on the arm (lift, rotate, gripper).
4. 3D-print and assemble the gripper. Attach to arm end. Connect Cylinder 3.
5. Install hydraulic pump and solenoid valves inside the electronics box.
6. Run hydraulic hoses from valves out through cable glands to each cylinder.
7. Fill system with hydraulic fluid. Bleed air from all lines.
8. Wire solenoid valves to RC receiver channels (via relay board or directly if valves are low-current).
9. **Test (on land first):** Actuate each function independently — lift, lower, rotate left, rotate right, grip open, grip close. Verify smooth operation and no leaks.
10. **Test (on water):** Full arm test. Pick up a 3 kg object, hold it, rotate, place it in the cargo container. Repeat 10 times.

### Phase 6: Integration & Field Test (Days 13–14)

1. Full system test: drive to a target, grab an object, store it, return.
2. Test with actual lechuguilla plants if possible.
3. Endurance test: run continuously for 1+ hour. Monitor battery voltage.
4. Stress test: load cargo to full 30 kg, drive at max speed, verify stability.
5. Identify and fix any issues.

---

## 10. Wiring Diagram (Simplified)

```
                    ┌─────────────────────────────────────────────┐
                    │        SEALED ELECTRONICS BOX               │
                    │                                             │
  ┌───────────┐    │  ┌─────────┐    ┌──────────┐               │
  │  12V      │    │  │  FUSE   │───▶│ 12V BUS  │──────────┐    │
  │  LiFePO4  │────┤  │  25A    │    │ (terminal│    ┌─────┐│    │
  │  Battery  │    │  └─────────┘    │  strip)  │───▶│5V   ││    │
  └───────────┘    │                 └────┬─────┘    │BUCK ││    │
                    │                      │          └──┬──┘│    │
  [MAIN SWITCH]────┤                      │             │    │    │
  (waterproof,     │              ┌───────┼─────────────┤    │    │
   on box lid)     │              │       │             │    │    │
                    │          ┌──┴──┐ ┌──┴──┐  ┌──────┴┐   │    │
                    │          │ESC  │ │ESC  │  │RC RX  │   │    │
                    │          │LEFT │ │RIGHT│  │FlySky │   │    │
                    │          └──┬──┘ └──┬──┘  └──┬────┘   │    │
                    │             │       │     PWM signals  │    │
                    │    ┌────────┼───────┼────to ESCs &     │    │
                    │    │        │       │    solenoids     │    │
                    │  ┌─┴──────────────────┐               │    │
                    │  │  SOLENOID VALVES   │               │    │
                    │  │  V1(lift) V2(rot)  │               │    │
                    │  │  V3(grip)          │               │    │
                    │  └─┬──────────────────┘               │    │
                    │    │                                   │    │
                    │  ┌─┴──────────┐    ┌───────┐          │    │
                    │  │ HYDRAULIC  │    │ FPV   │          │    │
                    │  │ PUMP 12V   │    │ VTX   │◀─────5V─┘    │
                    │  └────────────┘    └───┬───┘               │
                    │                        │                   │
                    └─────────┼──────┼───────┼──────────────────-┘
                              │      │       │
              (cable glands)  │      │       │
                              ▼      ▼       ▼
                          ┌──────┐ ┌──────┐ ┌──────┐
                          │MOTOR │ │MOTOR │ │FPV   │
                          │LEFT  │ │RIGHT │ │CAM   │
                          └──────┘ └──────┘ └──────┘

     6× Hydraulic hoses also exit through cable glands
     to the 3 cylinders on the arm.
```

---

## 11. Key Design Risks & Mitigations

| Risk | Impact | Mitigation |
|---|---|---|
| Water ingress into electronics box | Catastrophic (shorts) | Double-seal all glands with silicone. Pressure-test box before first deployment (seal it, submerge in bathtub, check for bubbles). Add silica gel inside. |
| Propellers clogged with weeds | Robot stranded | Weed guards with grid. Swept-blade propeller design. Operator can reverse thrust to clear minor clogs. Carry a spare set of propellers. |
| Hydraulic fluid leak | Arm stops working + environmental contamination | Use **biodegradable hydraulic fluid** (vegetable-based, available at industrial suppliers). Tighten all fittings with thread sealant tape. Carry a small toolkit for field repairs. |
| Loss of RC signal at range | Robot drifts uncontrolled | Set ESC failsafe to "throttle off" (motors stop on signal loss — robot just drifts and can be retrieved by boat). Consider ELRS upgrade for 10 km+ range. |
| Battery dies mid-mission | Robot stranded | Monitor battery voltage via a small **voltage buzzer** (~$1) that beeps when voltage drops below threshold. Operator returns to shore with 20% battery remaining. |
| Arm not strong enough to pull plants | Cannot harvest | The hydraulic system provides more than enough force for 1–3 kg plants. If roots are stuck, operator can use propulsion to pull back while arm grips. |

---

## 12. Environmental Compliance Checklist

- **No fuel / no combustion:** Electric-only propulsion. Zero emissions.
- **Biodegradable hydraulic fluid:** Mandatory. Use vegetable-based or similar eco-rated fluid.
- **No toxic materials in water:** PETG and HDPE are food-safe, non-toxic plastics. No anti-fouling paints.
- **Recycled materials:** Drums, crates, and scrap metal reused. Minimal new material purchase.
- **Noise:** Electric motors are near-silent. Minimal disturbance to wildlife.
- **Spill plan:** Carry absorbent pads on the support boat/shore. If hydraulic leak occurs, retrieve robot immediately.

---

## 13. Maintenance Schedule

| Task | Frequency |
|---|---|
| Visual inspection of hull, frame, and mounts | Before every mission |
| Check electronics box seal integrity | Before every mission |
| Inspect propellers for damage or weed buildup | Before and after every mission |
| Check hydraulic hose fittings for leaks | Before every mission |
| Charge battery | After every mission |
| Grease rotation bearing on arm base | Weekly |
| Replace silica gel packets in electronics box | Weekly (or when saturated) |
| Full hydraulic fluid level check | Weekly |
| Inspect and clean FPV camera lens | Weekly |
| Full system teardown and inspection | Monthly |
| Replace propellers (3D-print new ones) | As needed (expect every 2–4 weeks) |

---

## 14. Future V2 Upgrade Path (Out of Scope for V1)

These are not to be implemented now, but the V1 design should not make them impossible:

- GPS module + return-to-home failsafe
- Autonomous waypoint navigation
- Computer vision for automatic plant detection
- Solar panel trickle charger for extended missions
- Sonar for shallow-water depth detection
- Second camera (rear/arm-mounted) for better gripper visibility
- Telemetry overlay on FPV feed (battery voltage, GPS coordinates)

---

## 15. Tools Required for Assembly

Most of these are common workshop tools:

- Drill + drill bits (for cable gland holes, frame assembly)
- Screwdriver set (Phillips + flat)
- Wrench set (for U-bolts, pipe fittings)
- Soldering iron + solder + heat shrink (for wiring)
- Wire strippers + crimper
- Zip ties (lots of them — buy a 500-pack)
- Silicone sealant (marine grade)
- Thread sealant tape (PTFE / Teflon tape, for hydraulic fittings)
- 3D printer (or access to a printing service)
- Hacksaw or pipe cutter (for PVC/aluminum frame)
- Multimeter (for testing connections)
- Hot glue gun (for cable management and quick fixes)

---

*End of Implementation Plan — Lancha Robot V1*
