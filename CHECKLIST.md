# Lancha Robot V1 — Project Checklist

**Status:** Not started  
**Last updated:** 2026-04-09

---

## Phase 1: Hull & Flotation (Days 1-2)

- [ ] Acquire and inspect 2x 200L plastic drums
- [ ] Seal all bungs with silicone (optional: spray foam bottom 5cm)
- [ ] Build frame (PVC pipe or aluminum tubing, ~1.5m x 1.2m)
- [ ] Mount drums to frame with saddle clamps + U-bolts
- [ ] Attach deck surface (plywood or HDPE sheet)
- [ ] Mount cargo basket (center-aft)
- [ ] Attach weed deflectors (V-shaped PVC pipes on pontoon fronts)
- [ ] **TEST:** Float test with 30kg dead weight — check stability and waterline

## Phase 2: Propulsion (Days 3-4)

- [ ] 3D-print motor pods, propellers, and weed guards (PETG)
- [ ] Install motors into pods with shaft seals
- [ ] Mount pods to stern of frame (one per pontoon)
- [ ] Attach propellers and weed guards
- [ ] Wire ESCs to motors (route cables through frame tubes)
- [ ] **TEST:** In-water propulsion — forward, reverse, differential steering, weed clog test

## Phase 3: Electronics Box & RC (Days 5-6)

- [ ] Drill and install cable glands on sealed container
- [ ] Mount RC receiver, ESCs, buck converter, fuse, terminal strip inside box
- [ ] Wire all internal components per wiring diagram
- [ ] Route motor cables through glands, connect to ESCs
- [ ] Mount antenna on external mast, route through gland
- [ ] Install battery, connect main power switch
- [ ] Seal box, apply silicone to all glands, add silica gel packets
- [ ] **TEST:** Full RC control on water — verify range at 500m, 1km, 2km

## Phase 4: FPV Video (Day 7)

- [ ] Mount FPV camera on front mast
- [ ] Mount VTX inside electronics box, route antenna through gland
- [ ] Wire camera + VTX to 12V bus
- [ ] Set up operator-side monitor/goggles
- [ ] **TEST:** Drive robot via FPV only — check image quality, latency, range

## Phase 5: Hydraulic Arm (Days 8-12)

- [ ] Build arm boom structure (pipe, shoulder pivot, base rotation bearing)
- [ ] Mount arm base to front of deck
- [ ] Install 3x hydraulic cylinders (lift, rotate, gripper)
- [ ] 3D-print and assemble gripper (PETG + TPU pads)
- [ ] Attach gripper to arm end, connect gripper cylinder
- [ ] Install hydraulic pump and solenoid valves inside electronics box
- [ ] Run hydraulic hoses from valves through cable glands to cylinders
- [ ] Fill system with biodegradable hydraulic fluid, bleed air from lines
- [ ] Wire solenoid valves to RC receiver channels
- [ ] **TEST (land):** Actuate each function independently — lift, lower, rotate L/R, grip open/close
- [ ] **TEST (water):** Pick up 3kg object, rotate, place in cargo container (repeat 10x)

## Phase 6: Integration & Field Test (Days 13-14)

- [ ] Full mission test: drive, grab object, store, return
- [ ] Test with actual lechuguilla plants
- [ ] Endurance test: 1+ hour continuous operation, monitor battery
- [ ] Stress test: full 30kg cargo at max speed, verify stability
- [ ] Identify and fix issues

---

## Procurement

- [ ] Hull: drums, frame material, deck, hardware, cargo basket
- [ ] Propulsion: 2x 775 motors, 2x 30A ESCs
- [ ] Hydraulic: pump, 3x solenoid valves, 3x cylinders, hoses, fittings, fluid
- [ ] Power: 12V LiFePO4 battery (20-30Ah), charger
- [ ] Control: FlySky FS-i6X transmitter + receiver
- [ ] Video: FPV camera, 1W 5.8GHz VTX, monitor/goggles
- [ ] Electronics: sealed container, cable glands, buck converter, fuse, wiring
- [ ] 3D printing: PETG filament (~500g), TPU filament (~50g)
- [ ] Misc: fasteners, zip ties, silicone sealant, PTFE tape, silica gel

---

**Target budget:** $600-700 USD
