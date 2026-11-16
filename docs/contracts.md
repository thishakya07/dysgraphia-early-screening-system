# Contracts between components

Change a column name or format only after telling the whole group.

## 1. Dashboard -> Image Processing
Input: photo file (jpg or png, max 10 MB) plus
`child_code`, `grade_band` (G1-2, G3-5, G6-9, G10-13), `script` (Sinhala, English).

## 2. Image Processing -> Feature Extraction
Cleaned image: PNG, black ink on white, file name `<image_file>.png`.

`qc.csv` columns:
| column | meaning |
|---|---|
| image_file | key |
| status | pass or fail |
| retake_reason | blurry, too_dark, low_contrast, tilted, cropped, glare, faint_writing, too_few_lines, or empty |
| blur, brightness, contrast, shadow, skew_deg, ink_contrast, lines | measured values |

## 3. Feature Extraction -> Reference Analysis
`features.csv`: one row per image, key `image_file`.
| column | meaning |
|---|---|
| image_file | key |
| n_lines, n_letters | counts |
| letter_height_median | median letter height in pixels (used for normalising) |
| letter_height_cv | variation of letter height (consistency) |
| word_gap_median, word_gap_cv | word spacing, divided by letter height |
| line_gap_median | line spacing, divided by letter height |
| baseline_dev | baseline deviation, divided by letter height |
| slant_deg | writing slant in degrees |
| left_margin, right_margin | margins, divided by page width |
| stroke_width | stroke width, divided by letter height |
| ink_density | share of ink pixels in the writing area |

Missing values are left empty, never 0.

## 4. Reference Analysis -> Dashboard
Result JSON:
```json
{
  "image_file": "SCH-G1-2-SIN-0007_std.jpg",
  "child_code": "SCH-G1-2-SIN-0007",
  "grade_band": "G1-2",
  "script": "Sinhala",
  "label": "Within the reference range",
  "features_outside_range": [
    {"feature": "word_gap_cv", "value": 0.62, "z_score": 2.4, "direction": "high"}
  ],
  "ranges_version": "ranges_v1_real",
  "children_in_range": 34,
  "notice": "Screening aid only. This is not a diagnosis."
}
```
`label` is one of "Within the reference range" or "Worth a closer look".