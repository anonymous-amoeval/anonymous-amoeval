# AMOEval (Anonymized Code Release)

This repository provides an end-to-end Colab notebook to reproduce the AMOEval pipeline:

1. Template induction from training reports (fixed slot catalog)
2. Optional multimodal report generation (image + keywords)
3. Two-step template filling into entity descriptions with verbatim evidence
4. Entity-wise judging with a four-way taxonomy (ALIGNED / MISMATCHED / OMITTED / EXTRA)
5. Scope-map aggregation (IS vs OOS) and table export

## MICCAI anonymity

For double-blind review, keep this repository anonymous:

- Do not include author names, emails, affiliations, or identifying links.
- Use a fresh anonymous GitHub account.
- Avoid identifiable commit author information.

## Inputs

Only two inputs are required:

- `IMAGES_ROOT`: a folder containing the raw images
- `REPORT_JSON_PATH`: a single JSON file containing (at minimum) image paths and doctor/reference reports

The notebook supports several common JSON schemas (list of dicts; dict with train/test lists; dict with a `data` list). You can adapt field names in the loader if needed.

## Running

Open `AMOEval_DeepEyeNet_Colab.ipynb` in Google Colab and run cells in order.

You must provide an API key via the runtime prompt (the notebook does **not** hardcode keys).

## Outputs

The notebook writes outputs under `OUTPUT_DIR`:

- `amo_eval_template.json`: induced slot catalog
- `model_reports.jsonl`: generated model reports (optional; can be user-provided)
- `doctor_filled.jsonl`, `model_filled.jsonl`: entity extractions
- `semantic_sets_full.csv`: entity-level labels
- `label_stats_summary.xlsx`: compact tables for paper reporting
