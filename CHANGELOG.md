Changelog
=========


1.7.4 - 2026-09-03
------------------

  - readme, changelog: trimmed to vital information. Catalog unchanged.


1.7.3 - 2026-09-02
------------------

  - setup: PPC Adjustment x8 TUNE -> KEEP; _PPC only caps the OS
    P-state ceiling and the default already leaves boost open.
  - Rationales corrected where they named options a row does not offer
    (Smart Fan 3 Mode, Prefetcher x3, PCIe x4 Slot D3 Cold),
    contradicted the printed default (Thermal Control, Dynamic P3T
    limit, LCLK Maximum Frequency) or carried mis-copied text (DC
    Battery Saver Limit, Discrete GPU D3Cold HPD Support, D3Cold Force
    Gen1, fan-curve rows).
  - cbs: Accept (0x7011) drops a Submenus line belonging to Accept
    (0x7023). Stray separators removed from Mass Storage Device
    Emulation Type and APU PROCHOT# setting.
  - Tallies: 425 performance (5 CHANGE / 365 TUNE / 55 KEEP); 988
    default.


1.7.2 - 2026-08-29
------------------

  - setup: platform profile drops amd_iommu=on (inert; iommu=pt is
    load-bearing); anchored to ry-install 7.164+.
  - cbs: Corrector Branch Predictor KEEP -> TUNE (compiled default
    Disable, no Auto option). Spurious (Auto) dropped from REP-MOV/STOS
    Streaming and pbs ACP Power Gating.
  - Tallies: 425 performance (5 CHANGE / 373 TUNE / 47 KEEP).


1.7.1 - 2026-08-15
------------------

  - pdf: Submenus lines rebuilt from item lists (25 were glued or
    torn); torn STT_SKIN_TEMPERATURE_LIMIT names restored; contents
    two-column, 44 pages; LiberationSans base font, page labels,
    language and keywords in the catalog; American English.
  - Rationales: DC rows no longer instruct setting AC limits; PSPP and
    MWAIT name only offered options; TjMax states the compiled 0x5A
    beside AMD's 100 C rating; en dashes for ranges.
  - readme: image-of-record header; lineage cites Beelink's 1001C
    folder.


1.7.0 - 2026-07-27
------------------

  - pdf: trim pass. Inline values, legend on the cover, 120 -> 48
    pages; rationales cut to one sentence (mean 158 -> 109 chars)
    leading with the recommended option.
  - Enumerations of 12 or more collapse to default plus first/last and
    a count; 17 byte-identical sibling forms cross-referenced. 918 rows
    printed, 1,010 settings counted.
  - raid: submenu lines had absorbed page headers and the Appendix A
    table; runtime filler collapsed to one range row each.
  - cbs: UMA Frame buffer Size TUNE -> CHANGE (512M under Linux); SVM
    Enable TUNE -> KEEP; IOMMU cites the 234 vs 221 GB/s delta. aod:
    PPT Limit separates AMD's 45-120 W cTDP from Beelink's 140 W
    ceiling; PBO/CO noted supported on the non-PRO 395.
  - Tallies: 425 performance (5 CHANGE / 372 TUNE / 48 KEEP); 988
    default. README gains Elisions and Platform profile; CHANGELOG in
    kernel.org style.


1.6.5 - 2026-07-26
------------------

  - pdf: renderer rebuilt (no cell overflow), table of contents and
    bookmarks, subset fonts, page N of total. 106 -> 120 pages.
  - Value fixes: System Configuration Auto 0xF -> 0xFF; STAPM Boost
    Override label/value mapping; SM3_256 PCR Bank 0x1 -> 0x10.
  - Rationales retargeted or dropped where they described another
    setting (45 Curve Shaper rows, NUMA Nodes, Above 4GB MMIO Limit,
    ASPM/D3Cold/AC-DC/fan-curve carry-overs); rationales name only
    options the setting offers.
  - Settings 1,018 -> 1,010 (appendix rows miscounted). Tallies: 988
    default; 421 performance (4 CHANGE / 371 TUNE / 46 KEEP).


1.6.4 - 2026-07-04
------------------

  - README: Realtek NIC part number RT8127 -> RTL8127.


1.6.3 - 2026-06-25
------------------

  - Add /ToUnicode CMaps to all fonts; rendering unchanged.


1.6.2 - 2026-06-25
------------------

  - Remove stray trailing period from View Array Properties (0x240).


1.6.1 - 2026-06-25
------------------

  - Embed fonts as subsets; add bookmarks, page labels, metadata;
    linearize.


1.6.0 - 2026-06-24
------------------

  - Replace prose intro page with a one-page legend. 106 pages.


1.5.2 - 2026-06-24
------------------

  - README: revision guide and BIOS download link.


1.5.1 - 2026-06-24
------------------

  - Fix rationales mis-copied onto SATA/UFS/VGA/PS2 Support; default
    markers added to ten settings.


1.5.0 - 2026-06-24
------------------

  - Document of record set to BIOS GTRPRPI1001C; re-derived against
    GTRPR07.


1.4.1 - 2026-06-24
------------------

  - Correct tallies: 421 performance, 978 default.


1.4.0 - 2026-06-23
------------------

  - Remove 35 duplicate rows; distinct-hardware rows retained. 113 ->
    106 pages.


1.3.5 - 2026-06-19
------------------

  - Drop performance marker from 603 rows with no performance
    dimension.


1.3.0 - 2026-06-19
------------------

  - Render performance recommendations inline; three-column portrait
    layout.


1.2.1 - 2026-06-17
------------------

  - Collapse runtime USB mass-storage dropdown to one row.


1.2.0 - 2026-06-15
------------------

  - Add tiered performance recommendations with legend.


1.1.0 - 2026-06-15
------------------

  - Add DASH/ASF and RAIDXpert2 chapters; Appendix A for excluded UEFI
    forms.


1.0.0 - 2026-06-15
------------------

  - Initial catalog: 5 form-sets, 167 forms, 1,134 settings from
    GTRPR05.rom.
