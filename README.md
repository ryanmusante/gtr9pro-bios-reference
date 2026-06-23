# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![version](https://img.shields.io/badge/version-1.3.7-1793d1?style=flat-square)
![platform](https://img.shields.io/badge/platform-AMD%20Strix%20Halo-ed1c24?style=flat-square)
![firmware](https://img.shields.io/badge/firmware-AMI%20Aptio%20V-555?style=flat-square)
![settings](https://img.shields.io/badge/settings-1045-2563eb?style=flat-square)

Complete catalog of every BIOS Setup option exposed by the Beelink GTR9 Pro
UEFI firmware, decoded directly from the firmware image.

## Contents

| File | Purpose |
| --- | --- |
| `GTR9Pro_BIOS_Settings.docx` | The reference document (editable Word) |
| `README.md` | This file |
| `CHANGELOG.md` | Version history |

## Source

| | |
| --- | --- |
| Firmware image | `GTRPR05.rom` (33,554,432 bytes / 32 MB) |
| Flash package | `GTRPR05_WinFlash` (AMI AFUWIN / AfuEfi) |
| BIOS vendor | American Megatrends International (AMI Aptio V) |
| SoC platform | AMD Strix Halo (Ryzen AI Max series APU) |

## Coverage

7 BIOS-owned Setup form-sets, 186 forms, 1,045 configurable settings.

| Chapter | Form-set | Settings |
| --- | --- | --- |
| Aptio Setup (Main tree) | Setup | 184 |
| AMD CBS | CbsSetupDxe | 318 |
| AMD PBS | AmdPbsSetupDxe | 206 |
| AMD Overclocking | AodDxe | 153 |
| AMD PMF | AmdCpmPmfBoardDxe | 139 |
| DASH / ASF | DashManagementDxe | 8 |
| RAIDXpert2 | (RAID formset) | 37 |

Generic UEFI network-stack driver forms (IPv4/IPv6/VLAN/HTTP/TLS/PXE) are out of
scope and inventoried in Appendix A.

## Performance recommendations

Settings with a real performance dimension carry a red `◀ performance` marker
beneath the option list, with a recommended value for the Ryzen AI Max+ 395
platform and a one-line rationale. It mirrors the blue `◀ default` factory
marker; where both apply, `◀ default` sits on the default value and
`◀ performance` follows on the line beneath.

Each performance marker carries a tier tag:

| Tag | Meaning |
| --- | --- |
| **CHANGE** (green) | Change away from default for a clear gain |
| **TUNE** (orange) | Performance-relevant but workload-specific / expert-only |
| **KEEP** (blue) | Default already favors performance; leave it |

Settings with no performance dimension (security, connectivity, debug, or
factory-trained values) carry no `◀ performance` marker. TUNE entries are
validated starting points, not guaranteed-stable values — record originals
before changing low-level CBS, AMD Overclocking, or PMF settings.

## Methodology

1. ROM unpacked with UEFIExtract (UEFITool, built from source).
2. IFR decoded per Setup-bearing PE32 via Universal-IFR-Extractor (built from source).
3. HII string packages decoded with a custom SIBT block parser to resolve labels
   the stock extractor left unresolved, verified against its known-good output.
4. Internal scratch forms, runtime device-enumeration lists, and unlabeled
   working variables filtered out for readability.

## Reading the document

- Each chapter is one firmware form-set; sub-sections are individual Setup pages,
  in firmware presentation order.
- Settings tables are Setting / Type / Options-Values-Range. Bracketed values are
  raw NVRAM values (usable for SCEWIN/AMISCE scripting). The factory default
  carries a blue `◀ default`; rows with no fixed default (free input, runtime
  lists, IFR-unexposed defaults) are left unmarked rather than guessed.
- Defaults shown are compiled Standard Defaults; a unit's live values may differ.
- Many options are conditionally hidden (suppress-if / grayout-if), so this
  catalog is a superset of what any single unit displays.

## Notes

- The Table of Contents is a live Word field — open in Word and Update Field to
  populate it. It may show blank until updated.
- BIOS Version / Build Date are runtime-populated placeholders.

## Integrity (SHA256)

```
c92fde7027cbad513ef943fbe3b26f3bd3e3d290b5bcad9fb7247070084d8133  GTR9Pro_BIOS_Settings.docx
```
