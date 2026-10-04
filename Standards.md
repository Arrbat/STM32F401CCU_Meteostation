## Goal

Standards are aimed to improve project quality, usability and maintainability. All standards described there are recommended, but project has no goal to strictly apply them.
In other words, project has aim to follow them and will try so, but will not officially standardized, so there may exist issues with their implementations. Document may be changed. 

## Repository Structure
- Application, drivers, libs, hal, configs, building files/scripts, tests, documentation and hardware schemes are implemented separately for readability
- Platform-dependent code is separated so that application and its testing is easier to port and maintain

## Commits
- Commits follow the template:
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```
- Commits describe one change per time

References: Conventional Commits

## Code style
- In order to maintain code, ensuring its readability and consistency following references are used:

References: MISRA C 2012, BARR-C:2018

## Code Architecture
- Hardware Interfaces have API
- HAL cannot be called directly by Application Layer
- Project has Application, Drivers, Hardware Layers
- Layers communicate with each other through API

## Code Verification and Validation
- Unit tests are applied on Host for Application Layer
- Static Analysis is applied automatically for every commit that changes code

## Hardware Schemes and Verification
- One Functional block per list
- Hierarchical Lists
- Versioning and ChangeLog 
- ETC, DRC are applied
- SPICE is applied
- Produced values (like Temp) are compared with other similar devices

## Tests
- Unit tests for Application Layer
- API Tests 

## License
- MIT license. 
