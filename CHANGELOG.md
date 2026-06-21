# Changelog

## 1.3.6 - 2026-06-21

Fixed
- Removed 24 duplicate rows that did not represent distinct firmware settings.
  Earlier passes retained these as faithful artifacts; they are redundant for
  configuration and are now collapsed, first occurrence kept:
  - Smart Fan Function (Form 0x2737): Fan1 and Fan2 each listed their curve
    block (off/start/full-speed temp, start PWM, PWM slope) twice. Collapsed to
    one block per fan; the four fans now have one control set each (-10).
  - Trusted Computing (Form 0x271A): duplicate Security Device Support and
    Pending operation rows; the TPM-group copies are kept (-2).
  - Display Configurations (Form 0x10): repeated Adjust DP Caps; DP0's row is
    kept as the reference (-4).
  - View Physical Disk Properties (RAID Form 0x222): an 8-row block repeated
    verbatim (-8).
- Reconciled all settings totals against the document body:
  - Total configurable settings: 1,045 -> 1,021.
  - Aptio Setup form-set: 184 -> 172; AMD PBS: 206 -> 202; RAIDXpert2: 37 -> 29.
  - Tier distribution: 4 CHANGE, 386 TUNE, 42 KEEP, 589 no-marker. Only TUNE
    (396 -> 386) and no-marker (603 -> 589) changed; the removed rows were 10
    TUNE and 14 unmarked.
  - `◀ performance` markers: 442 -> 432.

Notes
- Rows that share a label but differ in content (growing Pstate/GOP/CacheTagSize
  one-of lists, per-port controls) are distinct settings and were retained.
- Document SHA256 updated in README to
  3e40738731e360c294f5fa433bdb564b924f0ed7e66958a673e79245703fac94.


## 1.3.5 - 2026-06-19

Changed
- Removed the `◀ performance` marker from every setting with no performance
  dimension (the 603 rows previously tagged NEUTRAL); they now show only their
  options and the blue `◀ default`. Markers remain on the 442 rows with an
  actual recommendation: 396 TUNE, 42 KEEP, 4 CHANGE.
- Front-matter legend reconciled: no longer lists NEUTRAL as a tag.

Notes
- `◀ performance` total: 1,045 -> 442. `◀ default` unchanged at 1,006. Settings
  count unchanged (1,045 rows; 603 carry no performance marker, 442 do).
- Document shortened from 138 to 113 pages.


## 1.3.4 - 2026-06-19

Fixed
- Extended default-marker coverage to 18 Selection rows whose firmware default
  the original IFR extraction did not capture (14 high-confidence AMI Aptio V
  defaults plus 4 clear platform defaults).

Notes
- No defaults were invented. 8 platform-specific rows and 2 borderline rows were
  left unmarked, as the source ROM/IFR was unavailable to recover them.


## 1.3.3 - 2026-06-19

Fixed
- Numeric settings that printed a default inline but carried no marker now have a
  blue `◀ default` appended next to the stated Default value (348 rows).


## 1.3.2 - 2026-06-19

Changed
- Marker colors adjusted for distinguishability from the tier-tag colors.
  Default is now royal blue (2563EB) and performance a stronger red (D50000);
  every marker/tier color pair is now CIE76 ΔE >= 31.


## 1.3.1 - 2026-06-19

Changed
- Marker colors standardized: `◀ default` blue and `◀ performance` red,
  everywhere including the front-matter legend. Superseded by v1.3.2.


## 1.3.0 - 2026-06-19

Changed
- Performance recommendations are no longer a separate fourth column. Each now
  renders inline at the foot of its Options / Values / Range cell as a
  `◀ performance` marker, followed by its tier label and one-line rationale.
- Settings tables narrowed from four columns to three; per-table width corrected
  12960 -> 9360 DXA and the document returned to portrait (US Letter).

Fixed
- Front matter reconciled to the inline layout.

Notes
- Counts unchanged: 7 form-sets, 186 forms, 1,045 settings, 147 settings tables.


## 1.2.3 - 2026-06-19

Fixed
- Footer page-number fields rendered blank ("Page  of "). Added a cached result
  run to the PAGE and NUMPAGES fields and marked them dirty; the footer now
  reads "Page N of M" on open.
- Typography: normalized the clause separator in the performance notes from a
  spaced ASCII hyphen to an em-dash (683 notes). No content or count change.

Removed
- Vestigial empty comments part (word/comments.xml) plus its relationship and
  content-type registration.

Notes
- Counts unchanged: 7 form-sets, 186 forms, 1,045 settings, 149 tables; tier
  distribution 4 CHANGE / 396 TUNE / 42 KEEP / 603 NEUTRAL.


## 1.2.2 - 2026-06-17

Fixed
- Typography: corrected two performance notes where a quoted term opened with a
  right single quote instead of a left one. No content or count change.

Notes
- Second review pass; all 149 tables well-formed and tier assignments
  internally consistent.


## 1.2.1 - 2026-06-17

Fixed
- Collapsed a 32-row runtime block in the Aptio USB Configuration form (Form
  0x2750): the per-device USB mass-storage emulation dropdown was emitted as 32
  identical `N/A` rows. Now represented by one summary row.
- Reconciled all settings totals against the document body:
  - Total configurable settings: 1,074 -> 1,045.
  - Aptio Setup form-set: 213 -> 184 settings.
  - Tier distribution sums to 1,045 (4 CHANGE, 396 TUNE, 42 KEEP, 603 NEUTRAL);
    only NEUTRAL changed (634 -> 603).

Notes
- No setting lost coverage: the collapsed rows described one control, and its
  full option list is preserved in the summary row.


## 1.2.0 - 2026-06-15

Added
- Performance column on every settings table (148 tables, 1,074 options),
  color-coded by tier:
  - CHANGE (green): change away from default for a clear gain.
  - TUNE (orange): performance-relevant but workload-specific or expert-only.
  - KEEP (blue): the default already favors performance; leave it.
  - NEUTRAL (grey): no performance impact; leave default.
- "How the performance recommendations were derived" section and a column
  legend in the front matter, citing the sources used.

Changed
- Settings-table layout widened to four columns; document switched to landscape
  (US Letter) so the Performance column fits.

Notes
- Tier distribution across the 1,074 options: 4 CHANGE, 396 TUNE, 42 KEEP,
  634 NEUTRAL.
- TUNE entries are validated starting points, not guaranteed-stable values.
  Record originals before changing low-level CBS, AMD Overclocking, or PMF
  values.


## 1.1.0 - 2026-06-15

Added
- DASH / ASF Management chapter (Dash Function submenu, 8 settings).
- RAIDXpert2 Configuration Utility chapter (37 settings) with full string
  resolution via custom SIBT decoder.
- Appendix A inventorying excluded generic UEFI network-driver forms.
- Scope and coverage section in the overview.

Fixed
- RAID module labels previously rendered as `<invalid offset>` now fully
  resolved.
- Corrected RAID form titles mis-resolved against the File Explorer string
  package.

Removed
- Internal scratch form (FormId 0x9999) holding 149 unlabeled working variables.
- Vestigial "File Explorer" string fragments and placeholders.
- Empty navigation-only forms; duplicate info-field labels.
- 32-slot runtime device-enumeration dropdown collapsed to a one-line summary.

Changed
- Totals: 5 -> 7 form-sets, 167 -> 186 forms, 1,134 -> 1,074 cleaned settings.


## 1.0.0 - 2026-06-15

Added
- Initial catalog: 5 form-sets (Aptio Setup, AMD CBS, AMD PBS, AMD Overclocking,
  AMD PMF), 167 forms, 1,134 settings, decoded from GTRPR05.rom.
- Title page, table of contents, overview, per-chapter settings tables.
