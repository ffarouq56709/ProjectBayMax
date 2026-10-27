## Day 3 — Project Charter Nominal-Case Analysis

| Field | Value |
|---|---|
| Day | 3 |
| Phase | Phase 1 — Requirements, access, and risk |
| Week | 1 |
| Revision | v1.1 |
| Date | 2026-10-23 |
| Owner | Faisal Farouq |
| Units | SI units: millimeters (mm), kilograms (kg), seconds (s), meters per second (m/s), newtons (N), and newton-meters (N·m) |
| Hardware required | None |
| Previous accepted input | [Day 1 accepted input summary](#day-1-accepted-input-summary) |
| Previous accepted artifact | [Day 2 comparison and completion decision](#day-2-comparison-and-completion-decision) |

### 1. Tools and inputs

Tools used:

- Text editor
- Project requirements table
- Project calendar
- Calculator
- Revision history

Parts and materials:

- No hardware
- No fabrication materials
- No physical testing equipment

### 2. Nominal-case purpose

This analysis checks whether the project charter is internally consistent with the first walking claim:

> A six-foot biped whose first walking claim is three slow, consecutive tethered steps in a cleared test cell.

The required acceptance values are:

- Height: 1,829 mm
- Consecutive steps: 3
- Walking-speed range: 0.10–0.15 m/s

This is a document-level nominal-case analysis. It does not prove that the physical robot can walk or meet its mass, strength, balance, or actuator requirements.

### 3. Day 3 shall-requirements

| ID | Shall-requirement | Owner | Verification method | Status |
|---|---|---|---|---|
| SYS-001 | The robot shall have an overall sole-to-crown height of 1,829 ± 10 mm. | Faisal Farouq | Compare the master CAD height with 1,829 mm and later measure the completed robot. | PROVISIONAL TARGET |
| SYS-002 | The robot shall have a target operating mass of 55 kg or less and shall trigger a design review if projected mass exceeds 65 kg. | Faisal Farouq | Calculate the CAD mass and reconcile it with component specifications, measured part masses, and the final scale measurement. | PROVISIONAL TARGET |
| SYS-003 | The lower body shall contain 10 active joints: five active joints in each leg. | Faisal Farouq | Inspect the joint register, CAD assembly, MuJoCo model, control configuration, and completed robot. | PROVISIONAL TARGET |
| WALK-001 | The robot shall complete three consecutive tethered steps twice at a target speed of 0.10–0.15 m/s in a cleared test cell. | Faisal Farouq | Review synchronized test video, commanded velocity, estimated velocity, and joint telemetry from an authorized walking test. | PROVISIONAL TARGET |
| BUD-001 | Total project spending shall remain between USD 6,350 and USD 10,000, including contingency. | Faisal Farouq | Compare supplier quotes, approved purchases, invoices, and the final cost ledger with the project budget. | PROVISIONAL TARGET |
| ACCESS-001 | Restricted fabrication, plastic forming, high-energy electrical work, battery handling, lifting, energization, load testing, and walking tests shall be performed only by a named person or vendor authorized for that work. | Faisal Farouq | Inspect the authorization record, released work order, and returned evidence for every gated task. | REQUIRED CONTROL |
| CLAIM-001 | The first-year prototype shall not claim to diagnose disease, recommend treatment, replace a caregiver or clinician, guarantee emergency response, lift a person, walk untethered in public, or walk while carrying a heavy payload. | Faisal Farouq | Review the project charter, interface text, reports, demonstration script, video captions, and public project descriptions. | REQUIRED CONTROL |

### 4. Nominal inputs

| Input | Symbol | Nominal value | Units | Source |
|---|---:|---:|---|---|
| Overall height | `H_TOTAL` | 1,829 | mm | Accepted project target |
| Target operating mass | `M_TARGET` | 55 | kg | Day 2 charter |
| Mass design-stop limit | `M_STOP` | 65 | kg | Day 2 charter |
| Joints per leg | `N_JOINTS_LEG` | 5 | joints | Lower-body architecture |
| Number of legs | `N_LEGS` | 2 | legs | Biped configuration |
| Required active lower-body joints | `N_LEG_DOF` | 10 | joints | Accepted project target |
| Required consecutive steps | `N_STEPS` | 3 | steps | Accepted walking claim |
| Required successful sequences | `N_SEQUENCES` | 2 | sequences | Day 2 charter |
| Minimum target speed | `V_WALK_MIN` | 0.10 | m/s | Accepted walking claim |
| Maximum target speed | `V_WALK_MAX` | 0.15 | m/s | Accepted walking claim |
| Nominal analysis speed | `V_WALK_NOM` | 0.125 | m/s | Midpoint calculation |
| Minimum project budget | `COST_LOW` | 6,350 | USD | Day 2 charter |
| Maximum project budget | `COST_HIGH` | 10,000 | USD | Accepted budget limit |
| Nominal planning budget | `COST_NOM` | 8,175 | USD | Budget midpoint calculation |

Every engineering value above remains provisional until supported by completed analysis, simulation, inspection, or testing.

### 5. Height calculation

The target height is:

`H_TOTAL = 1,829 mm`

Conversion to meters:

`1,829 mm ÷ 1,000 = 1.829 m`

Conversion to inches:

`1,829 mm ÷ 25.4 = 72.008 in`

Conversion to feet:

`72.008 in ÷ 12 = 6.0007 ft`

An exact height of 6 ft is:

`6 ft × 12 in/ft × 25.4 mm/in = 1,828.8 mm`

Difference between the project target and exactly 6 ft:

`1,829 mm − 1,828.8 mm = 0.2 mm`

Result:

- Required height: 1,829 mm
- Nominal charter height: 1,829 mm
- Difference: 0 mm relative to the stated requirement
- Difference from exactly 6 ft: +0.2 mm
- Status: **PASS**

The height target is consistent with the description of a six-foot robot.

### 6. Lower-body joint calculation

The planned active joints in each leg are:

1. Hip pitch
2. Hip roll
3. Knee pitch
4. Ankle pitch
5. Ankle roll

Calculation:

`5 active joints per leg × 2 legs = 10 active lower-body joints`

Result:

- Required active lower-body joints: 10
- Nominal architecture: 10
- Difference: 0
- Status: **PASS**

This only verifies the joint count. It does not validate joint range, torque, speed, strength, balance authority, or control performance.

### 7. Walking-step calculation

Required first walking claim:

`N_STEPS = 3 consecutive tethered steps`

Nominal charter value:

`N_STEPS = 3 consecutive tethered steps`

Step-count difference:

`3 nominal steps − 3 required steps = 0 steps`

The robot must complete the full three-step sequence without:

- Falling into the tether
- Requiring a person to manually reposition it
- Touching an external support with its arms
- Resetting the controller between steps
- Leaving the cleared test cell
- Exceeding an approved safety limit

Result:

- Required consecutive steps: 3
- Nominal consecutive steps: 3
- Step-count margin: 0
- Status: **PASS**

Because the nominal value exactly equals the minimum requirement, there is no step-count margin. Simulation should therefore target more than three stable steps before physical testing.

### 8. Walking-speed calculation

Accepted speed range:

`0.10 m/s ≤ V_WALK ≤ 0.15 m/s`

Nominal speed is the midpoint:

`V_WALK_NOM = (0.10 m/s + 0.15 m/s) ÷ 2`

`V_WALK_NOM = 0.125 m/s`

Margin above the minimum:

`0.125 m/s − 0.10 m/s = 0.025 m/s`

Margin below the maximum:

`0.15 m/s − 0.125 m/s = 0.025 m/s`

Range check:

`0.10 m/s ≤ 0.125 m/s ≤ 0.15 m/s`

Result:

- Minimum accepted speed: 0.10 m/s
- Nominal analysis speed: 0.125 m/s
- Maximum accepted speed: 0.15 m/s
- Margin to either boundary: 0.025 m/s
- Status: **PASS**

The nominal value is centered inside the accepted speed range.

### 9. Mass-limit calculation

Target operating mass:

`M_TARGET = 55 kg`

Design-stop mass:

`M_STOP = 65 kg`

Difference between target and design stop:

`65 kg − 55 kg = 10 kg`

Percentage margin relative to the design-stop mass:

`10 kg ÷ 65 kg × 100 = 15.4%`

Result:

- Target operating mass: 55 kg
- Design-stop mass: 65 kg
- Available mass difference: 10 kg
- Relative margin to the design stop: 15.4%
- Charter-definition status: **PASS**
- Physical-validation status: **PROVISIONAL**

The charter contains a numerical mass target and stop condition. Actual compliance cannot be established until the component mass budget and CAD mass model are completed.

### 10. Budget calculation

Budget range:

`USD 6,350 ≤ COST_TOTAL ≤ USD 10,000`

Nominal midpoint:

`COST_NOM = (USD 6,350 + USD 10,000) ÷ 2`

`COST_NOM = USD 8,175`

Headroom between the nominal budget and maximum budget:

`USD 10,000 − USD 8,175 = USD 1,825`

Result:

- Minimum planned budget: USD 6,350
- Nominal planning value: USD 8,175
- Maximum budget: USD 10,000
- Nominal upper-budget headroom: USD 1,825
- Status: **PASS**

This is a planning calculation only. Supplier quotations and actual purchases have not yet validated the final cost.

### 11. Access-boundary evaluation

The access requirement contains:

- A named accountable owner
- A defined list of gated activities
- A requirement for an authorized executor
- A requirement for released work instructions
- A requirement for returned inspection or test evidence

Ownership by Faisal Farouq does not imply authorization to use restricted equipment.

Acceptable execution paths include:

- Properly authorized Jacobs personnel
- Supervised work performed under applicable facility rules
- An approved outside fabrication vendor
- Purchase of commercially manufactured components

Result:

- Owner identified: Yes
- Restricted tasks identified: Yes
- Authorization condition identified: Yes
- Evidence requirement identified: Yes
- Status: **PASS**

No physical work is authorized by this nominal-case analysis.

### 12. Excluded-claims evaluation

The excluded-claims requirement explicitly prevents the project from claiming that the first-year prototype:

- Diagnoses medical conditions
- Recommends treatment
- Replaces medical or caregiving professionals
- Guarantees emergency response
- Lifts or supports people
- Walks untethered around the public
- Walks while carrying a heavy payload
- Has validated untested provisional values

Result:

- Excluded claims are explicitly listed: Yes
- Owner identified: Yes
- Verification method identified: Yes
- Status: **PASS**

### 13. Acceptance comparison

| Acceptance item | Required value | Nominal result | Comparison | Status |
|---|---:|---:|---|---|
| Overall height | 1,829 mm | 1,829 mm | Exact match | PASS |
| Consecutive tethered steps | 3 | 3 | Exact match | PASS |
| Minimum walking speed | 0.10 m/s | 0.125 m/s | 0.025 m/s above minimum | PASS |
| Maximum walking speed | 0.15 m/s | 0.125 m/s | 0.025 m/s below maximum | PASS |
| Active lower-body joints | 10 | 10 | Exact match | PASS |
| Target operating mass | 55 kg or less | 55 kg nominal | At target | PASS — PROVISIONAL |
| Mass design stop | 65 kg | 65 kg | Stop condition defined | PASS |
| Maximum budget | USD 10,000 | USD 8,175 nominal | USD 1,825 below maximum | PASS |
| Access boundary | Explicit control required | Explicit control included | Requirement satisfied | PASS |
| Excluded claims | Explicit exclusions required | Explicit exclusions included | Requirement satisfied | PASS |

### 14. Day 3 decision

**Overall status: PASS — nominal charter analysis only.**

The nominal charter values satisfy the stated document-level acceptance condition:

- Height: 1,829 mm — **PASS**
- Consecutive tethered steps: 3 — **PASS**
- Target speed: 0.10–0.15 m/s — **PASS**
- Nominal evaluated speed: 0.125 m/s — **PASS**

Every required shall-statement contains:

- A number or explicit control condition
- Faisal Farouq as the owner
- A verification method
- A current status

No required requirement is missing these elements. The Day 3 stop condition is therefore not triggered.

This PASS does not demonstrate that the robot is physically capable of walking. Height, mass, joint performance, stability, actuator capacity, plastic-panel clearance, caregiver functions, and physical safety remain unvalidated.

### 15. Stop condition

Immediately stop the charter analysis and record **BLOCKED** if any required requirement lacks:

- A numerical value or explicit control condition
- A named owner
- A verification method

Record **REWORK** if a calculation or proposed design falls outside an accepted numerical range.

Record **BLOCKED** if a required calculation cannot be completed because an essential input, authorization, or source is missing.

### 16. Next dependency

Day 4 shall convert the accepted charter into a requirements-traceability and engineering-input package.

The next work shall include:

1. Create a component-level mass budget.
2. Allocate the 55 kg target across the frame, actuators, batteries, electronics, arms, sensors, and plastic panels.
3. Define provisional step length, foot clearance, stance width, and gait-cycle timing.
4. Connect the 10-joint architecture to the MuJoCo model.
5. Begin joint torque and gearbox calculations.
6. Identify unresolved requirements and conflicting assumptions.
7. Identify the authorized reviewer for structural and fall-protection calculations.
8. Keep every unverified engineering value marked as provisional.

### 17. Revision-history entry

| Revision | Date | Author | Change |
|---|---|---|---|
| v1.1 | 2026-10-23 | Faisal Farouq | Added Day 3 nominal-case calculations for height, lower-body joint count, walking steps, walking speed, mass, budget, access boundaries, excluded claims, acceptance comparison, status, stop condition, and next dependency. |
