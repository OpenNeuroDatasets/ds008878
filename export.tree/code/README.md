# Chinese compound word EEG data organization

This repository builds the Table 3 data layers of the Scientific Data manuscript:
continuous BrainVision EEG, traceable trial events and behavior, stimulus metadata,
a separate harmonized Python derivative, QC, provenance and validation.

The complete local snapshot is `../Scientific_Data_Organized_2026-09-13/`.
Read `WORKFLOW.md` for commands and `TABLE3_ALIGNMENT.md` for manuscript corrections.
The data package contains a copy of this code and exact runtime dependency versions.

## Current entry points

- `src.release.curate`: exhaustive native inventory, raw copies and event/behavior linking.
- `src.release.harmonize`: reusable epochs, voltage features, flags, condition averages and signal QC.
- `src.release.audit_snapshot`: independent joins, counts and numerical feature checks.
- `src.release.package_review`: metadata, source tables, code snapshot and Table 3 crosswalk.
- `src.release.manifest`: SHA256 creation and verification.
- `tests/test_release_regressions.py`: timeout, indexing, sampling and stimulus-field regressions.

`src/preprocessing/` and older `build.py`, `qc.py`, `validate.py` are historical
implementations retained for provenance. Do not use them for the current release:
they do not implement the corrected full inventory and current data contract.
They are not BrainVision Analyzer source-publication reproductions.

This is local scientific data preparation. Public-release authorization, final
cohorts, licenses, DOI, some metadata and original-analysis histories remain unresolved.
