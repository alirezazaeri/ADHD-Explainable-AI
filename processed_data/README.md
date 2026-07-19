# Local processed data

Use this directory only for intermediate participant-level datasets generated during local analysis. Its contents are excluded from version control.

Intermediate tables may include imputed metadata, selected features, transformed connectome components, joins, or quality-control exports. De-identification and transformation do not make these files suitable for publication.

- Store only authorized local working files here.
- Do not commit samples, previews, manifests containing record values, or copied data dictionaries.
- Delete local derivatives according to the provider's terms and the user's retention policy.
- Confirm `git check-ignore processed_data/<filename>` before generating an export.

The repository's [MIT License](../LICENSE) does not apply to processed data.
