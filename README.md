# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![doc](https://img.shields.io/badge/doc-1.6.5-1793d1?style=flat-square)
![board](https://img.shields.io/badge/GTR9%20Pro-v2.2-6f42c1?style=flat-square)
![bios](https://img.shields.io/badge/BIOS-GTRPRPI1001C-ed1c24?style=flat-square)
![firmware](https://img.shields.io/badge/firmware-AMI%20Aptio%20V-555?style=flat-square)
![settings](https://img.shields.io/badge/settings-1010-2563eb?style=flat-square)

Complete catalog of every BIOS Setup option exposed by the Beelink GTR9 Pro
(v2.2) UEFI firmware, decoded directly from the firmware image.

## Which revision do you have?

| Revision | NIC | BIOS series |
| --- | --- | --- |
| GTR9 Pro v1.0 | Intel E610-XT2 | `P###` |
| **GTR9 Pro v2.2** (this catalog) | Realtek RTL8127 | `PR##` / `GTRPRPI####` |

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

`GTRPRPI1001C` is `GTRPR05` plus a silicon-init (AGESA/PI) refresh. A PI/AGESA
update changes platform init code, not the Setup interface — all six
Setup-bearing modules are byte-identical (SHA-256) across `GTRPR07` and
`GTRPRPI1001C`, with identical HII string packages. Setting names, types,
ranges, NVRAM values, and defaults apply unchanged to both.

To read the AGESA version your unit is actually running:

```console
$ sudo dmidecode -t 40 | grep -i agesa
```

## Coverage

7 form-sets, 186 forms, **1,010** settings. 120 pages.

| Chapter | Form-set | Forms | Settings |
| --- | --- | ---: | ---: |
| Aptio Setup | Setup | 35 | 161 |
| AMD CBS | CbsSetupDxe | 51 | 318 |
| AMD PBS | AmdPbsSetupDxe | 14 | 202 |
| AMD Overclocking | AodDxe | 28 | 153 |
| AMD PMF | AmdCpmPmfBoardDxe | 28 | 139 |
| DASH / ASF | DashManagementDxe | 1 | 8 |
| RAIDXpert2 | RAID formset | 29 | 29 |

Generic UEFI network-stack forms (IPv4/IPv6/VLAN/HTTP/TLS/PXE) are contributed
by shared platform drivers rather than by this board's BIOS. They are listed in
Appendix A and are not counted above.

Rows sharing an option pattern but addressing distinct hardware or indices
(PCI-E `Device0`–`Device7`, the four CPU Smart Fan controllers, the eight
`PPC Adjustment` variants, the sixteen `APTS State Index` forms, the three
per-device Trusted Computing forms) are retained in full.

## Performance markers

Settings with a real performance dimension carry a red `■ performance` marker
with a recommended value for the Ryzen AI Max+ 395 and a one-line rationale,
beside the blue `■ default` factory marker.

| Tag | Meaning | Count |
| --- | --- | ---: |
| **CHANGE** | Change away from default for a clear gain | 4 |
| **TUNE** | Performance-relevant but workload-specific / expert-only | 371 |
| **KEEP** | Default already favors performance; leave it | 46 |

988 settings carry a compiled default marker; 421 carry a performance marker.

TUNE entries are validated starting points, not guaranteed-stable — record
originals before changing low-level CBS, AMD Overclocking, or PMF settings.

## Reading the document

- The PDF opens on its bookmark tree and carries a full table of contents;
  every chapter and form is a bookmark target.
- Each chapter is one firmware form-set; sub-sections are individual Setup
  pages in firmware presentation order.
- Tables are Setting / Type / Options-Values-Range. Bracketed values are raw
  NVRAM values (usable for AMISCE/SCEWIN scripting).
- Defaults shown are compiled Standard Defaults; a unit's live values may differ.
- Many options are conditionally hidden (suppress-if / grayout-if), so the
  catalog is a superset of what any single unit displays.
- A setting whose values span a page break repeats its name marked *(cont.)*.

## Notes on specific settings

- **`System Configuration`** (AMD CBS → SMU Common Options) is the platform
  cTDP profile. The compiled default is `120W [0x3]`; `140W [0x5]` is the
  highest profile the board exposes.
- **`UMA Frame buffer Size`** defaults to `96G [0x18000]`, which leaves roughly
  31 GiB visible to the OS on a 128 GB unit. Under Linux the Vulkan/RADV path
  uses GTT, so `512M [0x200]` restores the full pool to the OS without costing
  the iGPU memory.
- **`IOMMU`** disabled measures roughly 6% higher iGPU memory-read bandwidth,
  at the cost of VFIO/GPU passthrough, NPU access, and reliable suspend.
- **RAIDXpert2** forms enumerate up to 32 SATA physical disks and 32 arrays.
  This board exposes no SATA ports — the chapter is catalogued for completeness
  and its runtime-populated fields are annotated as such.

## Integrity (SHA256)

```
bd363c13a47ef5f72f7b1a83a281242c328234bd2ad549bf4968c5fba4bdd07c  GTR9Pro_BIOS_Settings.pdf
```
