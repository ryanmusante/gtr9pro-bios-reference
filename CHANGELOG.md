# Changelog

## 1.3.0 - 2026-06-19

Changed
- Performance recommendations are no longer a separate fourth column. Each
  recommendation now renders inline at the foot of its Options / Values / Range
  cell as a `◀ performance` marker - same visual treatment as the existing
  `◀ default` factory-default marker - followed by its color-coded tier label
  and one-line rationale. This points the recommendation at the option it
  concerns and keeps the amplifying note beside it.
- Tier label color now carries onto the `◀ performance` arrow itself (CHANGE
  green / TUNE orange / KEEP blue / NEUTRAL grey), so the at-a-glance signal
  survives the move out of a dedicated column.
- Settings tables narrowed from four columns to three (Setting / Type /
  Options-Values-Range); per-table width corrected 12960 -> 9360 DXA and the
  document section returned to portrait (US Letter), reversing the v1.2.0
  landscape switch. The reclaimed width removes the right-edge overflow the
  four-column landscape layout had introduced.

Fixed
- Front matter reconciled to the inline layout: the "Reading the settings
  tables" legend now describes the `◀ performance` marker instead of a column,
  and "The Performance column reflects..." became "The Performance markers
  reflect...". No other front-matter wording changed.

Notes
- Counts unchanged and re-verified: 7 form-sets, 186 forms, 1,045 settings,
  147 settings tables (149 tables total incl. front-matter metadata and
  Appendix A); tier distribution 4 CHANGE / 396 TUNE / 42 KEEP / 603 NEUTRAL.
  1,045 `◀ performance` markers and 640 `◀ default` markers present.
- Recommendation text, tier assignments, and rationales are carried over
  verbatim from v1.2.3; only their placement and the arrow color changed.
- Document SHA256 updated in README to
  759619ea8a1cf2fda962b4b8fbaadf86efb767356c108746c1ff776754580256.


## 1.2.3 - 2026-06-19

Fixed
- Footer page-number fields rendered blank ("Page  of "). The PAGE and NUMPAGES
  fields were emitted with a begin/separate/end sequence but no result run and
  no dirty flag, so renderers showed nothing until a manual Update Field. Added
  a cached result run to each and marked them dirty; the footer now reads
  "Page N of M" on open without user action.
- Typography: normalized the clause separator in the Performance-column notes
  from a spaced ASCII hyphen to an em-dash (683 notes), matching the em-dash
  already used throughout the front matter. Compound terms (e.g. Serial/debug,
  Network-boot, all-core) and verbatim firmware strings are unchanged. No
  content, count, or tier change.

Removed
- Vestigial empty comments part (word/comments.xml) plus its relationship and
  content-type registration. The part held no comments and referenced nothing;
  dropping it yields a cleaner package with no functional change.

Notes
- Counts unchanged and re-verified: 7 form-sets, 186 forms, 1,045 settings,
  149 tables; tier distribution 4 CHANGE / 396 TUNE / 42 KEEP / 603 NEUTRAL.
- Form presentation order remains firmware depth-first (apparent form-ID
  descents are parent/child boundaries, not errors).
- Document SHA256 updated in README to
  b48f80a616dbd45066b5810a7df26ccef75ef17d9f147bdbb1a242911c217872.


## 1.2.2 - 2026-06-17

Fixed
- Typography: corrected two Performance-column notes where a quoted term opened
  with a right single quote instead of a left one (&#x2019;Custom&#x2019; ->
  &#x2018;Custom&#x2019; on AMD CBS OC Mode; the same on the PMF System
  Configuration power-profile note). No content or count change.

Notes
- Second full review pass. Verified with no further changes required: all 149
  tables well-formed; form presentation order matches firmware depth-first tree
  order (apparent form-ID descents are parent/child boundaries, not errors);
  Performance-tier assignments are internally consistent (no setting receives
  conflicting advice across its occurrences); duplicate-looking rows (Trusted
  Computing TPM/TCM blocks, RAID conditional form variants, runtime-populated
  one-of lists) are faithful firmware artifacts and were retained intentionally.
- Document SHA256 updated in README to 3502a9272f4b5908aeabc89f5f8591b8ff0aae61768761b153d8f9e9b5ba4c97.


## 1.2.1 - 2026-06-17

Fixed
- Collapsed a 32-row runtime block in the Aptio USB Configuration form (Form
  0x2750): the per-device USB mass-storage emulation dropdown was emitted as 32
  identical `N/A` rows. These are a single runtime-repeated control, not 32
  distinct settings; they are now represented by one summary row, matching the
  device-enumeration collapse already applied elsewhere in v1.1.0.
- Reconciled all settings totals against the document body. The 32 duplicate
  rows had inflated the catalog and the cover/overview counts had drifted out of
  sync with the per-tier breakdown. Corrected figures:
  - Total configurable settings: 1,074 -> 1,045.
  - Aptio Setup form-set: 213 -> 184 settings.
  - Tier distribution now sums to 1,045 (4 CHANGE, 396 TUNE, 42 KEEP, 603
    NEUTRAL); only the NEUTRAL count changed (634 -> 603), since the collapsed
    rows were all NEUTRAL.
- Form count (186), settings-table count, and all per-tier non-NEUTRAL totals
  were already correct and are unchanged.

Notes
- No setting was removed from the catalog's coverage: the collapsed rows
  described one control, and its full option list (Auto / Floppy / Forced FDD /
  Hard Disk / CD-ROM) is preserved in the summary row.
- Document SHA256 updated in README to a88f28411f024ceced60fd17971805d53c24eeec41309816f058478e58a28529.


## 1.2.0 - 2026-06-15

Added
- Performance column on every settings table (148 tables, 1,074 options). Each
  entry gives a recommended setting for the AMD Strix Halo / Ryzen AI Max+ 395
  platform plus a one-line rationale, color-coded by tier:
  - CHANGE (green): change away from default for a clear gain.
  - TUNE (orange): performance-relevant but workload-specific or expert-only.
  - KEEP (blue): the default already favors performance; leave it.
  - NEUTRAL (grey): no performance impact (security, connectivity, debug, or
    factory-trained values); leave default.
- "How the performance recommendations were derived" section and a column
  legend in the front matter, citing the sources used (AMD Variable Graphics
  Memory guidance, community Strix Halo LLM/BIOS setup guides, AMD/1usmus CBS
  high-performance recommendations, Tom's Hardware PBO + Curve Optimizer
  references, and Beelink GTR9 Pro Performance-mode reports).

Changed
- Settings-table layout widened to four columns; document section switched to
  landscape (US Letter) so the Performance column fits without crowding the
  existing Setting / Type / Options columns.

Notes
- Tier distribution across the 1,074 options: 4 CHANGE, 396 TUNE, 42 KEEP,
  634 NEUTRAL. The large NEUTRAL share reflects that most BIOS options here are
  security, connectivity, debug, or factory-trained memory/voltage controls with
  no performance dimension - the honest entry is "leave default," not an
  invented value.
- TUNE entries are validated starting points, not guaranteed-stable values.
  Silicon, cooling, and firmware revision vary; record originals before changing
  low-level CBS, AMD Overclocking, or PMF values. The soldered LPDDR5X memory is
  already trained to spec, so memory sub-timings and rail voltages are marked
  accordingly.

## 1.1.0 - 2026-06-15

Added
- DASH / ASF Management chapter (Dash Function submenu, 8 settings).
- RAIDXpert2 Configuration Utility chapter (37 settings) with full string
  resolution via custom SIBT decoder.
- Appendix A inventorying excluded generic UEFI network-driver forms.
- Scope and coverage section in the overview.

Fixed
- RAID module labels previously rendered as `<invalid offset>` (stock extractor
  bound only the first of multiple en-US string packages) now fully resolved.
- Corrected RAID form titles mis-resolved against the File Explorer string package.

Removed
- Internal scratch form (FormId 0x9999) holding 149 unlabeled working variables.
- Vestigial "File Explorer" string fragments and "create a new file" placeholders.
- Empty navigation-only forms; duplicate info-field labels.
- 32-slot runtime device-enumeration dropdown collapsed to a one-line summary.

Changed
- Totals: 5 -> 7 form-sets, 167 -> 186 forms, 1,134 -> 1,074 cleaned settings.

## 1.0.0 - 2026-06-15

Added
- Initial catalog: 5 form-sets (Aptio Setup, AMD CBS, AMD PBS, AMD Overclocking,
  AMD PMF), 167 forms, 1,134 settings, decoded from GTRPR05.rom.
- Title page, table of contents, overview, per-chapter settings tables.
