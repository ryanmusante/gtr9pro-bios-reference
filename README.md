# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![version](https://img.shields.io/badge/version-1.4.0-1793d1?style=flat-square)
![platform](https://img.shields.io/badge/platform-AMD%20Strix%20Halo-ed1c24?style=flat-square)
![firmware](https://img.shields.io/badge/firmware-AMI%20Aptio%20V-555?style=flat-square)
![settings](https://img.shields.io/badge/settings-1018-2563eb?style=flat-square)

Complete catalog of every BIOS Setup option exposed by the Beelink GTR9 Pro
UEFI firmware, decoded directly from the firmware image.

## Contents

| File | Purpose |
| --- | --- |
| `GTR9Pro_BIOS_Settings.pdf` | The reference document |
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
artifacts of the extraction, not real distinct settings. This revision removes
**35 such verbatim-duplicate rows**, keeping one canonical row each.

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

- BIOS Version / Build Date are runtime-populated placeholders.

## Integrity (SHA256)

```
a703615b9273aea31d71d6ecc8dd40a47284e1d2646d249e6c6e2494086c46b1  GTR9Pro_BIOS_Settings.pdf
```
