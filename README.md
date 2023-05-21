# Update Set - Collision detection tool

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![license-shield]][license-url]

This small utility allows ServiceNow developers to detect collision between update set before moving them to the upper-level environment. Additionally, it is also possible to analyse a specific developing element such as a business rule, script include, etc.

> **Disclaimer** The utility relies on the release date attribute of an update set to identify which ones are already deployed to next environment. You can either manually set the release data every time you commit the update set to next environment or check out [this other application](https://github.com/AlexAlvarez092/SN-Update-Set-Release-Date) which automates that job.

## Features included

- Toggle on/off property allowing to disable the feature in the production environment.
- Analyse an update set which would be moved to the upper-level environment.
- Analyse a developing object which would be moved to the upper-level environment.
- Exclude out update sets already committed to upper-level environment.
- Exclude out update sets within the same batch.

## Limitations

The tool just finds update sets not yet delivered and not included in the same batch (if there is a batch...) than the update set in-hand that are touching the same configuration objects, but the tool do not check which one has update before or after the configuration object, therefore it is possible false positves.

### Example

Business rule `My business rule` has three versions in the following order:

1. Update set `Update set A` which has been delivered in the next environment.
2. Update set `Update set B` which has not been delivered yet.
3. Update set `Update set C` which has not been delivered yet.

Executing the tool over `Update set B` would return a collision with `Update set C`. In fact this is a false positive as the version `Update set C` was created only after the version `Update set B` thus moving `Update set B` is safe.

# Installation

- Option 1. Clone repository

[contributors-shield]: https://img.shields.io/github/contributors/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool.svg?style=for-the-badge
[contributors-url]: https://github.com/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool/graphs/contributors

[forks-shield]: https://img.shields.io/github/forks/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool.svg?style=for-the-badge
[forks-url]: https://github.com/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool/network/members

[stars-shield]: https://img.shields.io/github/stars/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool.svg?style=for-the-badge
[stars-url]: https://github.com/gAlexAlvarez092/SN-Update-Set-Collision-Detection-Tool/stargazers

[issues-shield]: https://img.shields.io/github/issues/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool.svg?style=for-the-badge
[issues-url]: https://github.com/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool/issues

[license-shield]: https://img.shields.io/github/license/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool.svg?style=for-the-badge
[license-url]: https://github.com/AlexAlvarez092/SN-Update-Set-Collision-Detection-Tool/blob/master/LICENSE.txt
