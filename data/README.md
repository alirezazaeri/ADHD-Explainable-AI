# Local source data

This directory is intentionally data-free in version control. Place authorized local copies of the following files here when reproducing the exploratory workflow:

- `LABELS.xlsx`
- `METADATA_A.xlsx`
- `METADATA_B.xlsx`
- `FUNCTIONAL_CONNECTOME_MATRICES.csv`

These files contain participant-level records and must not be committed. Obtain them from the original provider, accept the provider's access conditions, and verify the applicable terms before use.

See [dataset setup](../docs/DATASET_SETUP.md) for the official WiDS and Kaggle links, expected local layout, and publication boundary. The repository does not grant access or usage rights to the dataset.

## Local handling boundary

- Keep the original provider filenames unchanged so notebook paths resolve.
- Do not add sample rows, schemas copied from restricted material, archives, or screenshots to this directory.
- Treat temporary extracts and data-quality exports as participant-level data even when identifiers have been removed.
- Confirm `git check-ignore data/<filename>` before beginning local work.

The repository's [MIT License](../LICENSE) does not apply to these files.
