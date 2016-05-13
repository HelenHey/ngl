# Change Log
All notable changes to this project will be documented in this file, following the suggestions of [Keep a CHANGELOG](http://keepachangelog.com/). This project adheres to [Semantic Versioning](http://semver.org/).


## [Unreleased]
### Added
- `backgroundColor` parameter for `Stage`
- `OX1` atoms are recognized as part of the protein backbone
- `stage.makeImage` now increments the task counter
- added `.isIdentity` method to test if an `Assembly` is an identity transformation over all chains
- embedded-dev build target (@sbliven)
- support for responseType = "json" to efficiently load json data

### Changed
- there is no longer a fake unitcell created when no space group information is available
- the query string is removed from urls before the determining file info (e.g. name, extension)

### Removed
- `stage.setTheme` removed (use new `backgroundColor` parameter), themes now part of GUI code
- `NGL.Preferences` is now part of the GUI code and removed from `NGL.Stage`. Setting `overwritePreferences: true` when instantiating an `NGL.Stage` object is not necessary anymore.
- removed .requestVisibility method and signal (too GUI specific, if needed, should be handled there)


## [v0.7] - 2016-05-08
### Added
- Store and Proxy classes for memory efficiency
- MMTF, DXBIN, DCD files format parsers
- 'unitcell' representation
- stage.makeImage (returns Promise)
- take NCS operations into account when creating unitcell & supercell assemblies
- added multi sample antialias rendering
- added support for spinning around an axis
- use bitsets for storing selections of atoms
- Assembly and AssemblyPart classes
- stage.toggleFullscreen method
- read occupancy data when available (mmCIF, pdb, mmtf)
- occupancy color scheme
- alternate location support in selections, e.g. %B
- read insertion codes when available (mmCIF, pdb, mmtf)
- insertion code support in selections, e.g. ^A
- numeric residue name support in selections, e.g. [032]
- Queue class to handle async tasks

### Changed
- fixed transformation matrix in mrc/ccp4 parser
- optimized near clipping
- Fiber class remanamed to Polymer
- more consistent fog
- use workers more sparsely due to the large overhead of creating them
- create font SDF on demand, remove asset dependency
- integrated three.js lighting into custom shaders
- MIGRATION: chainname read from `auth_asym_id` instead of from `label_asym_id` field
- DOC: clarified apache configuration for deployment
- FIX: cif parser, ignore non-displayable bonds between symmetry mates
- FIX: cif parser, struct_conn bonds not added for multiple altloc atoms
- LIB: updated signals.js
- LIB: updated promise.js
- LIB: updated three.js
- LIB: updated pako.js to pako_inflate.js (no deflation support needed)
- CODE: support loading of Blob objects in addition to File objects
- CODE: tweaked DistanceRepresentation visibility params

### Removed
- zip, lzma, bzip2 decompression
- removed async.js
- mdsrv related code and documentation
- stage.exportImage (makes image and triggers download), use stage.makeImage


## [v0.6] - 2015-10-12
### Added
- MIGRATION: `Stage.loadFile` signature changed, now returns a `Promise` and does not accept callbacks
- MIGRATION: moved trajectory server into its own repository: [MDSrv](https://github.com/arose/mdsrv/)
- ADD: Support for MOL2 and SDF files
- ADD: Support for DX files
- ADD: Support for PQR files
- ADD: `ExampleRegistry` singleton
- ADD: `PluginRegistry` singleton
- ADD: `Datasource` class to use instead of hard-coded paths
- ADD: `GidPool`
- ADD: simple xml parser
- ADD: APBS plugin to load PQR and DX file, simple GUI
- ADD: bond and surface picking
- ADD: User-defined color schemes (API)
- GUI: `VirtualList` and `VirtualTable`
- GUI: re-sizable sidebar (contents still need to be made responsive)
- WIP: scripting API

### Changed
- EXAMPLES: general fixes and enhancements
- DOC: moved installation and development information into the README
- GUI/DOC: Higher color contrast for GUI and documentation pages
- CODE: qunit updated
- CODE: moved logical units of code into their own files
- CODE: speeded up secondary structure assignment from PDB/mmCIF files; fixed bugs leading to wrong assignment
- CODE: element color scheme now uses colorValue parameter to color carbon elements
- CODE: script and assets paths are now configurable
- CODE: more forgiving pdb parsing wrt to model records
- CODE: helper function for re-ordering atoms
- CODE: enhancements to handling Web Workers (`WorkerPool`, lazy Worker creation)
- CODE: enhancements to volume triangulation (limit to given box, skip empty parts)
- CODE: all `*Buffer` classes now inherit from `Buffer` and share common code
- CODE: BufferAttributes can be re-used or grown
- CODE: moved Buffer-specific code out of Representation class
- CODE: molecular surface enhancements (color by atom, filter by atom)
- CODE: nicer clipping of meshes and impostors (unlit interior to make them appear solid)
- CODE: optimized kdtree building
- CODE: clearer atomnames handling for fiber creation
- CODE: Color handling code refactored exposing more parameters
- CODE: Basic support for async creation of representations (so far used for molecular surfaces and volume triangulation)
- CODE: chunked data loading and parsing via streamer class
- CODE: faster autobonding of large residues (e.g. hydrated lipids)
- CODE: WebWorker support while using development and build files
- CODE: WebWorker used for decompression, parsing and surface generation
- FIX: Issue #7
- FIX: residues at the end of fibers may not require all backbone atoms
- FIX: standard compatible atom names when writing pdb files
- FIX: origin coordinates not used/read from mrc header

### Removed
- DEL: removed FragFit plugins


## v0.5 - 2015-30-04
### Added
- Initial release


[Unreleased]: https://github.com/arose/ngl/compare/v0.7...HEAD
[v0.7]: https://github.com/arose/ngl/compare/v0.6...v0.7
[v0.6]: https://github.com/arose/ngl/compare/v0.5...v0.6