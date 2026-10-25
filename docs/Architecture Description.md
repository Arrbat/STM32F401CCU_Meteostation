## Overview

Goal: To implement maintainable open-source Meteostation. 

Functionality includes:
- Pressure measurement
- Humidity measurement
- Temperature measurement
- Light detection
- Graphically presented values for display
- UART logging

Since project use MCU, interfaces, external devices, dealing with hardware and firmware, the expected user is likely experienced with embedded engineering 
so that is able to understand and (mainly) deploy the project for its own purposes (both learning or practical)

## Architecture
Project aims to follow architecture:
- App - business logic, is hardware independent, easy to port and reuse.
- API and interfaces - are used by App and hardware-dependent code. In ideal case only requires the hardware-dependent code substitution,
while API is unchanged. In other cases API may be changed.
- HAL/Registers/Linkers and other files are generated and not changed manually (excluding main.c to include app logic)

## Code style

GNU-based style with minor changes

- `clang-format` is defined and automatically used for every commit that includes code changes

## Code Verification and Validation
- Every commit is tested at unit level
- `clang-tidy` is defined and automatically used for every commit that includes code changes

## Commits
- Commits follow the template:
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```
- Commits describe one change per time

References: Conventional Commits

## Hardware Schemes and Verification
- PCB is excluded from project scope for now
- Schemes try to follow general conventions of elements placement, hierarchical sheets and labels usage etc
- Schemes are tested with ERC checks, so that required to have zero errors and as minimum warnings as possible

## License
- MIT license

## Issues 

- Size rules:
```
    XS Edits that do not change the logic: typos, comments, constants, formatting. A single file, usually up to ~5 lines.
    S A local change to the logic in a single file. Does not affect the interfaces of other modules. Does not require changes to any files other than the tests.
    M It's one of two things: simple, coordinated changes across several files (such as renaming or extending a signature), or a significant change to the logic in a single file. Affects one component.
    L A change that affects multiple files with non-trivial logic within a single component or that modifies its interface. Before work begins, it is broken down into subtasks of size M or less; the L-issue remains as the parent/tracking issue.
    XL is not used. Must be break down into smaller issues
```
- Priority rules:
```
P0 Prevents the development, build, release, or operation of core functionality; or a critical defect (data loss, hardware damage, security). Must be addressed immediately, interrupting all current tasks.
P1 Required for the next milestone, but does not block other work at this time. A significant defect that does not block progress, or a task on the critical path. Must be resolved by the milestone deadline.
P2 Scheduled work within a Milestone: features, non-trivial bugs with workarounds. Assigned by default
P3 Not required for Milestones or the project's main objectives. Improvements, refactoring, and minor bugs that do not affect functionality. Worked on as time permits.
P4 Cosmetics, ideas, nice-to-haves. No planned deadline; may be closed without implementation during a backlog review.
```

- Estimate rules:
    Estimation points are assigned according to issue size, where
```
    XS = 1
    S  = 2-3
    M  = 4-5
    L  = 6-10
    XL is not used
```

Issues priority and size options are also described at Github project linked to this repository. "Estimation" is described only in that file.

## Maintainer hardware for which project is in development

- STM32F401CCU6 
- CH340C as UART-USB-C Converter
- Digital Light Sensor Module 
```
(NAMELESS, Characteristics:
Photoresistor, LM393 comparator, output >15 mA, potentiometer threshold, 3.3–5 V, digital output (0/1), mounting hole, 3.2 × 1.4 cm. Pins: VCC (3.3–5 V), GND, DO (digital out).)
```
- AHT10
- BMP280
- Display OLED (SSD1315) S0.96" I2C 128x64
- LEDs