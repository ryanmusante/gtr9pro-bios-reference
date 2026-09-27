# Beelink GTR9 Pro — UEFI BIOS Setup Reference

![doc](https://img.shields.io/badge/doc-1.7.8-1793d1?style=flat-square)

Every BIOS Setup option exposed by the Beelink GTR9 Pro (v2.2) UEFI firmware,
decoded from the firmware image.

## Which revision do you have?

| Revision | NIC | BIOS series |
| --- | --- | --- |
| GTR9 Pro v1.0 | Intel E610-XT2 | `P###` |
| **GTR9 Pro v2.2** (this catalog) | Realtek RTL8127 | `GTRPR##` / `GTRPRPI…` |

BIOS downloads: https://dr.bee-link.cn/?dir=uploads%2FGTR%2FGTR9-395%2FBIOS

## Image of record

| Field | Value |
| --- | --- |
| Board | Beelink GTR9 Pro **v2.2** |
| BIOS | **GTRPRPI1001C** (32 MB) |
| Prior image | `GTRPR07` (identical Setup interface) |
| BIOS vendor | AMI Aptio V |
| SoC | AMD Strix Halo (Ryzen AI Max+ 395) |

`GTRPRPI1001C` is a Secure Boot key + AGESA/PI refresh of the `GTRPR0X` line;
its six Setup-bearing modules are byte-identical (SHA-256) to `GTRPR07`, so
setting names, types, ranges, NVRAM values and defaults apply to both.

## Coverage

7 form-sets, 186 forms, **1,010** settings, 46 pages.

| Chapter | Form-set | Forms | Settings |
| --- | --- | ---: | ---: |
| Aptio Setup | Setup | 35 | 161 |
| AMD CBS | CbsSetupDxe | 51 | 318 |
| AMD PBS | AmdPbsSetupDxe | 14 | 202 |
| AMD Overclocking | AodDxe | 28 | 153 |
| AMD PMF | AmdCpmPmfBoardDxe | 28 | 139 |
| DASH / ASF | DashManagementDxe | 1 | 8 |
| RAIDXpert2 | RAID formset | 29 | 29 |

Generic UEFI network-stack forms (IPv4/IPv6/VLAN/HTTP/TLS/PXE) and the four
Setup-referenced driver formsets (Super IO Configuration, SIO Common Setting,
PCI Subsystem Settings, NVMe Configuration) come from shared drivers, not this
board's Setup modules; they are listed in Appendix A and not counted. Action,
confirmation and runtime-generated prompts (BBS boot priorities, Secure Boot
key management, RAID dialogs, firmware-update flow, Save & Exit) have no
catalog entry.

918 rows are printed: 17 forms byte-identical to an earlier sibling
(APTS State Index 1–15, `Select Physical Disks (0x211)`,
`Select Physical Disk Operations (0x320)`) are cross-referenced, not
reprinted. Enumerations of 12 or more options collapse to the default plus
first/last option and the total option count.

## Performance markers

Settings with a real performance dimension carry a red `■` marker with a
recommended value for the Ryzen AI Max+ 395 and a short rationale, beside
the blue `■` compiled-default marker. Rows without a red marker have no
performance dimension — including safety limits and rows inert on this board;
leave them at default.

| Tag | Meaning | Count |
| --- | --- | ---: |
| **CHANGE** | Change away from default for a clear gain | 5 |
| **TUNE** | Performance-relevant but workload-specific / expert-only | 384 |
| **KEEP** | Default already favors performance; leave it | 48 |

988 settings carry a default marker; 437 carry a performance marker. TUNE
entries are starting points, not guaranteed-stable — record originals before
changing CBS, AMD Overclocking or PMF settings.

## Platform profile

Recommendations assume a CachyOS host configured by `ry-install` (7.164+).
Where kernel and firmware govern the same behavior, the kernel setting wins at
runtime.

| Firmware area | Host interaction |
| --- | --- |
| CBS → NBIO → `IOMMU` | Host boots `iommu=pt`; keep the firmware default `Auto` (resolves Enabled) — NPU, KVM/VFIO passthrough and DMA isolation depend on it |
| `UMA Frame buffer Size` | Recommendation `512M` (RADV/ROCm use GTT); host runs a `32G` carve by choice; from `ry-install` 7.217.0 GTT stays at the kernel default (≈47 GiB, measured 2026-08-14) |
| S3 / wake-source rows | All systemd sleep targets are masked; no runtime effect |
| D3 / D3Cold rows | Still gate device idle at runtime; the wake-latency cost is marginal |
| NPU (XDNA) rows | `amdxdna` loads; NPU-gated rows are live |
| PCIe link-PM rows (ASPM, L1 substates, Clock PM) | `pcie_aspm.policy=performance` overrides per-port firmware policy |
| `Global C-state Control` | Firmware twin of `processor.max_cstate=1` |
| Network Stack / PXE | Disabled in firmware; systemd-boot, no UEFI network path |

## Reading the document

- Tables are Setting / Type / Values; options are separated by `·` and
  bracketed values are raw NVRAM values (AMISCE/SCEWIN scripting).
- Defaults are compiled Standard Defaults; live values may differ.
- Gray `Submenus` lines list every goto prompt on a form, including prompts
  whose target has no catalog entry; `Information fields` lines are read-only
  text rows.
- Strings are verbatim, firmware typos included (`USB4 D3 Eanble`,
  `USBC Port Harware Disable Support`, `Minimun Frequency`, …).
- Many options are suppress-if / grayout-if hidden; the catalog is a superset
  of any one unit's display.

## Notes on specific settings

- **`System Configuration`** (CBS → SMU Common Options) is the cTDP profile:
  default `120W [0x3]`, highest exposed `140W [0x5]`. AMD rates 45–120 W;
  140 W is Beelink's validated chassis ceiling.
- **`Precision Boost Overdrive`** and **`Curve Optimizer`** are supported on
  the Ryzen AI Max+ 395; the PRO variant has both fused off.
- **`UMA Frame buffer Size`** defaults to `96G [0x18000]`, leaving ~31 GiB to
  the OS on a 128 GB unit; RADV and ROCm use GTT, so `512M [0x200]` restores
  the pool without costing the iGPU.
- **`IOMMU`** disabled measures ~6% higher iGPU memory read (234 vs 221 GB/s,
  community strix-halo-testing runs by lhl) at the cost of VFIO passthrough,
  NPU access, DMA isolation and reliable suspend.
- **`TjMax`** prints its compiled default `0x5A`; AMD's rated Tjmax for the
  395 is 100 °C.
- **RAIDXpert2** enumerates up to 32 SATA disks and 32 arrays; this board has
  no SATA ports — cataloged for completeness, runtime fields annotated.

## Integrity (SHA256)

```
3757a1482f51175e592474f3285761be57f9826a13212701820c738e1ccdb307  GTR9Pro_BIOS_Settings.pdf
```
