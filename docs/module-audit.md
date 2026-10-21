# Xbox 360 Module Audit

**Project:** L4D2-Recomp-Android  
**Status:** Initial audit completed  
**Target:** Native ARM64 recompilation research for Android

## 1. Overview

An initial audit was performed on 22 modules associated with the Xbox 360 version of Left 4 Dead 2.

The audit focused on module address ranges, image sizes, dependency relationships, and hardware-specific library references.

This stage documents the binary layout and prepares the project for recompilation feasibility tests.

## 2. Address Map

- Lowest reported address: `0x82000000`
- Highest reported address: `0x8B100000`
- Approximate address-space span: 145 MiB
- Combined reported image sizes: approximately 37 MiB
- Address-range overlap check: passed

The address-space span includes gaps between modules and does not represent the total size of executable code.

## 3. Module Dependencies

The current dependency analysis identifies three groups:

### Group A — Kernel-level dependencies

- `default`
- `tier0_360`

### Group B — tier0 dependencies

- `vstdlib_360`
- `datacache`
- `inputsystem`
- `scenefilecache`
- `stdshader_dx9`
- `vphysics`

### Group C — tier0 and vstdlib dependencies

- `launcher`
- `engine`
- `client`
- `server`
- `matchmaking`
- `filesystem_stdio`
- `GameUI`
- `materialsystem`
- `shaderapidx9`
- `soundemittersystem`
- `studiorender`
- `vgui2`
- `vguimatsurface`
- `vscript`

The observed dependency graph appears relatively shallow.

Runtime interfaces and dependencies must still be verified during subsequent tests.

## 4. Xbox 360-Specific Dependencies

The audit identified references to the following technologies:

| Technology | Reported modules |
|---|---|
| D3D9 | `engine`, `materialsystem`, `shaderapidx9` |
| XAudio2 | `engine`, `shaderapidx9` |
| XHV2 | `engine` |
| XParty | `engine` |
| XOnline | `engine` |

These references identify potential compatibility challenges for an Android implementation.

They do not establish that equivalent Android implementations already exist.

## 5. Recompilation Status

| Test | Status |
|---|---|
| Initial module audit | Completed |
| Address overlap verification | Passed |
| Complete kernel import analysis | Pending |
| Code generation for AArch64 | Not tested |
| Compilation of a module for AArch64 | Not tested |
| Cross-module runtime integration | Not tested |
| Android execution | Not tested |
| Title Update analysis | Pending |

## 6. Next Steps

### Test 1A — Small module

Attempt to process `default.xex` through ReXGlue and determine whether the generated output can be compiled for AArch64.

### Test 1B — Core dependencies

Investigate `tier0_360` and `vstdlib_360`, focusing on imports and cross-module compatibility.

### Test 1C — Dynamic loading

Investigate how `default` interacts with `launcher_360` and whether the expected runtime loading behavior can be reproduced.

## 7. Limitations

This report summarizes the current audit findings.

The analysis does not yet prove that the game can be recompiled successfully, that its runtime dependencies can be reproduced, or that it can execute natively on Android.

Further validation is required.

---

*Part of the L4D2-Recomp-Android research project.*
