# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![doc](https://img.shields.io/badge/doc-1.6.1-1793d1?style=flat-square)
![board](https://img.shields.io/badge/GTR9%20Pro-v2.2-6f42c1?style=flat-square)
![bios](https://img.shields.io/badge/BIOS-GTRPRPI1001C-ed1c24?style=flat-square)
![firmware](https://img.shields.io/badge/firmware-AMI%20Aptio%20V-555?style=flat-square)
![settings](https://img.shields.io/badge/settings-1018-2563eb?style=flat-square)

Complete catalog of every BIOS Setup option exposed by the Beelink GTR9 Pro
(v2.2) UEFI firmware, decoded directly from the firmware image.

## Which revision do you have?

| Revision | NIC | BIOS series |
| --- | --- | --- |
| GTR9 Pro v1.0 | Intel E610-XT2 | `P###` |
| **GTR9 Pro v2.2** (this catalog) | Realtek RT8127 | `PR##` / `GTRPRPI####` |

Identify yours by NIC chipset or current BIOS series.
BIOS downloads: https://dr.bee-link.cn/?dir=uploads%2FGTR%2FGTR9-395%2FBIOS

## Contents

| File | Purpose |
| --- | --- |
| `GTR9Pro_BIOS_Settings.pdf` | Reference document |
| `README.md` | This file |
| `CHANGELOG.md` | Version history |

## Image of record

| | |
| --- | --- |
| Board | Beelink GTR9 Pro **v2.2** |
| BIOS | **GTRPRPI1001C** (32 MB) |
| Prior image | `GTRPR07` (identical Setup interface) |
| BIOS vendor | AMI Aptio V |
| SoC | AMD Strix Halo (Ryzen AI Max+ 395) |

`GTRPRPI1001C` is `GTRPR05` plus `PI 1.0.0c1` (AGESA/PI microcode refresh). A
PI/AGESA update changes silicon-init code, not the Setup interface — all six
Setup-bearing modules are byte-identical (SHA-256) across `GTRPR07` and
`GTRPRPI1001C`, with identical HII string packages. Setting names, types,
ranges, NVRAM values, and defaults apply unchanged to both.

## Coverage

7 form-sets, 186 forms, **1,018** settings (after de-duplication).

| Chapter | Form-set | Settings |
| --- | --- | --- |
| Aptio Setup | Setup | 161 |
| AMD CBS | CbsSetupDxe | 318 |
| AMD PBS | AmdPbsSetupDxe | 202 |
| AMD Overclocking | AodDxe | 153 |
| AMD PMF | AmdCpmPmfBoardDxe | 139 |
| DASH / ASF | DashManagementDxe | 8 |
| RAIDXpert2 | RAID formset | 37 |

Generic UEFI network-stack forms (IPv4/IPv6/VLAN/HTTP/TLS/PXE) are out of scope
(Appendix A).

## De-duplication

Firmware extraction emitted 35 byte-identical rows more than once within a
single form; these are removed (one canonical row kept each). 1,053 − 35 = 1,018.

| Form | Form ID | Removed |
| --- | --- | --- |
| Smart Fan Function | 0x2737 | 21 |
| View Associated Physical Disks | 0x222 | 8 |
| Display Configurations | 0x10 | 4 |
| Trusted Computing | 0x271A | 2 |

Rows sharing an option pattern but addressing distinct hardware/indices (PCI-E
`Device0`–`Device7`, the four CPU Smart Fan controllers, the eight
`PPC Adjustment` variants, the three per-device Trusted Computing forms) are
retained in full.

## Performance markers

Settings with a real performance dimension carry a red `■ performance` marker
with a recommended value for the Ryzen AI Max+ 395 and a one-line rationale,
beside the blue `■ default` factory marker.

| Tag | Meaning |
| --- | --- |
| **CHANGE** | Change away from default for a clear gain |
| **TUNE** | Performance-relevant but workload-specific / expert-only |
| **KEEP** | Default already favors performance; leave it |

TUNE entries are validated starting points, not guaranteed-stable — record
originals before changing low-level CBS, AMD Overclocking, or PMF settings.

## Reading the document

- The PDF is bookmarked by form-set; open the bookmarks panel to jump between
  chapters. Each chapter is one firmware form-set; sub-sections are individual
  Setup pages in firmware presentation order.
- Tables are Setting / Type / Options-Values-Range. Bracketed values are raw
  NVRAM values (usable for SCEWIN/AMISCE scripting).
- Defaults shown are compiled Standard Defaults; a unit's live values may differ.
- Many options are conditionally hidden (suppress-if / grayout-if), so the
  catalog is a superset of what any single unit displays.

## Integrity (SHA256)

```
639371ab19c16c1ef22d37a2d2cb3e0f01cba21a4ea4f50b736bf2585335fa52  GTR9Pro_BIOS_Settings.pdf
```
