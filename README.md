# Update Set - Collision detection tool

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![license-shield]][license-url]

This small utility allows ServiceNow developers to detect collision between update set before moving them to the upper-level environment. Additionally, it is also possible to analyse a specific developing element such as a business rule, script include, etc.

**Disclaimer** The utility relies on the release date attribute of an update set to identify which ones are already deployed to next environment. You can either manually set the release data every time you commit the update set to next environment or check out [this other application](https://github.com/AlexAlvarez092/SN-Update-Set-Release-Date) which automates that job.

Features included:

- Toggle on/off property allowing to disable the feature in the production environment.
- Analyse an update set which would be moved to the upper-level environment.
- Analyse a developing object which would be moved to the upper-level environment.

# Installation

- Option 1. Cloning repository
- Option 2. Committing [update set](./releases/collision_detection_tool_200.xml)

## System properties

| Property name | Description |
| ------------- | ----------- |
| `collision_detection.app_file.active` | Toggle on/off the feature (developing element) |
| `collision_detection.app_file.exclude_completed_ignored` | Exclude update sets in states completed / ignored |
| `collision_detection.app_file.exclude_default` | Exclude update sets markes as default |
| `collision_detection.app_file.exclude_your_own_sets` | Exclude your own update sets |
| `collision_detection.set.active` | Enable / disable the feature (update set) |
| `collision_detection.set.exclude_default` | Exclude update sets markes as default |
| `collision_detection.set.exclude_updated_before` | Exclude update sets updated before |

## UI Actions

**`collision_detection`**

Ad-hoc run a scanner finding potential conflicts with other update sets.

## Business Rules

**`Collision detection [App file]`**

Automatically run a scanner finding potential conflicts with other update sets.

**`Conflicts detection [Update set]`**

Automatically run a scanner finding potential conflicts with other update sets.


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
