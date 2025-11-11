# Dictionary based method (old samples)


## Purpose
- Parse text files (plain .txt) that contain content, and count occurrences of theme word lists (e.g., positive/negative/forward-looking/risk).
- Produce an Excel workbook with one sheet per theme. Each sheet shows counts by file ID (rows) and year (columns).
- Designed to support word-based and phrase-based matching.

## Quick usage
- Install dependencies:
  pip install openpyxl tqdm

- Run (example):
  python list_sentences_by_categories.py \

## Category file format
- Each non-empty line: KEY: word1, word2, phrase three
- Lines beginning with `#` or empty lines are ignored.
- Example:
  positive: improve, growth, succeed
  negative: risk, loss, decline

## Theme file format
- Same format as category file. Keys will become sheet names (capitalized).

## Filename convention
- By default the script expects filenames matching:
  {id}_..._{YYYY}[...].txt
  Example: 123_report_2020.txt
- If the regex does not match, the script uses the filename (without extension) as ID and year `"Unknown"`.

## Outputs
- Excel workbook with one sheet per theme (sheet title is theme name capitalized).
- Rows: file IDs; Columns: years (sorted, with "Unknown" included if present).
- Counts are integers; missing combinations are filled with 0.

## Notes & tips
- If your theme words include multi-word phrases, they should be listed verbatim in the theme file (comma-separated). Phrases are matched as whole-word sequences.
- The script is case-insensitive.
- For scanned PDFs you must OCR them to .txt before using this script.
