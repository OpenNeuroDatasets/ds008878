# Chinese compound word EEG local review dataset

This directory organizes the available native recordings against Table 3 of
2026.9.9 Scientific Data Data Descriptor Final Expert Polished Methods Migrated.
It is a local review snapshot, not a frozen or authorized public release.

## Start here

- `derivatives/qc/table3_crosswalk.tsv`: each Table 3 row and its actual status.
- `derivatives/qc/retention_by_experiment.tsv`: observed trial and derivative counts.
- `derivatives/harmonized/trial_resolved_eeg_behavior.tsv`: complete linked trial table.
- `derivatives/harmonized/data_dictionary.tsv`: field types, units and definitions.
- `code/WORKFLOW.md`: reproducible commands and known limitations.

## Layers and keys

`sub-*/eeg/` contains unchanged EEG binaries and renamed BrainVision headers/markers,
with acquisition timestamps removed from New Segment markers. Recorded target and
response markers are retained. Other display onsets are reconstructed in named columns.
`participant_id`, `run`, `trial_index` link events, epochs and trial features. Trial
indices retain original main-task order, including gaps. `native_list` identifies
the randomized stimulus list; it is distinct from chronological `block`.

`sourcedata/behavior/` retains every main-task behavioural row with pseudonymous codes,
including unlinked rows. Original workbooks and native EEG remain in their source folder.
`sourcedata/native_to_bids_mapping.tsv` records the mapping, offsets and known corrections.
`stimuli/materials.tsv` uses a stable `stimulus_key`. Raw Stimulus1/Stimulus2 strings
are retained because prime/target roles still require program-level confirmation.
No pinyin, translations, morpheme labels or item norms have been invented.

`derivatives/harmonized/` contains a code-defined 0.5–30 Hz, average-mastoid branch.
Epochs span -0.4 to 1.0 s in every experiment, with experiment-specific baselines.
NPZ arrays contain all in-bounds epochs, including artifact and incorrect-response trials.
The posterior ROI peak-to-peak threshold applies to its channel-averaged waveform.
Inclusion flags do not delete observations. Missing values in TSV files are `n/a`.
Timing-sensitive inclusion is provisional. RT=0 without a response is not a fast RT.

`derivatives/published-analysis/` documents missing historical inputs; no files in
that directory are presented as reproduced published condition averages.
`derivatives/qc/` contains record and channel reports, PSDs, timing flags and checks.
No measured electrode coordinates are available; no synthetic montage is supplied.

## Inventory corrections relative to the earlier manuscript audit

The earlier code omitted exp2p35, although a 110-trial recording exists and matches
the first 110 formal behavioural rows exactly. This snapshot retains it: 98 codes,
99 recordings, 53,456 linked trials. Of 53,900 formal behavioural rows, 444 lack a
matched preserved target marker: 4 for exp2p02 and 440 for exp2p35. This is a file
inventory finding, not evidence about participant recruitment or exclusions.

The earlier 213 timing mismatches included 209 RT=0/no-response trials. These are
now separated from 4 valid-response residuals outside the provisional 25-ms threshold.
Earlier fast-response counts also included RT=0; use the regenerated positive-RT counts.

Final public cohorts, consent, license, DOI, source-analysis histories, lexical
annotations and several acquisition parameters still require author records.
See code/TABLE3_ALIGNMENT.md before updating manuscript claims.
