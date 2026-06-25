# Changelog

## 1.4.1 - 2026-06-24

- Correct the performance/default marker tallies of record. The shipped PDF
  (SHA256 a703615b9273aea31d71d6ecc8dd40a47284e1d2646d249e6c6e2494086c46b1)
  carries 421 performance markers (4 CHANGE / 375 TUNE / 42 KEEP) and 978
  default markers. Both are self-consistent with the catalog (421 performance
  lines == 421 tier tags) and with the 1.4.0 de-duplication delta below
  (-21 TUNE performance, -27 default).
- The immediately prior PDF (SHA256 41abf78997ffea37e89a905ef5efbd458e13a2bb716cb1c8dfb7cb80a3d86da9,
  releases 1.3.8 through 1.3.11) carried 442 performance markers
  (4 CHANGE / 396 TUNE / 42 KEEP) and 1,005 default markers. The 1.3.11 recount
  to 446 performance (5 / 398 / 43), 1,004 default, and 1,450 total markers was
  erroneous, as was the 1,006 default figure in 1.3.7. The 1.3.5 and 1.3.9
  figures (442 = 4 / 396 / 42 performance, 1,005 default) were correct and are
  reaffirmed here; the 1.4.0 marker delta (27 default + 21 all-TUNE performance
  dropped) was also correct.
- PDF unchanged; SHA256 a703615b9273aea31d71d6ecc8dd40a47284e1d2646d249e6c6e2494086c46b1
  preserved. Changelog/README-only correction; README version badge -> 1.4.1.

## 1.4.0 - 2026-06-23

- Remove 35 verbatim-duplicate option rows the IFR extraction emitted more
  than once within a single form (identical setting name, type, and values).
  One canonical row kept per duplicate. Removals: Smart Fan Function (0x2737)
  21, View Associated Physical Disks (0x222) 8, Display Configurations (0x10)
  4, Trusted Computing (0x271A) 2.
- Settings total: the shipped firmware tables held 1,053 option rows; removing
  the 35 duplicates leaves 1,018. The 1,045 quoted in prose since 1.2.1 had
  already deducted the 8 duplicate View Associated Physical Disks rows from the
  count without removing them from the tables; 1,045 minus the remaining 27
  duplicates is the same 1,018.
- Only byte-identical repeats removed. Distinct-hardware rows that share an
  option pattern are retained: PCI-E Port Device0-Device7 and their per-device
  ASPM/Hotplug controls, the four CPU Smart Fan controllers, the eight
  PPC Adjustment P-state-count variants, and the three per-device Trusted
  Computing form variants (0x2719 / 0x271A / 0x271B).
- Per-chapter settings: Aptio Setup 184 -> 161 (Smart Fan 21 + Trusted
  Computing 2), AMD PBS 206 -> 202 (Display Configurations 4); RAIDXpert2
  stays 37 in prose (tables 45 -> 37 once the 8 VAP duplicates are dropped);
  AMD CBS, AOD, PMF, DASH/ASF unchanged.
- Marker totals follow the removed rows: 27 default and 21 performance (all
  TUNE) markers dropped.
- PDF regenerated from the shipped document's tagged table structure (markers,
  tier tags, and per-line shading reproduced; 113 -> 106 pages from the smaller
  row set; Page N of M fields repopulated).
- README settings badge and coverage table updated to 1,018; de-duplication
  section added.
- SHA256 -> a703615b9273aea31d71d6ecc8dd40a47284e1d2646d249e6c6e2494086c46b1.

## 1.3.11 - 2026-06-23

- Correct performance-marker total of record: the shipped PDF carries 446
  performance markers (5 CHANGE / 398 TUNE / 43 KEEP), not the 442
  (4 / 396 / 42) carried forward in 1.3.5, 1.3.7, and 1.3.9. Body and PDF
  were already correct; only the prior changelog tallies were off.
- Default markers reconcile to 1,004 (1,450 total markers minus 446
  performance), superseding the 1,005 figure in 1.3.9.
- PDF unchanged; SHA256 41abf78997ffea37e89a905ef5efbd458e13a2bb716cb1c8dfb7cb80a3d86da9.

## 1.3.10 - 2026-06-23

- Format changelog as Markdown lists: de-indent tab-led bullets to
  column 0 so GitHub renders them as a list, not a code block.
- PDF unchanged; SHA256 41abf78997ffea37e89a905ef5efbd458e13a2bb716cb1c8dfb7cb80a3d86da9.

## 1.3.9 - 2026-06-23

- Shade each marker line in its marker color: blue behind ◀ default,
  red behind ◀ performance (1,005 blue, 442 settings-table rows red).
- Legend lines in About This Document left unshaded.
- Body content, totals, and firmware ordering unchanged.
- SHA256 -> 41abf78997ffea37e89a905ef5efbd458e13a2bb716cb1c8dfb7cb80a3d86da9.

## 1.3.8 - 2026-06-23

- Fix corrupt document Word refused to open: remove three duplicate
  w:styleId definitions (Heading1/2/3) from styles.xml; the surviving
  definitions retain outlineLvl, so the table of contents still resolves.
- Convert deliverable to PDF (table of contents and Page N of M fields
  populated on export); drop the Word source.
- Body content, totals, and firmware ordering unchanged.
- SHA256 -> 9f20e029be8b16b9cb1d0550097b872e083f8b9d7ce878fd030ab5cda02e6166.

## 1.3.7 - 2026-06-22

- Trim verbose front-matter prose; condense performance-source list.
- Remove triplicated "record originals" caveat; keep one instance.
- Rewrite README in GitHub style (badges, source/coverage tables).
- Body unchanged: 149 tables, 1,045 rows, 1,006 default markers,
  442 performance markers (4 CHANGE / 396 TUNE / 42 KEEP), 113 pages.

## 1.3.6 - 2026-06-22

- Remove orphan part word/_rels/comments.xml.rels. Body unchanged.

## 1.3.5 - 2026-06-19

- Drop performance marker from 603 rows with no performance dimension.
- Markers remain on 442 rows (396 TUNE, 42 KEEP, 4 CHANGE).
- Legend no longer lists NEUTRAL; 138 -> 113 pages.

## 1.3.4 - 2026-06-19

- Add default markers to 18 Selection rows the IFR extraction missed.
- Leave 8 platform-specific and 2 borderline rows unmarked.

## 1.3.3 - 2026-06-19

- Append default marker to 348 numeric rows that printed a default
  inline but carried no marker.

## 1.3.2 - 2026-06-19

- Adjust marker colors: default royal blue (2563EB), performance red
  (D50000); every pair now dE >= 31.

## 1.3.1 - 2026-06-19

- Standardize markers: default blue, performance red. Superseded by 1.3.2.

## 1.3.0 - 2026-06-19

- Render performance recommendations inline at the foot of the Options
  cell (marker + tier tag + rationale), not a fourth column.
- Narrow settings tables to three columns; return to portrait US Letter.

## 1.2.3 - 2026-06-19

- Fix blank footer page numbers: cache PAGE/NUMPAGES with a dirty flag.
- Normalize clause separator in 683 performance notes to an em-dash.
- Drop vestigial empty comments part and its registration.

## 1.2.2 - 2026-06-17

- Fix two performance notes opening with the wrong single quote.

## 1.2.1 - 2026-06-17

- Collapse a 32-row runtime USB mass-storage dropdown to one summary row.
- Reconcile totals: 1,074 -> 1,045 settings; Aptio 213 -> 184.

## 1.2.0 - 2026-06-15

- Add tiered performance recommendation to every settings table, with a
  derivation section and legend.
- Widen tables to four columns; switch section to landscape.

## 1.1.0 - 2026-06-15

- Add DASH/ASF (8) and RAIDXpert2 (37) chapters; add Appendix A for
  excluded generic UEFI network-driver forms.
- Resolve RAID labels shown as <invalid offset> via a custom SIBT decoder.
- Totals: 5 -> 7 form-sets, 167 -> 186 forms, 1,134 -> 1,074 settings.

## 1.0.0 - 2026-06-15

- Initial catalog: 5 form-sets, 167 forms, 1,134 settings, decoded from
  GTRPR05.rom.
