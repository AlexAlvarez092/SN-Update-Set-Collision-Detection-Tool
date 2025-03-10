# 📌 Update Set - Collision detection tool

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![license-shield]][license-url]

## 📝 Overview

The **Update Set - Collision detection tool** is a ServiceNow enhancement that allows users to identify potential collisions between update sets before committing them. A collision occurs when an update set modifies the same elements as another update set that has not yet been committed in the next instance (e.g., from Dev to Test or Test to Prod).

### ✨ Features

- **UI Action:** Adds a related link to update sets, enabling users to check for collisions.
- **Service Portal Widget:** Displays a report of conflicting update sets.
- **Automated Release Tracking:** Uses a REST integration to mark update sets as committed in the source instance.
- **Collision Filtering:**
  - Ignores default update sets.
  - Ignores update sets marked as "ignored."
  - Excludes update sets that were overridden by a later committed update set.

###  How It Works

1. The UI Action triggers a Service Portal widget that checks for collisions.
2. A **Script Include** scans the update set for modifications that overlap with another update set that has not been committed.
3. The logic considers an update set as "committed" if its **release_date** field is set.
4. When an update set is committed, a **Business Rule** triggers an event.
5. A **Script Action** listens for the event and calls a **REST API** on the next instance, marking the update set as committed.

## 📂 Installation

1. Import and commit both update sets from this repository:
   - [CollisionToolSourceInstance.xml](./CollisionToolSourceInstance.xml): Includes the UI Action, Service Portal widget, and Script Include.
   - [CollisionToolTargetInstance.xml](./CollisionToolTargetInstance.xml): Contains the Business Rule and REST integration.
2. Ensure proper user permissions to access the Service Portal widget.

## 🚀 Usage

1. Navigate to an update set.
2. Click the "Check for Collisions" related link.
3. Review the list of conflicting update sets.
4. If necessary, resolve conflicts before committing the update set.

## Technical Details

- **Collision Detection Logic:**
  - Extracts all **customer updates** (modifications) from the update set.
  - Checks if any of these updates exist in another update set that is pending commit.
  - Uses the **sys_update_version** table to compare versions and determine conflicts.
- **Filtering Mechanism:**
  - Default update sets are ignored.
  - Update sets marked as "ignored" are skipped.
  - If a conflicting update set was ultimately overridden by a later committed update set, it is ignored.
- **Release Tracking:**
  - Uses the **release_date** field to determine whether an update set has been committed to the next instance.
  - When an update set is committed, the next instance is notified via REST, updating the **release_date**.

## 📢 Contributions

Feel free to contribute by submitting pull requests or reporting issues!

## 📜 License

This project is licensed under the MIT License.

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
