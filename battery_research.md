# Battery & Power Research

## Battery Spec

- **Type:** 12V LiFePO4, 20Ah (240Wh)
- **Cost:** ~$50–80 (20Ah) | ~$80–120 (30Ah upgrade)
- **Safe usable capacity:** ~80% (192Wh) — stop at 20% to preserve battery health

## Power Draw Estimates

| Subsystem | Peak | Avg Draw |
|---|---|---|
| 2x 775 motors (propulsion) | ~300W | ~100W (half throttle cruise) |
| Hydraulic pump | ~100W | ~20W (20% duty cycle) |
| FPV camera + VTX | ~5W | ~5W |
| RC receiver + valves | ~10W | ~10W |
| **Total** | **~415W** | **~135W** |

## Runtime Estimates (20Ah, with 20% reserve)

| Scenario | Runtime |
|---|---|
| Light cruising, few grabs | ~2 hours |
| Typical mixed mission | ~1.5 hours |
| Heavy work (constant throttle + arm) | ~40–45 min |

30Ah battery adds ~50% to all runtimes.

## Charge Times (0→100%, 20Ah)

| Charger | Time | Cost |
|---|---|---|
| 5A (standard) | ~4–4.5 hrs | Often bundled |
| 10A | ~2 hrs | ~$15–25 |
| 20A | ~1 hr | ~$30–50 |

Real-world recharge from 20% is ~20% faster than listed above.

## Solar Panels — Not Recommended for V1

- A 100W panel (largest that fits the deck) produces ~60–70W real-world — only ~15% of the active power draw.
- Adds $75–130 (panel + MPPT controller + mounting) for minimal runtime gain.
- Eats deck space needed for cargo container, arm, and electronics.
- Raises center of gravity, hurting stability.
- Adds wiring complexity and failure points.
- **Better alternative:** a second battery ($50–80) doubles runtime with zero added complexity.
- Solar makes sense only if a future V2 does long-duration autonomous patrols at low power.
