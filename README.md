# MLZ-Hybrid-Method
Python pipeline that extracts equipment data from unstandardized instrument cut sheets (PDFs) and populates a standardized Excel template. Uses OCR for scanned docs, a versioned mapping table for known vendors/fields, and the Claude API to infer new/ambiguous fields — validated inferences get written back to the table.
