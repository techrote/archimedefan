# Design rationale and current reasoning — 2026-10-03

This note records the reasoning and conclusions that led to reviving the `archimedefan` project and the current proposed geometry experiments.

It intentionally distinguishes **observed prototype behaviour** from **engineering hypotheses** that still need measurement.

## 1. Cooling context that revived the project

The discussion began from a practical cooling problem.

A 24 V industrial fan capable of nearly 1 A at rated voltage had been run from a 12 V Molex supply. Even at half rated voltage it remained obnoxiously loud. The objection was not simply motor noise: high static pressure and strong local turbulence from a small, thick, high-pressure fan remain acoustically aggressive even when slowed down.

Several undervolting approaches were considered:

- The classic PC "7 V trick" (+12 V as supply and +5 V as the return) was rejected for this application. It can inject current into the PSU's +5 V rail unless there is always enough 5 V load to consume the injected current.
- Adding a known 5 V load with equal or greater **actual instantaneous** current draw can prevent steady-state reverse current, but startup, shutdown, fan failure and nonlinear BLDC behaviour make this a fragile way to engineer the system.
- Two similar 12 V fans in series across +12 V and ground is electrically cleaner and gives roughly 6 V each, provided both fans start reliably and the BLDC electronics share the voltage tolerably.
- None of these hacks solves the basic acoustic problem of small high-pressure industrial fans.

Decision: keep the industrial fans for extreme/special situations rather than design the normal cooling system around them.

That led back to the existing 160 × 60 mm custom fan, whose large diameter should permit useful airflow at much lower RPM and tip speed.

## 2. Existing prototype

Known prototype properties from the discussion:

- approximately **160 mm rotor diameter**;
- approximately **60 mm depth**;
- currently printed in **PETG**;
- 12 V drive;
- demonstrated operating range approximately **0.3–10 A**, i.e. about **3.6–120 W** electrical input;
- broad, strongly swept pumping surfaces rather than conventional narrow axial-fan blades;
- continuous cylindrical outer band which is part of the rotor and rotates with the blades;
- stationary surrounding housing/shroud outside that rotating band;
- airflow deliberately passes strongly through/around the motor;
- the vital printed attachment region is deliberately air-gapped from the motor rotor;
- an inlet guard has already been made and mounts to the shroud holes.

An early high-power test produced enough thrust for the assembly to lift itself a few inches from the desk before power was cut. That is useful evidence that the design is not merely a large PC fan: at the upper end it behaves more like a small ducted propulsor and should be treated mechanically as such.

## 3. What is unusual about the rotor

The user's description is the most useful conceptual model:

> a cross between a slice of an Archimedean screw cloned around the centre axis and a ducted fan, except the duct also spins

The key feature is that there are **no conventional free blade tips**.

Each main blade joins the continuous outer cylindrical rotor shell. Therefore:

- blade-to-rotating-shell clearance is effectively zero;
- the only radial running clearance is between the rotating outer shell and stationary housing;
- a conventional axial fan's direct pressure-side-to-suction-side leakage around each individual free tip is largely removed as a mechanism;
- the outer band also mechanically ties all blade ends together.

A more conventional vocabulary would be **banded rotor**, **shrouded rotor**, or **co-rotating outer band**, although "pseudo-toroidal" remains a useful descriptive project term.

## 4. Aerodynamic reasoning

### 4.1 Tip leakage and vortices

Conventional axial rotors have a finite gap between blade tips and a stationary shroud. Pressure can leak through that gap and roll into tip vortices.

Here, each blade terminates into the co-rotating outer band. The aerodynamic boundary adjacent to the blade tip moves with the blade, so there is no comparable blade-tip gap.

Hypothesis:

- lower tip leakage than an otherwise similar free-tip axial rotor;
- weaker conventional blade-tip vortices;
- potentially better pressure generation and efficiency, especially under restriction.

This should not be stated as established performance until measured. There can still be leakage and shear in the annular gap between rotating outer cylinder and stationary housing.

### 4.2 Large passages and possible slip/recirculation

The present design has very large open passages between its main pumping surfaces. That is attractive for low blockage and free-air flow, but wide passages may allow some flow to recirculate, slip, or fail to follow the intended helical/axial path.

This observation motivated the inward-reaching splitter-vane idea.

### 4.3 Low-RPM / large-area advantage

At a given useful volumetric flow, a 160 mm rotor can operate at much lower tip speed than an 80 mm pressure fan.

That is the core acoustic opportunity:

- normal mode: large area, low RPM, modest electrical power;
- restricted-load mode: moderate RPM/power with more pressure reserve;
- extreme mode: substantial available motor power when noise is acceptable.

The desirable design target is therefore not maximum RPM. It is a broad efficient operating envelope.

## 5. Structural reasoning

The rotating outer band changes the structure as well as the aerodynamics.

Potential benefits:

- each blade is supported at both inner and outer ends rather than behaving purely as a cantilever;
- the band constrains relative blade-end motion;
- reduced individual blade flutter/flex is plausible;
- circumferential continuity may help preserve geometry and contribute to the observed lack of obvious balance problems.

However, putting material at the largest radius increases the consequence of any eccentricity, so smooth operation is evidence that the printed band is reasonably concentric/uniform rather than proof that outer mass is intrinsically self-balancing.

The outer ring also becomes a critical structural member. Important load paths include:

1. motor/hub interface;
2. hub-to-main-blade junctions;
3. main-blade-to-outer-band junctions;
4. circumferential/hoop stress in the outer band.

A crack in the band could therefore be more consequential than a local cosmetic defect.

## 6. Material and safety conclusions

The present PETG part is suitable as an experimental prototype, but high-power operation deserves propulsion-style rather than ordinary-PC-fan safety thinking.

The discussion considered CF/GF PETG or nylon for a later "production" rotor. The conclusion was not simply "filled is stronger":

- fibre-filled materials can provide higher stiffness and dimensional stability;
- but they may be more notch-sensitive;
- inter-layer toughness can be worse depending on material/process;
- blade-root/hub applications care about toughness, fatigue resistance and layer adhesion as much as stiffness.

Potential later approaches include a metal hub/insert or mechanical capture at the motor interface rather than relying only on printed polymer.

Safety context:

- the fan has already generated enough thrust to move/lift itself;
- its operating envelope reaches about 120 W electrical input;
- an inlet guard exists;
- guarding should be considered both as finger protection and as possible fragment containment at higher speeds;
- high-power testing should use secure mounting and remote power interruption rather than relying on hand access near the rotor.

## 7. Proposed inward-reaching splitter vanes

The sketched idea is interpreted as **short blades attached to the outer rotating shell and projecting inward into each broad passage**.

They should be thought of first as **splitter / guide vanes**, not full additional main blades.

### Working hypothesis

A modest splitter may:

- increase effective solidity near the outer radius;
- make better use of the region with highest tangential speed;
- reduce internal slip/recirculation within each very broad passage;
- encourage the flow to follow the intended sweep/helix;
- improve static pressure against filters, heatsinks, ducts and other restriction.

### Risks

An oversized or badly aligned splitter may:

- consume too much open flow area;
- reduce free-air flow;
- add drag and electrical load;
- add turbulence and tonal/broadband noise;
- operate at excessive incidence and separate;
- partially choke the passage instead of guiding it.

Therefore the splitter experiment should be conservative.

### First geometry worth printing

Initial recommendation:

- one splitter per major passage;
- attached to the co-rotating outer shell;
- project inward roughly **15–25% of passage width**;
- follow the **local curvature/sweep/helix direction** of the existing main surfaces rather than being a simple radial paddle;
- rounded leading edge;
- generous fillet into the outer shell;
- positioned in the outer part of the passage where the open channel is widest / most weakly guided.

This is a starting experiment, not a final aerodynamic prescription.

## 8. Experimental matrix

The most useful next comparison is a controlled A/B/C set rather than trying to infer the result from appearance alone.

### Rotor A — baseline

Current geometry, unchanged.

### Rotor B — small splitters

One short outer-band splitter per major passage, approximately 15–25% inward projection.

### Rotor C — larger splitters

Same concept, larger projection/solidity, primarily to reveal the trend and determine where blockage/drag begins to dominate.

Keep other geometry as constant as practical.

Measure or record, ideally at several operating points:

- supply voltage;
- current / electrical input power;
- RPM;
- free-air thrust and/or volumetric airflow;
- static pressure or pressure through a repeatable restriction;
- temperature of motor/windings where practical;
- subjective and preferably measured acoustic level/spectrum;
- startup behaviour;
- vibration/balance behaviour.

A representative restriction such as a repeatable filter, radiator/heatsink, or calibrated duct/orifice will likely be more informative than free-air flow alone because the splitter hypothesis is primarily about flow guidance and pressure capability.

## 9. Control direction

No controller architecture was committed to, but the wide demonstrated power range suggests a useful eventual control strategy:

- reliable startup kick;
- low-power quiet operating region;
- temperature/RPM/current-controlled normal operation;
- explicit current/power ceiling;
- optional high-output override for short extreme-cooling tests.

A large rotor that can loaf at a few watts yet has much higher reserve is more interesting than tuning the design only for its maximum 10 A operating point.

## 10. Current conclusions and decisions

1. **Keep the project alive.** The co-rotating outer band is mechanically and aerodynamically interesting enough to justify further experiments.
2. **Use the custom 160 × 60 mm rotor as the preferred route to quieter high-capacity cooling**, rather than trying to make small industrial pressure fans pleasant.
3. **Treat the outer band as a defining feature**, not merely a shroud: it removes conventional free blade tips and forms part of both the aerodynamic and structural design.
4. **Do not assume the apparent benefits are established.** Tip leakage, pressure performance, noise and efficiency need measurement.
5. **Test short outer-band splitter vanes next.** Start conservative and compare against the unchanged rotor.
6. **Optimise for a broad operating envelope**, especially quiet low-power airflow plus useful pressure under restriction, rather than maximum electrical input alone.
7. **Keep safety/containment proportional to the demonstrated thrust and stored mechanical energy**, particularly for high-power runs.

## 11. Open questions

- How much conventional tip-loss reduction does the co-rotating band actually deliver?
- What is the optimum stationary-housing-to-rotating-band annular clearance?
- Does the outer band incur meaningful skin-friction / windage loss at high RPM?
- What splitter depth and incidence maximises restricted-flow pressure before blockage/noise dominates?
- Does the splitter geometry improve efficiency, or merely trade more electrical input for more pressure?
- Where are the dominant acoustic sources: motor, broad blade loading, annular-gap shear, passage turbulence, or housing interaction?
- How does efficiency scale across the very wide 3.6–120 W operating range?
- Which rotor material and print orientation give the best combination of stiffness, toughness, fatigue resistance and containment margin?
- Would a mechanically retained metal hub materially improve high-speed safety and repeatability?
