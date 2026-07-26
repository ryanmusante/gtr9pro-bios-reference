# Changelog

## 1.6.5 - 2026-07-26

- pdf: rebuild renderer; table cells split across pages instead of
  overflowing, and the appendix no longer bleeds into the RAIDXpert2 forms.
- pdf: add table of contents; bookmark every chapter and form.
- pdf: embed all fonts as subsets; drop the unused base-14 reference.
- pdf: footer now carries page N of total. 106 -> 120 pages.
- cbs: System Configuration, Auto 0xF -> 0xFF; 0xF is 28W.
- cbs: STAPM Boost Override, correct inverted label/value mapping.
- setup: SM3_256 PCR Bank, Enabled 0x1 -> 0x10 per TCG algorithm registry.
- aod: retarget all 45 Curve Shaper rationales; the form is Zen 5 per-band
  V/F tuning, not fan or iGPU DPM control.
- cbs: NUMA Nodes rationale, Strix Halo is a chiplet part.
- cbs: Above 4GB MMIO Limit rationale described Above 4G Decoding.
- pbs: drop ASPM rationale from link-training, clock-gating and port-control
  settings; drop D3Cold rationale from lid, P3T and PME settings.
- pmf: drop AC/DC profile rationale from timer and Fake DC Level settings;
  drop STT rationale from PPT Limit for PMF APU Only.
- cbs: drop fan-curve rationale from Fan polarity, Pwm Frequency, Critical
  Temperature and Fan Table Index.
- cbs: System Configuration rationale now states the 120W default.
- cbs: IOMMU rationale now names the NPU and suspend cost.
- raid: annotate runtime-populated Select Controller and Array Size fields.
- Settings count 1,018 -> 1,010; eight appendix rows were miscounted as
  RAIDXpert2 settings. Tallies: 988 default; 421 performance
  (4 CHANGE / 371 TUNE / 46 KEEP).
- aod: Infinity Fabric Frequency and Dividers, repair duplicated heading.
- raid: merge split option labels in Select Array (0x220, 0x240).
- Rationales now name only options the setting actually offers: Core
  Performance Boost, OC Mode, Memory interleaving, Chip Select Interleaving,
  iGPU Configuration, STAPM Boost Override, Force PWM Control, SMT Control,
  Down Core Mode, GFX Curve Optimizer, Curve Optimizer.
- README: drop the PI version decode in favour of reading AGESA from
  dmidecode; add per-chapter form counts and a notes section.

## 1.6.4 - 2026-07-04

- README: correct Realtek NIC part number, RT8127 -> RTL8127.

## 1.6.3 - 2026-06-25

- Add /ToUnicode CMaps to all fonts. Rendering pixel-identical to 1.6.2.

## 1.6.2 - 2026-06-25

- Remove stray trailing period from View Array Properties heading (0x240).

## 1.6.1 - 2026-06-25

- Embed all fonts as subsets; add bookmarks, page labels, metadata; linearize.

## 1.6.0 - 2026-06-24

- Replace prose intro page with one-page legend. 106 pages.

## 1.5.2 - 2026-06-24

- README: add revision guide and BIOS download link.

## 1.5.1 - 2026-06-24

- Fix performance rationales mis-copied onto SATA/UFS/VGA/PS2 Support.
- Add default markers to ten previously-unmarked settings.

## 1.5.0 - 2026-06-24

- Set document of record to BIOS GTRPRPI1001C; re-derive against GTRPR07.

## 1.4.1 - 2026-06-24

- Correct tallies: 421 performance, 978 default.

## 1.4.0 - 2026-06-23

- Remove 35 duplicate rows; distinct-hardware rows retained. 113 -> 106 pages.

## 1.3.5 - 2026-06-19

- Drop performance marker from 603 rows with no performance dimension.

## 1.3.0 - 2026-06-19

- Render performance recommendations inline; three-column portrait layout.

## 1.2.1 - 2026-06-17

- Collapse runtime USB mass-storage dropdown to one row.

## 1.2.0 - 2026-06-15

- Add tiered performance recommendations with legend.

## 1.1.0 - 2026-06-15

- Add DASH/ASF and RAIDXpert2 chapters; Appendix A for excluded UEFI forms.

## 1.0.0 - 2026-06-15

- Initial catalog: 5 form-sets, 167 forms, 1,134 settings from GTRPR05.rom.
