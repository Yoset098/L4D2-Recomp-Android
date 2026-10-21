# L4D2-Recomp-Android

**Experimental native ARM64 recompilation research for Left 4 Dead 2 on Android.**

## Project Overview

L4D2-Recomp-Android is an experimental research project investigating the feasibility of recompiling the Xbox 360 version of Left 4 Dead 2 for ARM64 devices running Android.

The goal is to explore a native execution path rather than relying on traditional Windows emulation.

## Current Progress

### Phase I — Module Audit

- [x] Audited 22 Xbox 360 modules.
- [x] Documented module address ranges and image sizes.
- [x] Checked address ranges for overlaps.
- [x] Analyzed module dependency relationships.
- [x] Identified Xbox 360-specific graphics, audio, and online dependencies.

### Phase II — Recompilation Feasibility

- [ ] Install and validate the ReXGlue toolchain.
- [ ] Test code generation using `default.xex`.
- [ ] Validate AArch64 compilation.
- [ ] Test core module dependencies.
- [ ] Investigate dynamic module loading.

## Technical Challenges

- PowerPC to AArch64 code generation.
- Xbox 360 kernel and system API compatibility.
- Direct3D 9 graphics translation to a suitable Android rendering backend.
- Audio, input, filesystem, and runtime integration.

## Current Status

**Research and reverse-engineering stage.**

The module audit is complete, but successful AArch64 code generation and execution on Android have not yet been demonstrated.

## Disclaimer

This is an independent research project and is not affiliated with or endorsed by Valve.

No proprietary game binaries are distributed through this repository.
