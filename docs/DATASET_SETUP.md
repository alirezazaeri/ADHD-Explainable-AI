# Dataset setup

## Official source

This project uses data from the **WiDS Datathon 2025**.

- [Kaggle competition](https://www.kaggle.com/competitions/widsdatathon2025)
- [Official WiDS event page](https://www.widsworldwide.org/events/event/wids-datathon-2025-unraveling-the-mysteries-of-the-female-brain/)

Obtain the dataset directly from the official provider. A Kaggle account and acceptance of the applicable competition rules may be required. Users are responsible for reviewing and complying with the provider's current access, privacy, citation, and usage terms.

This repository does not grant dataset access or usage rights, and its licensing status does not apply to the dataset.

## Expected local layout

Place authorized copies of the four input files in `data/`:

```text
data/
├── FUNCTIONAL_CONNECTOME_MATRICES.csv
├── LABELS.xlsx
├── METADATA_A.xlsx
└── METADATA_B.xlsx
```

The notebooks expect these exact filenames. Run them from the `notebooks/` working directory so their relative paths resolve correctly.

## Publication boundary

The complete dataset is not redistributed by this repository. Source files, processed files, generated splits, participant-level exports, copied archives, and model caches must remain local and ignored by Git.

Do not commit:

- any file listed above;
- files generated under `notebooks/final_datasets/`;
- participant extracts or sample rows;
- copied competition archives or restricted data-dictionary content.

The two published notebooks retain their historical recorded outputs. Those outputs are part of the preserved project record and are not a substitute for obtaining the dataset or accepting the provider's terms.

## Execution order

1. Obtain the files from the official provider.
2. Place them in `data/` using the expected filenames.
3. Create an isolated Python environment and install `requirements.txt`.
4. Start Jupyter with `notebooks/` as the working directory.
5. Run `01_data_exploration.ipynb`, then `02_modeling_and_testing.ipynb`.

The first notebook writes local derived tables to `notebooks/final_datasets/`. That directory is intentionally excluded from version control.
