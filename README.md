# Beelink GTR9 Pro — UEFI BIOS Setup Reference

Comprehensive catalog of every BIOS Setup configuration option exposed by the
Beelink GTR9 Pro UEFI firmware, decoded directly from the firmware image.

## Contents

| File | Purpose |
| --- | --- |
| `GTR9Pro_BIOS_Settings.docx` | Editable Word document (the deliverable) |
| `README.md` | This file |
| `CHANGELOG.md` | Version history |

## Source

- Firmware image: `GTRPR05.rom` (33,554,432 bytes / 32 MB)
- Flash package: `GTRPR05_WinFlash` (AMI AFUWIN / AfuEfi)
- BIOS vendor: American Megatrends International (AMI Aptio V)
- SoC platform: AMD Strix Halo (Ryzen AI Max series APU)

## Coverage

7 BIOS-owned Setup form-sets, 186 forms, 1,045 configurable settings.

| Chapter | Form-set | Settings |
| --- | --- | --- |
| Aptio Setup (Main tree) | Setup | 184 |
| AMD CBS | CbsSetupDxe | 318 |
| AMD PBS | AmdPbsSetupDxe | 206 |
| AMD Overclocking | AodDxe | 153 |
| AMD PMF | AmdCpmPmfBoardDxe | 139 |
| DASH / ASF | DashManagementDxe | 8 |
| RAIDXpert2 | (RAID formset) | 37 |

Generic UEFI network-stack driver forms (IPv4/IPv6/VLAN/HTTP/TLS/PXE) are
out of scope (not board BIOS settings) and inventoried in Appendix A.


## Performance recommendations (v1.2.0+)

Every settings table carries a per-option **Performance** recommendation: a
recommended value for the AMD Strix Halo / Ryzen AI Max+ 395 platform with a
one-line rationale. As of v1.3.0 the recommendation is rendered inline beneath
each option list as a red `◀ performance` marker (mirroring the blue `◀ default`
factory-default marker), rather than in a separate fourth column; the document
is therefore in portrait. Each marker is followed by a color-coded tier tag -
**CHANGE** (green; change for a gain), **TUNE** (orange; workload-specific /
expert-only), **KEEP** (blue; default already optimal), and **NEUTRAL** (grey;
no performance impact; leave default). The marker colors (blue default, red
performance) are deliberately chosen to be distinct from all four tier-tag
colors. See the front-matter section "How the performance recommendations were
derived" for the sources and caveats. TUNE entries are validated starting
points, not guaranteed-stable values - record originals before changing
low-level CBS, AMD Overclocking, or PMF settings.

## Methodology

1. ROM unpacked with UEFIExtract (UEFITool, built from source).
2. IFR decoded from each Setup-bearing PE32 via Universal-IFR-Extractor (built from source).
3. HII string packages decoded with a custom SIBT block parser to resolve
   labels the stock extractor left unresolved (the RAID module ships multiple
   en-US string packages; only the first is auto-bound). String resolution
   verified byte-for-byte against the extractor's known-good Setup output.
4. Internal scratch forms, runtime device-enumeration lists, and unlabeled
   working variables filtered out for readability.

## Reading the document

- Each chapter = one firmware form-set; sub-sections = individual Setup pages,
  in the exact order the firmware presents them.
- Settings tables: Setting / Type / Options-Values-Range. Bracketed values are
  raw NVRAM values (usable for SCEWIN/AMISCE scripting). The factory default is
  marked with a blue `◀ default`. Beneath each option list, a red `◀ performance`
  marker gives the recommended setting per option, followed by its tier tag (see
  "Performance recommendations" above).
- Defaults shown are compiled Standard Defaults; a unit's live values may differ.
- Many options are conditionally hidden on screen (suppress-if / grayout-if), so
  this catalog is a superset of what any single unit displays.

## Notes

- The Table of Contents is a live Word field: open in Word and Update Field
  (or right-click -> Update Field) to populate it. It may show blank until
  updated — expected behavior for that field type.
- BIOS Version / Build Date are runtime-populated and shown as placeholders.

## Integrity (SHA256)

```
47e2bf3610f5b9a68ca47a5051a668d73c3589214277ab96e325d2a69cf10ee7  GTR9Pro_BIOS_Settings.docx
```
