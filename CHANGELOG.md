# Changelog

## 1.3.7 - 2026-06-22

	- Trim verbose front-matter prose: condense the performance-derivation
	  source list to a compact summary (1,241 -> ~640 chars).
	- Remove the triplicated "record originals" caveat; it now lives only in
	  the Advanced tuning caution note.
	- README rewritten in GitHub style (badges, source/coverage tables).
	- Document body unchanged: 149 tables, 1,045 rows, 1,006 default markers,
	  442 performance markers (4 CHANGE / 396 TUNE / 42 KEEP), 113 pages.
	- SHA256 -> c92fde7027cbad513ef943fbe3b26f3bd3e3d290b5bcad9fb7247070084d8133.

## 1.3.6 - 2026-06-22

	- Remove orphan part word/_rels/comments.xml.rels, left dangling when the
	  comments part was dropped in 1.2.3. Body byte-for-byte unchanged.

## 1.3.5 - 2026-06-19

	- Drop the performance marker from the 603 rows with no performance
	  dimension (was NEUTRAL); they now show only options and default. Markers
	  remain on 442 rows: 396 TUNE, 42 KEEP, 4 CHANGE.
	- Legend no longer lists NEUTRAL; document 138 -> 113 pages.

## 1.3.4 - 2026-06-19

	- Add default markers to 18 Selection rows the IFR extraction missed
	  (Network Stack, PXE/HTTP, Fast Boot, NumLock, VGA/USB Support, boot mode,
	  etc.). 8 platform-specific and 2 borderline rows left unmarked.

## 1.3.3 - 2026-06-19

	- Append a default marker to 348 numeric rows that printed a default
	  inline but carried no marker, matching the Selection convention.

## 1.3.2 - 2026-06-19

	- Adjust marker colors for separation from tier tags: default royal blue
	  (2563EB), performance red (D50000); every pair now dE >= 31.

## 1.3.1 - 2026-06-19

	- Standardize markers: default blue, performance red. Superseded by 1.3.2.

## 1.3.0 - 2026-06-19

	- Move performance recommendations inline: render at the foot of the
	  Options cell as a marker + tier tag + rationale, not a fourth column.
	- Narrow settings tables to three columns; return document to portrait
	  US Letter (reverses the 1.2.0 landscape switch).

## 1.2.3 - 2026-06-19

	- Fix blank footer page numbers: add cached result + dirty flag to the
	  PAGE/NUMPAGES fields so "Page N of M" renders on open.
	- Normalize the clause separator in 683 performance notes to an em-dash.
	- Drop the vestigial empty comments part and its registration.

## 1.2.2 - 2026-06-17

	- Fix two performance notes opening a quote with the wrong single quote.

## 1.2.1 - 2026-06-17

	- Collapse a 32-row runtime USB mass-storage dropdown to one summary row.
	- Reconcile totals: 1,074 -> 1,045 settings; Aptio 213 -> 184; NEUTRAL
	  634 -> 603.

## 1.2.0 - 2026-06-15

	- Add a performance recommendation to every settings table, tiered
	  CHANGE / TUNE / KEEP / NEUTRAL, with a derivation section and legend.
	- Widen tables to four columns; switch section to landscape.

## 1.1.0 - 2026-06-15

	- Add DASH/ASF (8 settings) and RAIDXpert2 (37 settings) chapters; add
	  Appendix A for excluded generic UEFI network-driver forms.
	- Resolve RAID labels previously shown as <invalid offset> via a custom
	  SIBT decoder; drop internal scratch forms and placeholder fragments.
	- Totals: 5 -> 7 form-sets, 167 -> 186 forms, 1,134 -> 1,074 settings.

## 1.0.0 - 2026-06-15

	- Initial catalog: 5 form-sets, 167 forms, 1,134 settings, decoded from
	  GTRPR05.rom.
