# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Documentation

- Expand installation and usage guidance with serial-port troubleshooting, the 11-field packet format, graph controls, startup and no-signal behavior, and tested Processing compatibility.

### Maintenance

- Add CodeMeta project and dependency metadata and automated GitHub metadata synchronization, using repo-sync 5.0.7.
- Add CI and weekly link checks for Markdown documentation and the repository's configured website.
- Enforce LF line endings for repository text files.

## [1.1.0] - 2025-04-29

### Changed

- **Breaking:** Migrate the sketch to Processing 3 APIs and upgrade bundled ControlP5 to 2.2.5; Processing 1.x and 2.x can no longer run the sketch.
- Package the sketch and bundled library together in a matching `BrainGrapher/` folder for the Processing editor.
- Change the default serial-port selection from index 5 to index 0.

### Documentation

- Update dependency guidance for Processing 3.0.2 and ControlP5 2.2.5 and refresh project contact information.
- Add an application screenshot to the README.
- Correct README heading rendering and tutorial links, and rename the file to `readme.md`.

### Maintenance

- Add an MIT license in `license.txt`.

## [1.0.0] - 2014-01-18

### Added

- Visualize attention, meditation, and eight EEG power bands from Arduino Brain CSV packets received over a 9600-baud serial connection.
- Provide per-channel bar meters and graph toggles, with graphing enabled by default.
- Support Lines, Curves, Shaded, and Triangles rendering, adjustable time scale, and local or global maximum scaling.
- Display connection quality with a red/yellow/green indicator and a received-packet counter.
- Skip the first three incoming packets during initialization and zero EEG power readings when the headset reports no signal.

### Documentation

- Document Processing setup, serial-port selection, bundled dependencies, and MindFlex hardware prerequisites, including testing with Processing 1.5.1 and 2.0a5.

### Maintenance

- Consolidate the Processing sketch layout, bundle ControlP5 2.0.4 without a separate library installation, and remove obsolete editor and font assets.

[Unreleased]: https://github.com/kitschpatrol/brain-grapher/compare/v1.1...HEAD
[1.0.0]: https://github.com/kitschpatrol/brain-grapher/releases/tag/v1.0
[1.1.0]: https://github.com/kitschpatrol/brain-grapher/compare/v1.0...v1.1
