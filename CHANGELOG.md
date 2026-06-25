# Changelog

## 1.5.2 - 2026-06-24

- README: added "Which revision do you have?" section (v1.0 Intel E610-XT2 /
  `P###` vs v2.2 Realtek RT8127 / `PR##`) and the Beelink BIOS download link.
- Documentation-only; PDF unchanged from 1.5.1 (SHA256 83bf8f71…).

## 1.5.1 - 2026-06-24

- Marker accuracy pass; no settings, types, values, or ranges changed.
- Fixed performance rationales copy-pasted from **NVMe Support** onto four
  unrelated settings — **SATA Support** (boot-time enumeration scope),
  **UFS Support**, **VGA Support** (VBIOS/GOP init policy), **PS2 Devices
  Support**. NVMe Support rationale unchanged.
- Added `◀ default` to ten settings whose exposed Standard default was unmarked:
  SHA-1/SHA384/SHA512/SM3_256 PCR Bank (Disabled), SHA256 PCR Bank (Enabled),
  XHCI Hand-off (Enabled), Secure Boot (Disabled), Secure Boot Mode (Custom),
  Password protection of Runtime Variables (Enabled), SATA Support.
- Tallies: 988 default (+10); 421 performance (4 CHANGE / 375 TUNE / 42 KEEP).
- SHA256 -> 83bf8f716f81db007b1f34adf1fdd5441b697ad8f207a4357e74cb0c8d0523e5.

## 1.5.0 - 2026-06-24

- Set document of record to GTR9 Pro v2.2 latest BIOS `GTRPRPI1001C`; running
  header, page-1 subtitle, and BIOS Version field updated accordingly.
- Re-derived against `GTRPRPI1001C` and `GTRPR07` (both 32 MB), replacing
  `GTRPR05`. Body unchanged: 7 form-sets, 186 forms, 1,018 settings.
- Verified Setup interface identical across images: all six Setup-bearing PE32
  modules byte-identical (SHA-256), HII string packages identical.
- `GTRPRPI1001C` = `GTRPR05` + `PI 1.0.0c1` (AGESA/PI refresh); no Setup-option
  changes.
- SHA256 -> 229fa7666721d4965637ef50f98031e18a1f7a76f04d85e90bf5e84996e97f22.

## 1.4.1 - 2026-06-24

- Corrected marker tallies of record: 421 performance (4 CHANGE / 375 TUNE /
  42 KEEP) and 978 default; both self-consistent with the 1.4.0 de-dup delta.
- Prior PDF (releases 1.3.8–1.3.11) carried 442 performance / 1,005 default; the
  1.3.11 recount to 446/1,004 and the 1.3.7 figure of 1,006 default were
  erroneous. 1.3.5/1.3.9 figures reaffirmed.
- PDF unchanged; SHA256 a703615b9273aea31d71d6ecc8dd40a47284e1d2646d249e6c6e2494086c46b1.

## 1.4.0 - 2026-06-23

- Removed 35 verbatim-duplicate rows: Smart Fan Function (0x2737) 21, View
  Associated Physical Disks (0x222) 8, Display Configurations (0x10) 4, Trusted
  Computing (0x271A) 2. One canonical row kept each.
- Settings: 1,053 − 35 = 1,018. Distinct-hardware rows (PCI-E Device0–Device7,
  four CPU Smart Fan controllers, eight PPC Adjustment variants, three Trusted
  Computing form variants) retained.
- Per-chapter: Aptio 184 -> 161, AMD PBS 206 -> 202, RAIDXpert2 37.
- Marker totals dropped 27 default and 21 performance (all TUNE).
- PDF regenerated; 113 -> 106 pages.
- SHA256 -> a703615b9273aea31d71d6ecc8dd40a47284e1d2646d249e6c6e2494086c46b1.

## 1.3.11 - 2026-06-23

- Corrected performance total to 446 (later superseded by 1.4.1); PDF unchanged.

## 1.3.10 - 2026-06-23

- Format changelog as Markdown lists; PDF unchanged.

## 1.3.9 - 2026-06-23

- Shade each marker line in its marker color (blue ◀ default, red ◀ performance).
- SHA256 -> 41abf78997ffea37e89a905ef5efbd458e13a2bb716cb1c8dfb7cb80a3d86da9.

## 1.3.8 - 2026-06-23

- Fixed corrupt document (removed duplicate Heading1/2/3 styleIds); converted
  deliverable to PDF, dropped Word source.
- SHA256 -> 9f20e029be8b16b9cb1d0550097b872e083f8b9d7ce878fd030ab5cda02e6166.

## 1.3.7 - 2026-06-22

- Trimmed front-matter prose; rewrote README in GitHub style.

## 1.3.6 - 2026-06-22

- Removed orphan comments rels part.

## 1.3.5 - 2026-06-19

- Dropped performance marker from 603 rows with no performance dimension;
  138 -> 113 pages.

## 1.3.4 - 2026-06-19

- Added default markers to 18 Selection rows the extraction missed.

## 1.3.3 - 2026-06-19

- Appended default marker to 348 numeric rows missing one.

## 1.3.2 - 2026-06-19

- Adjusted marker colors: default blue (2563EB), performance red (D50000).

## 1.3.1 - 2026-06-19

- Standardized marker colors. Superseded by 1.3.2.

## 1.3.0 - 2026-06-19

- Rendered performance recommendations inline at foot of Options cell; narrowed
  tables to three columns, portrait US Letter.

## 1.2.3 - 2026-06-19

- Fixed blank footer page numbers; normalized performance-note separators.

## 1.2.2 - 2026-06-17

- Fixed two performance notes with wrong opening quote.

## 1.2.1 - 2026-06-17

- Collapsed runtime USB mass-storage dropdown to one row; 1,074 -> 1,045.

## 1.2.0 - 2026-06-15

- Added tiered performance recommendations with derivation section and legend.

## 1.1.0 - 2026-06-15

- Added DASH/ASF (8) and RAIDXpert2 (37) chapters; Appendix A for excluded
  generic UEFI network forms. 5 -> 7 form-sets, 167 -> 186 forms.

## 1.0.0 - 2026-06-15

- Initial catalog: 5 form-sets, 167 forms, 1,134 settings, decoded from
  `GTRPR05.rom`.
