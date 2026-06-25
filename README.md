# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![version](https://img.shields.io/badge/doc-1.5.2-1793d1?style=flat-square)
![board](https://img.shields.io/badge/GTR9%20Pro-v2.2-6f42c1?style=flat-square)
![bios](https://img.shields.io/badge/BIOS-GTRPRPI1001C%20(latest)-ed1c24?style=flat-square)
![firmware](https://img.shields.io/badge/firmware-AMI%20Aptio%20V-555?style=flat-square)
![settings](https://img.shields.io/badge/settings-1018-2563eb?style=flat-square)

**GTR9 Pro v2.2 — latest BIOS v (GTRPRPI1001C).** Complete catalog of every BIOS
Setup option exposed by the Beelink GTR9 Pro UEFI firmware, decoded directly
from the firmware image.

## Which revision do you have?

You need to know which GTR9 Pro revision is yours, the original GTR9 Pro v1.0
(Intel E610-XT2 NIC, BIOS vP### series) or the latest GTR9 Pro v2.2 (Realtek
RT8127 NIC, BIOS vPR## series). Check your GTR9 Pro's NIC chipset or its current
BIOS series version to differentiate them. This catalog documents the **v2.2**
(BIOS `GTRPR##` / `GTRPRPI####` series). At the time of this writing:
https://dr.bee-link.cn/?dir=uploads%2FGTR%2FGTR9-395%2FBIOS

## Contents

| File | Purpose |
| --- | --- |
| `GTR9Pro_BIOS_Settings.pdf` | The reference document |
| `README.md` | This file |
| `CHANGELOG.md` | Version history |

## Source

`GTRPRPI1001C` is the current/latest BIOS version for the GTR9 Pro v2.2 and is
the image of record for this catalog. `GTRPR07` is the immediately prior
production image; both expose an identical BIOS Setup interface (verified below),
so the catalog applies to either.

| | |
| --- | --- |
| Board revision | Beelink GTR9 Pro **v2.2** |
| BIOS version (latest) | **GTRPRPI1001C** (`GTRPRPI1001C.rom`, 33,554,432 bytes / 32 MB) |
| Prior image | `GTRPR07.rom` (33,554,432 bytes / 32 MB) |
| Flash packages | `GTRPRPI1001C` (AfuEfi); `GTRPR07_WinFlash` (AMI AFUWIN / AfuEfi) |
| Originally documented image | `GTRPR05.rom` (catalog basis for 1.0.0–1.4.1) |
| BIOS vendor | American Megatrends International (AMI Aptio V) |
| SoC platform | AMD Strix Halo (Ryzen AI Max series APU) |

### Image lineage and what changed

`GTRPRPI1001C` is, per its own release note, **based on `GTRPR05`** with the
single summary change `PI 1.0.0c1` — an AMD AGESA / Platform Initialization
(CPU/SoC microcode) refresh. `GTRPR07` is the corresponding production image
carrying that PI level.

A PI/AGESA refresh updates silicon-init code, not the BIOS Setup interface. We
verified this directly rather than assuming it: every Setup-bearing PE32 module
was extracted from both `GTRPR07` and `GTRPRPI1001C` and compared byte-for-byte.

| Module | Owns chapter | `GTRPR07` vs `GTRPRPI1001C` |
| --- | --- | --- |
| `Setup` (899407D7) | Aptio Setup tree | identical (SHA-256) |
| `CbsSetupDxeSTXH` (C5440ED5) | AMD CBS | identical (SHA-256) |
| `AmdPbsSetupDxe` (BBB77CB9) | AMD PBS | identical (SHA-256) |
| `AodDxe` (442BA91E) | AMD Overclocking | identical (SHA-256) |
| `AmdCpmPmfBoardDxe` (2C20B724) | AMD PMF | identical (SHA-256) |
| `AmdRaid` (AFD69E65) | RAIDXpert2 | identical (SHA-256) |

Both images carry **identical HII string packages** (the on-screen option
labels and help text resolve to the same string IDs: 1181 strings in Setup, 930
in CBS, 693 in PBS, 536 in AOD, 220 in PMF, 587 in RAID). Because the Setup
modules are byte-identical between the two images and structurally consistent
with the `GTRPR05` decode that produced this catalog, **the setting names,
types, value ranges, stored NVRAM values, and defaults documented here apply
unchanged to the latest `GTRPRPI1001C` BIOS (and to `GTRPR07`).** No
setting-level edits were required; the 1.5.0 revision updated provenance only.
The 1.5.1 revision additionally corrected default/performance marker accuracy
in the Options / Values / Range column (mis-pasted performance rationales on
four settings, and ten missing factory-default markers) — see the changelog;
no settings, types, values, or ranges changed.

## Coverage

7 BIOS-owned Setup form-sets, 186 forms, 1,018 configurable settings (after
de-duplication; see below).

| Chapter | Form-set | Settings |
| --- | --- | --- |
| Aptio Setup (Main tree) | Setup | 161 |
| AMD CBS | CbsSetupDxe | 318 |
| AMD PBS | AmdPbsSetupDxe | 202 |
| AMD Overclocking | AodDxe | 153 |
| AMD PMF | AmdCpmPmfBoardDxe | 139 |
| DASH / ASF | DashManagementDxe | 8 |
| RAIDXpert2 | (RAID formset) | 37 |

Generic UEFI network-stack driver forms (IPv4/IPv6/VLAN/HTTP/TLS/PXE) are out of
scope and inventoried in Appendix A.

## De-duplication

The firmware IFR extraction emitted some option rows more than once **within a
single form** — identical setting name, type, and stored values. These are
artifacts of the extraction, not real distinct settings. This revision keeps
**35 such verbatim-duplicate rows** removed, keeping one canonical row each.

The firmware tables as shipped held **1,053** option rows; removing the 35
duplicates leaves **1,018**. (Prior revisions quoted 1,045 in prose — that
figure had already deducted the 8 duplicate *View Associated Physical Disks*
rows in the count without removing them from the tables; 1,045 − the remaining
27 duplicates also lands at 1,018.)

Removals by form:

| Form | Form ID | Rows removed |
| --- | --- | --- |
| Smart Fan Function | 0x2737 | 21 |
| View Associated Physical Disks | 0x222 | 8 |
| Display Configurations | 0x10 | 4 |
| Trusted Computing | 0x271A | 2 |

Only **byte-identical** repeats were removed. Settings that share an option
pattern but address **distinct hardware or indices** are NOT duplicates and are
retained in full — for example PCI-E Port `Device0`–`Device7` and their
`ASPM Mode Control(DeviceN)` / `Hotplug Mode Control(DeviceN)` rows, the four
independent CPU Smart Fan controllers, the eight `PPC Adjustment` P-state-count
variants, and the three per-device Trusted Computing form variants (0x2719 /
0x271A / 0x271B, which the firmware presents per detected TPM/security device).

## Performance recommendations

Settings with a real performance dimension carry a red `◀ performance` marker
beneath the option list, with a recommended value for the Ryzen AI Max+ 395
platform and a one-line rationale. It mirrors the blue `◀ default` factory
marker; where both apply, `◀ default` sits on the default value and
`◀ performance` follows on the line beneath. Each marker line is shaded in its
marker color — blue behind `◀ default`, red behind `◀ performance` — for
at-a-glance scanning.

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
5. Verbatim-duplicate rows within a form removed (one canonical row kept each),
   decoded from the shipped PDF's tagged table structure.
6. Cross-image verification (this revision): all six Setup-bearing modules
   extracted from `GTRPR07` and the latest `GTRPRPI1001C` and compared by
   SHA-256; HII string packages compared by resolved string set. All identical.

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

- BIOS Version / Build Date on the Main page are runtime-populated; this catalog
  documents the GTR9 Pro v2.2 latest BIOS, `GTRPRPI1001C`.
- The Setup interface is identical across `GTRPR05`, `GTRPR07`, and the latest
  `GTRPRPI1001C`; differences between these images are confined to AGESA/PI
  silicon-init code, which is outside the BIOS Setup catalog.

## Integrity (SHA256)

```
83bf8f716f81db007b1f34adf1fdd5441b697ad8f207a4357e74cb0c8d0523e5  GTR9Pro_BIOS_Settings.pdf
```
