# archimedefan

Toroidal co-rotating propulsive ducted fan design experimentation.

This repository records development of a large, low-speed-to-high-power axial/pseudo-toroidal fan concept whose **outer cylindrical band rotates with the blades**. The rotor is therefore not a conventional propeller inside a stationary duct: each blade terminates into a moving outer shell, so there are effectively no free blade tips.

The current prototype is approximately **160 mm diameter × 60 mm deep**, printed in PETG, and driven from 12 V. It has been operated over an unusually wide electrical range, from roughly **0.3 A to 10 A** (about **3.6–120 W**).

## Core concept

The rotor can be thought of as a cross between:

- a repeated circumferential slice of an Archimedean-screw-like pumping surface;
- a ducted axial fan;
- and a banded/shrouded impeller in which the "duct" itself co-rotates.

The important geometric feature is the continuous outer cylinder joining the blades. Relative blade-tip clearance to that rotating band is effectively zero; the remaining clearance is the annular gap between the rotating band and the stationary housing.

This is expected to influence both aerodynamics and structure:

- suppress conventional free-tip leakage and tip-vortex formation;
- provide a continuous structural tie between blades;
- constrain blade-tip position and reduce independent blade flex;
- potentially improve pressure performance through restrictive loads;
- move some structural concern from individual free blade tips toward the hub, blade/ring junctions, and hoop stress in the outer band.

These are working hypotheses until measured.

## Prototype observations

- The prototype has run smoothly enough that balance has not been an obvious problem.
- On an early test it produced enough thrust to lift itself a few inches from the bench before power was cut.
- The design deliberately promotes airflow through the motor.
- The critical printed attachment region is air-gapped from the motor rotor to reduce direct thermal exposure.
- An inlet guard exists and mounts to the shroud holes.
- The current PETG rotor is a prototype. Filled PETG or nylon have been considered for later versions, but stiffness, layer adhesion, toughness, fatigue behaviour, and blade/hub retention all need to be considered rather than assuming filled filament is automatically safer.

## Why revive it

The immediate motivation was PC/workbench cooling.

A pair of industrial-style high-static-pressure fans demonstrated that brute-force pressure is available, but even when undervolted they produce objectionable turbulence and tonal/mechanical noise. A large rotor with much lower tip speed should offer a better route to:

- quiet bulk airflow at low power;
- useful static pressure at moderate power;
- and very high cooling reserve when noise is temporarily irrelevant.

The custom fan therefore has the potential to cover both ordinary quiet cooling and extreme test-bench cooling without relying on small, very high-RPM industrial fans.

## Current design question: outer-band splitter vanes

The next design idea is to add **short inward-reaching splitter vanes attached to the rotating outer shell**, between the existing major blades.

The first hypothesis to test is not "more blades are better", but that modest splitters may guide flow in the unusually wide passages and improve performance under restriction.

Expected possible benefits:

- increased local blade solidity;
- reduced slip / internal recirculation in the broad outer passages;
- stronger guidance of flow near the highest-tangential-speed part of the rotor;
- higher static pressure through filters, heatsinks, ducts, or restrictive case geometry.

Expected possible costs:

- reduced open area and potentially lower free-air flow;
- increased aerodynamic drag and electrical power at a given RPM;
- more turbulence and noise;
- greater risk of local separation or passage choking if the splitters are too aggressive.

The preferred first experiment is therefore a **small splitter**, not another full blade: approximately one per main passage, projecting inward perhaps 15–25% of passage width, following the local sweep/helix of the existing surfaces, with a rounded leading edge and generous root fillet.

See [the design rationale](docs/design-rationale-2026-10-03.md) for the conversation-derived reasoning, uncertainties, safety considerations, and proposed test matrix.
