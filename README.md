# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![doc](https://img.shields.io/badge/doc-1.7.1-1793d1?style=flat-square)

Complete catalog of every BIOS Setup option exposed by the Beelink GTR9 Pro
(v2.2) UEFI firmware, decoded directly from the firmware image.

## Which revision do you have?

| Revision | NIC | BIOS series |
| --- | --- | --- |
| GTR9 Pro v1.0 | Intel E610-XT2 | `P###` |
| **GTR9 Pro v2.2** (this catalog) | Realtek RTL8127 | `GTRPR##` / `GTRPRPI…` |

Identify yours by NIC chipset or current BIOS series.
BIOS downloads: https://dr.bee-link.cn/?dir=uploads%2FGTR%2FGTR9-395%2FBIOS

## Files

| File | Purpose |
| --- | --- |
| `GTR9Pro_BIOS_Settings.pdf` | Reference document |
| `README.md` | This file |
| `CHANGELOG.md` | Version history |

## Image of record

| Field | Value |
| --- | --- |
| Board | Beelink GTR9 Pro **v2.2** |
| BIOS | **GTRPRPI1001C** (32 MB) |
| Prior image | `GTRPR07` (identical Setup interface) |
| BIOS vendor | AMI Aptio V |
| SoC | AMD Strix Halo (Ryzen AI Max+ 395) |

`GTRPRPI1001C` is a Secure Boot key + AGESA/PI refresh of the `GTRPR0X`
line — Beelink's folder for it is named
`GTR9-Version2-GTRPRPI1001C_Note-secure-boot-update-AMD-AGESA-only-GTRPR0X-can-flash`
([Beelink forum, 2026-05-30](https://bbs.bee-link.com/d/11236-gtr9-pro-ryzen-ai-max-395-128gb-need-help-identifying-bios-update)). A PI/AGESA
update changes platform init code, not the Setup interface — all six
Setup-bearing modules are byte-identical (SHA-256) across `GTRPR07` and
`GTRPRPI1001C`, with identical HII string packages. Setting names, types,
ranges, NVRAM values, and defaults apply unchanged to both.

To read the AGESA version your unit is actually running:

```console
$ sudo dmidecode -t 40 | grep -i agesa
```

## Coverage

7 form-sets, 186 forms, **1,010** settings. 44 pages.

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

## Elisions

Every setting is counted; the document prints 918 rows because two classes of
repetition are elided.

| Class | Rule |
| --- | --- |
| Long enumerations | 12 or more options collapse to the default plus first/last option and a count |
| Identical sibling forms | 17 forms byte-identical to an earlier sibling are cross-referenced, not reprinted |

The cross-referenced forms are APTS State Index 1–15,
`Select Physical Disks 0x211`, and `Select Physical Disk Operations 0x320`.

Rows sharing an option pattern but addressing distinct hardware or indices
(PCI-E `Device0`–`Device7`, the four CPU Smart Fan controllers, the eight
`PPC Adjustment` variants, the three per-device Trusted Computing forms) are
retained in full.

## Performance markers

Settings with a real performance dimension carry a red `■ performance` marker
with a recommended value for the Ryzen AI Max+ 395 and a one-line rationale,
beside the blue `■ default` factory marker.

| Tag | Meaning | Count |
| --- | --- | ---: |
| **CHANGE** | Change away from default for a clear gain | 5 |
| **TUNE** | Performance-relevant but workload-specific / expert-only | 372 |
| **KEEP** | Default already favors performance; leave it | 48 |

988 settings carry a compiled default marker; 425 carry a performance marker.

Rationales are one line and lead with the recommended value wherever the
setting has one; the remainder states why.

TUNE entries are validated starting points, not guaranteed-stable — record
originals before changing low-level CBS, AMD Overclocking, or PMF settings.

## Platform profile

Recommendations assume a CachyOS host configured by `ry-install` (7.162
line). Where firmware and kernel govern the same behavior, the kernel setting
wins at runtime and the firmware row is redundant rather than wrong.

| Firmware area | Host interaction |
| --- | --- |
| CBS → NBIO → `IOMMU` | Host boots `amd_iommu=on iommu=pt`; keep firmware Enabled — NPU, KVM/VFIO and DMA isolation depend on it |
| `UMA Frame buffer Size` | Recommendation `512M` (RADV/ROCm use GTT); host currently runs a `32G` carve, ≈47 GiB GTT |
| S3 / D3Cold / wake-source rows | All systemd sleep targets are masked; no runtime effect |
| NPU (XDNA) rows | `amdxdna` loads and the NPU is active; NPU-gated rows are live |
| PCIe ASPM rows | `pcie_aspm.policy=performance` overrides per-port firmware policy |
| `Global C-state Control` | Firmware twin of `processor.max_cstate=1` |
| Network Stack / PXE | Disabled in firmware; boot path is systemd-boot with no UEFI network stack |

## Reading the document

- The PDF opens on its bookmark tree and carries a table of contents; every
  chapter and form is a bookmark target.
- Each chapter is one firmware form-set; sub-sections are individual Setup
  pages in firmware presentation order.
- Tables are Setting / Type / Values. Options are separated by `·`; bracketed
  values are raw NVRAM values (usable for AMISCE/SCEWIN scripting).
- Defaults shown are compiled Standard Defaults; a unit's live values may
  differ.
- Option and setting strings are reproduced verbatim, firmware typos included
  (`USB4 D3 Eanble`, `USBC Port Harware Disable`, `Minimun Frequency`, …).
- Many options are conditionally hidden (suppress-if / grayout-if), so the
  catalog is a superset of what any single unit displays.

## Notes on specific settings

- **`System Configuration`** (AMD CBS → SMU Common Options) is the platform
  cTDP profile. The compiled default is `120W [0x3]`; `140W [0x5]` is the
  highest profile the board exposes. AMD rates this part at cTDP 45–120 W;
  the 140 W figure is Beelink's own validated chassis ceiling.
- **`Precision Boost Overdrive`** and **`Curve Optimizer`** are supported on
  the Ryzen AI Max+ 395; the PRO variant of the same silicon has both fused
  off, so guidance written for PRO parts does not apply here.
- **`UMA Frame buffer Size`** defaults to `96G [0x18000]`, which leaves roughly
  31 GiB visible to the OS on a 128 GB unit. Under Linux the Vulkan/RADV and
  ROCm paths use GTT, so `512M [0x200]` restores the full pool to the OS
  without costing the iGPU memory.
- **`IOMMU`** disabled measures roughly 6% higher iGPU memory-read bandwidth
  (234 vs 221 GB/s, community strix-halo-testing runs by lhl), at the cost of
  VFIO/GPU passthrough, NPU access, DMA isolation, and reliable suspend.
- **`TjMax`** prints its compiled default `0x5A`; AMD's rated Tjmax for the
  395 is 100 °C. The document leaves the compiled value as extracted.
- **RAIDXpert2** forms enumerate up to 32 SATA physical disks and 32 arrays.
  This board exposes no SATA ports — the chapter is catalogued for completeness
  and its runtime-populated fields are annotated as such.

## Integrity (SHA256)

```
2d4ea699640bdbc1f68704d4ddbc2d712cca71d858e46068d8636e3233ef7753  GTR9Pro_BIOS_Settings.pdf
```
