# Notebook integrity

## Preserved artifacts

The repository publishes two historical notebooks with their saved cells, outputs, execution counts, figures, and metadata intact:

| Notebook | SHA-256 |
|---|---|
| `notebooks/01_data_exploration.ipynb` | `77dc1c6c01b8557c8eb92449ac5e870f89bed5950ac14dabc8357f50c2acf79d` |
| `notebooks/02_modeling_and_testing.ipynb` | `a9d9f1e681bf6fc30ef6305d95883798f6e0482c086241b70d948181e004ba3f` |

These hashes define the publication baseline. A mismatch means the notebook is no longer byte-for-byte identical to the approved artifact.

## Read-only verification

From the repository root, run:

```bash
python scripts/validate_publication.py
```

The validator reads file bytes and Git metadata. It does not import notebook code, start a kernel, access the dataset, execute cells, clear outputs, or rewrite metadata.

Direct platform commands may also be used:

```bash
shasum -a 256 notebooks/01_data_exploration.ipynb notebooks/02_modeling_and_testing.ipynb
```

## Change boundary

Do not use notebook formatters, output cleaners, metadata normalizers, automatic execution tools, or merge-conflict resolvers on these files. Even a semantically harmless JSON rewrite changes the byte-level record and its hash.

A proposed corrected analysis must be designed and reviewed as a new, explicitly versioned experiment. It must not replace, sanitize, or silently revise the preserved historical notebooks.

## Mismatch response

If either hash differs:

1. stop the publication or review operation;
2. do not execute or attempt to repair the notebook in place;
3. inspect Git status and the exact binary/text diff without exposing outputs;
4. identify whether the change is local, staged, or committed;
5. restore only through an explicitly reviewed repository change.

Never copy participant-level output into an issue or pull request while investigating a mismatch.
