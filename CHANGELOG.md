# Changelog

## 1.6.1 - 2026-06-25

- Embedded all fonts (Helvetica, Helvetica-Bold, ZapfDingbats) as subsets for
  print fidelity and portability; page layout byte-identical to 1.6.0.
- Added document structure: form-set bookmarks, page labels, document language
  (en-US), viewer preferences, and document title/metadata.
- Linearized for faster web viewing. No settings, types, values, ranges, or
  markers changed.
- SHA256 -> 639371ab19c16c1ef22d37a2d2cb3e0f01cba21a4ea4f50b736bf2585335fa52.

## 1.6.0 - 2026-06-24

- Replaced the prose "About This Document" page with a compact one-page legend
  (layout, Type column, values, markers, tier tags). Settings unchanged.
- 106 pages; settings pages byte-identical to 1.5.2 (988 default / 421
  performance markers; 186 forms; 1,018 settings).
- SHA256 -> 120ebc2f7ccdd92cb965e8fba128a3516d7381318b525ae0688e436ba41198b1.

## 1.5.2 - 2026-06-24

- README: added "Which revision do you have?" section and BIOS download link.
  Documentation-only; PDF unchanged.

## 1.5.1 - 2026-06-24

- Marker accuracy pass. Fixed performance rationales mis-copied from NVMe
  Support onto SATA/UFS/VGA/PS2 Support; added default markers to ten settings
  whose Standard default was unmarked.
- Tallies: 988 default; 421 performance (4 CHANGE / 375 TUNE / 42 KEEP).

## 1.5.0 - 2026-06-24

- Set document of record to GTR9 Pro v2.2 BIOS `GTRPRPI1001C`; re-derived
  against `GTRPRPI1001C` and `GTRPR07` (both 32 MB), replacing `GTRPR05`.
- Setup interface verified identical across images (six Setup-bearing modules
  byte-identical, HII string packages identical). Body unchanged: 7 form-sets,
  186 forms, 1,018 settings.

## 1.4.1 - 2026-06-24

- Corrected marker tallies of record: 421 performance (4 CHANGE / 375 TUNE /
  42 KEEP) and 978 default.

## 1.4.0 - 2026-06-23

- Removed 35 verbatim-duplicate rows (one canonical row kept each); distinct-
  hardware rows retained. Settings: 1,053 − 35 = 1,018.
- Per-chapter: Aptio 184 -> 161, AMD PBS 206 -> 202, RAIDXpert2 37.
- PDF regenerated; 113 -> 106 pages.

## 1.3.5 - 2026-06-19

- Dropped performance marker from 603 rows with no performance dimension;
  138 -> 113 pages.

## 1.3.0 - 2026-06-19

- Rendered performance recommendations inline at foot of Options cell; narrowed
  tables to three columns, portrait US Letter.

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
