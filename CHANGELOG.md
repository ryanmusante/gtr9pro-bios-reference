Changelog
=========


1.7.1 - 2026-08-15
------------------

  - pdf: rebuild all 68 Submenus lines from their item lists; 25 were
    glued or torn where separators had followed the old line breaks.
  - pdf: un-splice the AMD CBS (0x7000) submenu tail from its
    Information line; South Bridge keeps the bare goto token 17113.
  - cbs: restore the torn names STT_SKIN_TEMPERATURE_LIMIT_APU/_HS2;
    long identifier names now wrap at underscores.
  - setup: platform profile matches the live host - amd_iommu=on
    iommu=pt, NPU active; UMA row states recommendation vs live carve.
  - pmf: AC/DC profile rationales repunctuated; DC rows no longer
    instruct setting AC limits.
  - aod: GFX Curve Optimizer rationale de-duplicated; GPU Boost Clock
    Override drops the CPU-row (Positive) label.
  - aod: Scalar and Curve Shaper ranges use en dashes (1X-2X, 3-5).
  - cbs: PSPP rationale names only offered options; TjMax states the
    compiled 0x5A default beside AMD's 100 C rating.
  - cbs: MWAIT and pbs: Core Count rationales lead with the option
    label; setup: PSS Support scoped to the acpi-cpufreq fallback.
  - pdf: contents set two-column; it was 5 pages at 1.7.0, not the 2
    the note below claims; it is 2 now and the total is 44 pages.
  - pdf: DASH banner pluralizes by count (1 form); spelling
    standardized to American English; elision wording matches README.
  - pdf: verbatim-strings caveat added (firmware typos preserved).
  - pdf: LiberationSans is the canvas base font - no Helvetica object;
    page labels, language and keywords added to the catalog.
  - readme: Contents renamed Files; image-of-record header row;
    revision pattern GTRPRPI...; behaviour -> behavior; hash updated.
  - readme: lineage cites Beelink's published 1001C folder name.


1.7.0 - 2026-07-27
------------------

  - pdf: trim pass. Inline values, no per-form column headers, legend
    folded into the cover, contents 6 -> 2 pages. 120 -> 48 pages.
  - pdf: rationales cut to whole sentences, mean 158 -> 109 chars; the
    recommended option is lifted to the front where trimming would
    otherwise drop it (67 rows).
  - pdf: enumerations of 12 or more collapse to the default plus first
    and last option and a count; largest 57 -> 2.
  - pdf: 17 forms whose table is byte-identical to an earlier sibling
    are cross-referenced. 918 rows printed, all 1,010 settings counted.
  - raid: 0x320, 0x321 and 0x322 submenu lines had absorbed page
    headers, page numbers and the Appendix A table. Repaired.
  - raid: Select Array and Select Physical Disk runtime filler collapse
    to one range row each, from 64 and 32 rows.
  - setup: strip trailing marker glyphs from Secure Boot info fields.
  - aod: PPT Limit separates the AMD cTDP range 45-120 W from Beelink's
    validated 140 W chassis ceiling; value is mW.
  - aod: PBO and Curve Optimizer noted as supported on the non-PRO 395
    and fused off on the PRO SKU.
  - cbs: UMA Frame buffer Size TUNE -> CHANGE, 512M under Linux.
  - cbs: IOMMU cites the 234 vs 221 GB/s read delta and the KVM/VFIO
    cost.
  - cbs: SVM Enable TUNE -> KEEP, required for KVM.
  - setup: ACPI Sleep State, Secure Boot, Network Stack and Onboard
    PCIE LAN PXE ROM gain performance markers.
  - Tallies: 425 performance (5 CHANGE / 372 TUNE / 48 KEEP); 988
    default.
  - README: add Elisions and Platform profile sections.
  - CHANGELOG: reformat to kernel.org style.


1.6.5 - 2026-07-26
------------------

  - pdf: rebuild renderer; cells split across pages instead of
    overflowing, appendix no longer bleeds into the RAIDXpert2 forms.
  - pdf: add table of contents; bookmark every chapter and form.
  - pdf: embed all fonts as subsets; drop the base-14 reference.
  - pdf: footer carries page N of total. 106 -> 120 pages.
  - cbs: System Configuration, Auto 0xF -> 0xFF; 0xF is 28W.
  - cbs: STAPM Boost Override, correct inverted label/value mapping.
  - setup: SM3_256 PCR Bank, Enabled 0x1 -> 0x10 per TCG registry.
  - aod: retarget all 45 Curve Shaper rationales; the form is Zen 5
    per-band V/F tuning, not fan or iGPU DPM control.
  - cbs: NUMA Nodes rationale, Strix Halo is a chiplet part.
  - cbs: Above 4GB MMIO Limit rationale described Above 4G Decoding.
  - pbs: drop ASPM rationale from link-training, clock-gating and
    port-control rows; drop D3Cold from lid, P3T and PME rows.
  - pmf: drop AC/DC profile rationale from timer and Fake DC Level;
    drop STT from PPT Limit for PMF APU Only.
  - cbs: drop fan-curve rationale from Fan polarity, Pwm Frequency,
    Critical Temperature and Fan Table Index.
  - cbs: System Configuration rationale states the 120W default.
  - cbs: IOMMU rationale names the NPU and suspend cost.
  - raid: annotate runtime-populated Select Controller and Array Size.
  - Settings 1,018 -> 1,010; eight appendix rows were miscounted as
    RAIDXpert2 settings. Tallies: 988 default; 421 performance
    (4 CHANGE / 371 TUNE / 46 KEEP).
  - aod: Infinity Fabric Frequency and Dividers, repair duplicated
    heading.
  - raid: merge split option labels in Select Array (0x220, 0x240).
  - Rationales name only options the setting offers: Core Performance
    Boost, OC Mode, Memory interleaving, Chip Select Interleaving, iGPU
    Configuration, STAPM Boost Override, Force PWM Control, SMT
    Control, Down Core Mode, GFX Curve Optimizer, Curve Optimizer.
  - README: read AGESA from dmidecode instead of decoding the PI
    version; add per-chapter form counts and a notes section.


1.6.4 - 2026-07-04
------------------

  - README: correct Realtek NIC part number, RT8127 -> RTL8127.


1.6.3 - 2026-06-25
------------------

  - Add /ToUnicode CMaps to all fonts. Rendering pixel-identical to
    1.6.2.


1.6.2 - 2026-06-25
------------------

  - Remove stray trailing period from View Array Properties (0x240).


1.6.1 - 2026-06-25
------------------

  - Embed all fonts as subsets; add bookmarks, page labels, metadata;
    linearize.


1.6.0 - 2026-06-24
------------------

  - Replace prose intro page with one-page legend. 106 pages.


1.5.2 - 2026-06-24
------------------

  - README: add revision guide and BIOS download link.


1.5.1 - 2026-06-24
------------------

  - Fix performance rationales mis-copied onto SATA/UFS/VGA/PS2
    Support.
  - Add default markers to ten previously-unmarked settings.


1.5.0 - 2026-06-24
------------------

  - Set document of record to BIOS GTRPRPI1001C; re-derive against
    GTRPR07.


1.4.1 - 2026-06-24
------------------

  - Correct tallies: 421 performance, 978 default.


1.4.0 - 2026-06-23
------------------

  - Remove 35 duplicate rows; distinct-hardware rows retained.
    113 -> 106 pages.


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
