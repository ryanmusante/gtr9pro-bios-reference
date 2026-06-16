# Changelog

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
