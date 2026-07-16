# MLZ-Hybrid-Method
Python pipeline that extracts equipment data from unstandardized instrument cut sheets (PDFs) and populates a standardized Excel template. Uses OCR for scanned docs, a versioned mapping table for known vendors/fields, and the Claude API to infer new/ambiguous fields — validated inferences get written back to the table.

# Cut Sheet Extractor

Automates populating standardized Excel specs from unstandardized manufacturer
cut sheets, for the I&C team.

Cut sheets arrive in inconsistent formats across vendors — different layouts,
labels, and units for the same fields. This tool extracts the relevant data
and writes it into our standard Excel template, so engineers don't hand-key
values off PDFs.

## How it works
1. **Extract** — `pdfplumber` for text-based PDFs, falls back to OCR
   (Docling) for scanned/image-only sheets.
2. **Map** — a versioned mapping table normalizes known vendor labels, units,
   and value formats deterministically (no API call needed for known cases).
3. **Infer** — fields the mapping table doesn't recognize are sent to the
   Claude API for extraction/normalization.
4. **Validate** — a human reviews any LLM-inferred fields before they're
   accepted.
5. **Learn** — approved mappings are written back into the table, so the
   same vendor/field combo is handled deterministically (and for free) next
   time.

## Status
Early build — in development by the I&C team's summer interns.
