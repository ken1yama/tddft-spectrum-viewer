# Changelog / 変更履歴

All notable changes are listed here. The format follows [Keep a Changelog](https://keepachangelog.com/), and the project uses [Semantic Versioning](https://semver.org/).

## [0.1.0] - 2026-11-16

First tagged release.

### Features
- Read the TDDFT output (`.out` / `.log`) of Gaussian in the browser (nothing is uploaded).
- Transition table with energy, wavelength, oscillator strength, symmetry and major / minor orbital contributions (closed shell and open shell).
- Calculation details: route, functional, basis set, solvent, charge, multiplicity, energies, termination status, etc.
- UV-Vis spectrum: Gaussian / Lorentzian band, x axis in nm / eV / 10³ cm⁻¹, left / right edge, FWHM, reversed x axis, y-axis maxima, figure size and font sizes.
- Download: transition table (CSV), spectrum (PNG / SVG / CSV).
- Japanese / English interface.
- Range is adjusted automatically each time a file is loaded; the range includes every transition regardless of its oscillator strength.
- Wrapped route lines of Gaussian output are joined correctly.

