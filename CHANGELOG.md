# Changelog

You can find all notable changes to Bridge For Git Explorer in this document.

## [0.6.1] &ndash; 2025-12-12

### Fixed

- Fixed an issue that prevented any extension function from being automatically re-invoked if a certificate error occurs and **Disable and Retry** was selected.

## [0.6.0] &ndash; 2025-10-24

### Added

- Added compatibility with Bridge for Git 3.0.
- Added Bridge for Git aliases support.
- Mapping Activity setting that enables you to specify the number of operations to list.

### Changed

- Mapping Activity view changed to show repositories instead of branch nodes. Listed operations now include the operations of the entire mapping (unlike operations in separate branches).

## [0.5.3] &ndash; 2025-01-27

### Added

- Added tooltips for element and branch nodes with information about Endevor inventory and mapping.

### Fixed

- Fixed an issue that prevented elements from being added to the mapping when multiple target locations are available.

## [0.5.2] &ndash; 2024-09-09

### Fixed

- Fixed the 'read our documentation' link in the Bridge for Git Explorer welcome view.
- Fixed an issue that prevented the blame lines from being rendered in the Element change level comparing tabs.

## [0.5.1] &ndash; 2024-07-15

### Added

- Added a Git Pre-push hook un-installation ability. You can also uninstall or re-install the Pre-push hook for a particular mapping.

### Changed

- Adjust Git Pre-push hook installation indication and messages.

## [0.5.0] &ndash; 2024-06-24

### Added

- Added a Git Pre-push hook installation detection. You can now automatically install a Git Pre-push hook for a mapping or you can skip installation.
- Added an ability to see a detailed message for each of the status records in the Mapping Activity view.

### Fixed

- Fixed an issue that prevented the Update Processor Group action on the elements, that were newly added to the mapping, from using.
- Fixed an issue with the flickering of the Welcome message in the Elements view during the extension initialization.
- Fixed an issue that led to performance degradation during git branch switching.

### Changed

- Mapping Activity view default location is changed to the bottom panel.
- Changed the VSCode version requirement. Ensure that you use VSCode 1.82.0 or higher.

## [0.4.1] &ndash; 2023-10-16

### Added

- Added proper handling for Bridge for Git and Endevor connection issues related to invalidation of certificate or use of self-signed certificates.
- Zowe Bridge for Git and Endevor profile used for mapping actions are now explicitly reported in the extension logs.

### Fixed

- Fixed an issue with adding element to the mapping operation which falsely reported that a subsystem for the element is not found in certain scenarios.
- Fixed an issue with "Unexpected end of JSON input" pop-up message appearing constantly when switching between the editor tabs in VSCode.

## [0.4.0] &ndash; 2023-09-05

### Added

- Bridge for Git mapping activity section. Review the Bridge for Git activity in the currently opened mapping.
- Elements History section in the tree. See the changes and the authors of changes in elements directly in the editor area.
- Specify processor groups for elements feature. Now you can update processor groups for your elements in a VS Code workspace.

### Changed

- Improved experience with profiles. Zowe V1 and team configuration profiles are still supported but are not necessary for the extension to work.

### Fixed

- Introduced minor logging mechanism improvements.

## [0.3.0] &ndash; 2022-11-04

### Added

- Support for Zowe V2 profiles with Team and User Configuration files.
- Support for version 4 of the mapping.json files (Bridge for Git version 2.12.0).

## [0.2.5] &ndash; 2022-05-23

### Added

- Support for v1 Endevor REST API (Endevor version 18.0).

## [0.2.4] &ndash; 2022-04-08

### Changed

- Changed the VS Code version requirement. Ensure that you use VS Code 1.58.0 or higher.

### Fixed

- Removed the outstanding CA reference from the extension description as part of the re-branding effort.

## [0.2.3] &ndash; 2022-02-23

### Added

- Added a `Show logs` button in the notification panel, which enables you to open the output of the extension.
- Added a build commit hash to the extension activation message.

### Changed

- Reworked the documentation by introducing the product name rebranding changes.
- Improved user notifications and log messages.

### Fixed

- Fixed an issue in the URI building process. Characters that may potentially break the building process are escaped.

## [0.2.2] &ndash; 2021-11-23

### Added

- Added the compatibility for the latest Endevor WebServices charset response headers

## [0.2.1] &ndash; 2021-10-27

### Added

- Added support for the latest version of the BFG mapping configuration

## [0.2.0] &ndash; 2021-07-05

### Added

- Added the tree view multi-selection ability
- Added support for the multi-branch & multi-system BFG mappings
- Added support for the HTTPS sessions for the Endevor and BFG connections
- Added progress bars for the long operations

### Fixed

- Fixed the refresh icon in the tree view

### Changed

- Improved the user notifications and messages
- Improved the internal type system
- Improved the codebase structure. Migrated the content to the monorepo

## [0.1.1] &ndash; 2020-12-16

### Fixed:

- Fixed a bug in the display of the license on the Visual Studio Code Marketplace as well as in the Open VSX Registry

## [0.1.0] &ndash; 2020-11-02

- Initial release
