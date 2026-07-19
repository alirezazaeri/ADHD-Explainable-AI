# Local final data

Use this directory only for final participant-level feature tables generated locally. Its contents are excluded from version control and must not be published.

Final analysis tables remain derived dataset material even when columns have been scaled, selected, encoded, or transformed. They may retain sensitive labels, subgroup attributes, or linkable row structure.

- Keep train/test tables and model-ready matrices local.
- Do not publish representative rows or record-level predictions.
- Do not treat derived tables as covered by the repository licence.
- Confirm `git check-ignore final_data/<filename>` before writing an export.

The historical notebooks write their own generated tables under `notebooks/final_datasets/`; that directory follows the same publication boundary.
