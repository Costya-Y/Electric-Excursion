# Electric Excursion

Exploring the possibility and viability of converting a Ford Excursion into a practical AWD range-extended EV: battery-electric for short trips and transient power, with a compact generator for long-range energy.

The design goal is **not** to maximize peak power. It is to keep the motors, generator, and inverters relatively small while retaining good acceleration, towing/off-road capability, useful regenerative braking, and a short-duration top-speed capability around 120 mph.

> **Status:** conceptual engineering / design exploration. All performance figures below are estimates to be validated against selected motors, battery cells, gearing, vehicle mass, aerodynamic measurements, thermal limits, and component efficiency maps.

## 1. Real-world duty cycle

The powertrain should be optimized around the speeds the truck will actually see:

- **55–65 mph:** majority of driving.
- **45 mph and below:** much of the remaining driving.
- **75–80 mph:** occasional highway segments.
- **90 mph:** rare.
- **120 mph:** exceptional, short-duration capability only; it is not a generator-sizing condition.

This changes the range-extender target substantially. The generator should cover **long-term average road energy**, while the battery handles acceleration, hills, towing transients, AWD demand, and brief high-speed operation.

## 2. Revised architecture

### Rear axle — primary propulsion

- Approx. **130–160 kW peak** traction motor.
- Powered from the HV battery/DC bus and therefore indirectly from both battery and generator.
- **3-speed constant-mesh electrically synchronized gearbox** preferred.
- Always available and optimized for ordinary propulsion and highway efficiency.

Conceptual total motor-to-wheel ratios:

| Gear | Approx. ratio | Primary purpose |
|---|---:|---|
| 1st / Low | 14–16:1 | off-road, towing launch, steep grades, low-speed regen |
| 2nd / Drive | 8–9:1 | city, acceleration, normal towing |
| 3rd / Highway | 4.5–5.5:1 | efficient 55–80 mph cruise and short high-speed operation |

The ratios are placeholders until a specific motor efficiency map, maximum RPM, and tire diameter are selected.

### Front axle — battery-only assist axle

- Approx. **80–100 kW peak** motor.
- Logically treated as a **battery-only boost/traction/regen axle**.
- Mechanical disconnect for long-range/highway operation.
- Likely fixed ratio or compact 2-speed rather than duplicating the rear 3-speed gearbox.
- Reconnected for launch, low-traction conditions, off-road use, towing assistance, strong acceleration, and stronger regenerative braking.

The front axle should not reconnect merely because the steering wheel moves. Re-engagement should be based on requested torque, steering angle, yaw/lateral acceleration, wheel slip, road conditions, and stability-control demand.

### Range extender

- Target: **~40–50 kW electrical continuous**.
- Current nominal design point: **~45 kW electrical**.
- Likely requires roughly **50–55 kW mechanical** at the generator shaft depending on generator/inverter efficiency.
- Engine should be sized so normal generator output falls near a favorable BSFC/load region rather than running a much larger automotive engine at low load.

The generator is primarily assigned to:

1. rear propulsion demand;
2. maintaining battery state of charge;
3. restoring energy after acceleration, towing climbs, or high-speed segments.

It does **not** need to match combined traction-motor peak power.

### Battery

- Approx. **80–100 kWh usable-class pack** is currently preferred.
- Its large capacity is useful not only for EV range but as a high-power buffer.
- Long-range generator mode should intentionally maintain substantial charge and regen headroom; a preliminary target is around **50–60% SOC**, subject to battery chemistry.
- Battery supplies transient differences between generator output and traction demand.

An optional high-power secondary battery or supercapacitor module should remain an interface/design option, but should only be added if testing shows that the main pack's short-duration charge-power limit materially clips useful regen.

## 3. Operating modes

### EV mode

Generator off. Battery powers rear propulsion; front axle connects only when useful.

### Range mode

- Generator runs near an efficient operating point as required.
- Rear axle is the primary drive axle.
- Front axle is disconnected during steady highway operation.
- Generator surplus restores/maintains target SOC.
- Battery covers temporary power deficits at higher speeds, on grades, and during acceleration.

### AWD / Tow / Off-road mode

- Rear motor remains primary.
- Front axle is connected and receives battery power.
- Generator continues supporting rear propulsion and/or SOC.
- 1st gear is a real low/crawl/towing ratio rather than simply another closely spaced road gear.

### Maximum Performance / "Mad Max" endurance mode

- Rear motor active.
- Front motor connected and active.
- Battery discharge limits relaxed within safe thermal/electrical limits.
- Generator kept at high/maximum useful output.
- Cooling system operated aggressively.

This mode is intended for unusual sustained high-load use such as track-style operation, long grades, sand, or repeated acceleration — not normal driving.

## 4. Why 3 gears instead of 4 or a CVT

Three gears currently look like the best balance:

- **1st:** genuine low/off-road/towing gear.
- **2nd:** normal drive/acceleration gear.
- **3rd:** highway/high-speed efficiency gear.

EV motors have a much wider useful speed range than combustion engines, so a 4th ratio is likely to provide only a small efficiency improvement while adding another engagement state, gear path, bearings, mass, and failure modes.

A belt/chain CVT would theoretically keep the motor closer to an ideal efficiency point, but towing, shock loads, bidirectional regen torque, vehicle mass, and off-road use make it unattractive for a reliability-focused build. A constant-mesh dog-clutch gearbox synchronized by motor speed control is preferred.

## 5. Highway power estimate

### Baseline assumptions

These estimates use a deliberately conservative conceptual model:

- Vehicle mass: **~3,500 kg / 7,700 lb**.
- Tire diameter: **~33 in**.
- Effective CdA: **~1.45 m²**.
- Rolling-resistance coefficient: **~0.012**.
- Air density: **1.225 kg/m³**.
- Motor/inverter/reduction path efficiency during cruise: **~91% combined**.
- Accessories/cooling allowance: **~2 kW**.
- Level road, still air.

Actual numbers can differ materially with ride height, tires, roof accessories, wind, temperature, trailer, road grade, and final mass.

| Vehicle speed | Estimated electrical road demand |
|---:|---:|
| 45 mph | ~19 kW |
| 55 mph | ~28 kW |
| 60 mph | ~33 kW |
| 65 mph | ~39 kW |
| 75 mph | ~54 kW |
| 80 mph | ~63 kW |
| 90 mph | ~84 kW |
| 120 mph | ~177 kW |

### Implication for a 45 kW generator

- **45–60 mph:** significant surplus is available for SOC restoration.
- **~65 mph:** close to charge-neutral with modest reserve.
- **75–80 mph:** battery supplies roughly 10–20 kW of temporary deficit under baseline conditions.
- **90 mph:** strongly battery-assisted and not intended as a sustained generator-only operating point.
- **120 mph:** traction-battery performance condition; generator sizing is almost irrelevant.

Example: if 80 mph requires ~63 kW, a 45 kW generator leaves an ~18 kW battery deficit. Thirty minutes at that condition consumes only about **9 kWh**, which can be restored later when speed falls back into the normal 55–65 mph range.

## 6. Projected performance

### Combined traction power

Current conceptual range:

- Rear: **130–160 kW peak**.
- Front: **80–100 kW peak**.
- Combined: roughly **210–260 kW peak**.

This is deliberately smaller than using two large fixed-ratio EV drive units. The gearbox trades motor RPM for wheel torque so the motors can be smaller without sacrificing launch/towing capability.

### 0–60 mph

For a ~3,500 kg truck with ~210–260 kW combined peak power, appropriate low gearing, and AWD traction, a reasonable conceptual target is:

- **~6.5–8.0 s 0–60 mph** unloaded on good pavement.
- Heavy payload, trailer, thermal limits, conservative current limits, or traction constraints will increase this substantially.

This is not a simulation result; it is an engineering target range. Final acceleration must be calculated from actual motor torque-vs-RPM maps, gear ratios, inverter/battery current limits, tire traction, shift timing, and vehicle mass.

### Top speed

A **~120 mph short-duration top speed appears feasible** if:

- combined traction power is near the upper part of the proposed range;
- the rear high gear places the rear motor below its RPM/field-weakening limit;
- battery can supply ~180–220+ kW electrical for the event;
- tires, driveshafts/half-shafts, wheel bearings, suspension, brakes, and vehicle stability are explicitly rated and validated for that speed.

The estimated level-road electrical demand at 120 mph is already around **~177 kW** before adding strong acceleration margin, wind, grade, or conservative thermal reserve. Therefore 120 mph should remain a brief capability, not a cruise requirement.

### 90 mph

Estimated road demand is approximately **~84 kW** in the baseline model. The rear motor can handle this by itself; the battery supplies the portion above generator output. Front engagement should be based on acceleration/traction demand rather than speed alone.

## 7. Towing and grade behavior

The generator should **not** be sized to sustain worst-case towing climbs indefinitely. Instead:

- generator supplies ~45 kW continuously when useful;
- battery supplies the temporary difference;
- front motor joins for traction and additional wheel power;
- gearbox downshifts to keep motor torque/current and temperature under control;
- SOC is restored on easier terrain afterward.

This permits a substantially smaller genset while retaining high transient towing capability.

For long-duration maximum-GCWR mountain towing, however, the limiting factor becomes sustained thermal/power balance. That use case may justify increasing generator output toward **55–65 kW** or accepting gradual SOC depletion on long climbs. It should be treated as a separate requirement rather than silently oversizing the generator for all trips.

## 8. Regenerative braking strategy

### Principle

Do **not** simply select the lowest possible gear during regen. The controller should choose the ratio that gives the best combination of:

- requested braking power;
- motor/generator efficiency;
- motor RPM and back-EMF limits;
- inverter current/voltage limits;
- tire traction and stability;
- battery charge-power acceptance;
- available SOC headroom.

At high speed, a tall gear avoids excessive motor RPM. As speed falls, the controller can downshift to keep the motor in an effective generating region.

### Front axle during regen

The front drivetrain may be disconnected during steady highway propulsion but should be able to synchronize and reconnect for stronger braking. This is useful because dynamic weight transfer increases front-tire normal load during braking.

Typical sequence:

1. light deceleration: rear regen only;
2. stronger requested deceleration: synchronize and reconnect front motor;
3. distribute regen according to traction, motor efficiency, and battery acceptance;
4. downshift one or both motors as vehicle speed falls;
5. friction brakes provide the remaining braking power and low-speed stop capability.

### Recoverable kinetic energy

For the ~3,500 kg baseline vehicle, translational kinetic energy is approximately:

| Initial speed | Vehicle kinetic energy | ~65–75% potentially returned to pack* |
|---:|---:|---:|
| 60 mph | ~0.35 kWh | ~0.23–0.26 kWh |
| 80 mph | ~0.62 kWh | ~0.40–0.47 kWh |
| 120 mph | ~1.40 kWh | ~0.91–1.05 kWh |

\*Illustrative overall recovery fraction only. Actual recovery depends on braking rate, SOC, pack temperature, motor/inverter efficiency, tire traction, gearbox losses, and how much friction braking is required.

The important design conclusion is that hard regen is mainly a **power-acceptance problem**, not an energy-capacity problem. Even a 120-to-0 mph event contains only about 1.4 kWh of translational kinetic energy, but absorbing much of it in a few seconds can require several hundred kilowatts of instantaneous charge power.

### Generator behavior during regen

The combustion engine does not need to stop every time regen begins.

Preferred behavior:

- keep the engine warm/spinning when range mode requires it;
- rapidly unload the electrical generator when regen consumes available battery charge power;
- restore generator load after the braking event.

An optional supercapacitor/high-power battery buffer should only be added if measurements show that useful vehicle regen is frequently clipped by the main battery's charge-power limit.

## 9. SOC management

A preliminary long-range strategy is to maintain the battery near the middle of its usable SOC window rather than keeping it nearly full.

Conceptual policy:

- target in range mode: **~50–60% SOC**;
- upper region leaves room for regen;
- lower region preserves AWD/boost/towing reserve;
- generator increases average output/duty cycle as SOC approaches the lower control boundary;
- high-speed and climbing deficits are intentionally repaid later at lower road load.

Exact thresholds depend on battery chemistry, usable SOC limits, temperature, aging strategy, and desired emergency reserve.

## 10. Updated design summary

```text
                         FUEL
                           |
                    ~45 kW GENSET
                           |
                           v
                         HV BUS
                    /       |       \
                   /        |        \
          80–100 kWh     REAR        FRONT
            battery       motor        motor
                         130–160 kW   80–100 kW
                              |          |
                           3-speed    fixed/2-speed
                              |          |
                              |       disconnect
                              |          |
                            rear        front
                            axle        axle
```

Operating philosophy:

- **Rear axle moves the truck most of the time.**
- **Generator covers average long-range energy, not peak traction demand.**
- **Battery supplies dynamics:** acceleration, hills, towing transients, high speed, and AWD.
- **Front axle is an electric booster/traction/regen axle and is disconnected when unnecessary.**
- **Low gearing provides towing/off-road wheel torque without requiring enormous motors.**
- **Regen uses both axles and gear selection when useful, but remains limited by stability and battery charge power.**
- **120 mph is a rare short-duration engineering capability, not a design cruise point.**

## 11. Next engineering work

The next iteration should replace the placeholder motor/gear figures with actual candidate components and run a numerical vehicle model containing:

1. measured/estimated Excursion CdA at normal and lowered highway ride height;
2. candidate front/rear motor torque, power, RPM, and efficiency maps;
3. candidate gearbox ratios and gear-mesh efficiencies;
4. battery discharge/regen power vs SOC and temperature;
5. generator engine BSFC map and generator efficiency;
6. 0–60 and 40–80 mph acceleration simulation;
7. towing/grade thermal simulation;
8. SOC evolution over a realistic mixed-speed trip;
9. regen power and energy capture for representative braking events;
10. cooling and fail-safe analysis.

The objective is to find the smallest practical generator and traction motors that satisfy the **real duty cycle**, rather than sizing every component around rare peak conditions.
