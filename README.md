# Shallow-water angle-selection data

Data accompanying *Selecting angle estimates for shallow-water acoustic localization using cross-window posterior compatibility*, by Chuanxi Xing and Lianjie Zhang, Yunnan Minzu University.

## Download

Download both ZIP files from [Release v1.0.0](https://github.com/lianjie228/shallow-water-angle-selection-data/releases/tag/v1.0.0). GitHub's automatically generated source-code ZIP contains repository documentation, not the measurement archives.

| File | Contents |
|---|---|
| hydroacoustic_raw_10kHz.zip | 158 original MAT measurement files, stored under raw/ |
| simulation_and_processed_data.zip | 934 simulation, protocol and processed-result files |
| hydroacoustic_file_manifest.csv | Raw-file sizes and SHA-256 hashes, matched against the experiment inventory |
| simulation_file_manifest.csv | Published and source-file hashes and relative paths |
| SHA256SUMS.txt | SHA-256 checksums of the two ZIP archives |

## Measurement format

The MAT files contain the double-precision matrix `U`, with seven rows (channels) and columns representing samples. Sampling frequency is 10,000 Hz. MATLAB can load a file using `load('115249.mat')`; Python can use `scipy.io.loadmat`. The inspected file 115249.mat has shape 7 by 149796. File lengths should be read from each matrix.

The paper uses pressure channel 4 (MATLAB `U(4,:)`, Python `U[3,:]`). Other channel identities and absolute calibration are not specified here. Filenames are acquisition identifiers. The original archive is described as vector-hydrophone measurements of a 60–400 Hz linear frequency-modulated signal.

`output/主线验证与小论文修订_20261002/field/background_manifest.csv` identifies the six temporal groups, the development/evaluation split (62/96 files), background segments and original hashes. The release preserves all 158 MAT files byte-for-byte. Unrelated Word documents and the MATLAB script bundled in the supplied archive are excluded.

## Mapping to manuscript results

Paths below are inside simulation_and_processed_data.zip. Original experiment directory names are preserved to keep file provenance traceable.

- `output/pure_simulation_20260929/` and `output/pure_simulation_reaudit_20260929/`: controlled feature/waveform simulations and their recalculated results.
- `output/contribution_feasibility_20261002/`: independent feature/waveform experiments, record-level outputs, primary comparisons and propagation files. `primary_mse_table.csv` includes the primary feature comparison; `all_records.csv` contains record-level results.
- `output/主线验证与小论文修订_20261002/simulations/`: additional simulation comparisons.
- `output/主线验证与小论文修订_20261002/field/`: measured-background inventories, signal-injection results and derived field analyses.
- `output/shared_environment_external_20260928/` and `output/定位内证据精进_20261002/`: derived field/model results.
- `output/声学链路闭环验证与修订_20261005/background_stress/`: known-waveform stress tests underlying Figure 3.
- `output/声学链路闭环验证与修订_20261005/background_compensation_v2/`: final time-scaled-template experiment underlying Table 5. The natural-background continuous-scaling success rates in summary.csv are 0.6651742581 for the fixed template and 0.9406659765 for the dilation bank.

CSV files retain their original column headers; JSON files describe protocols and environments. NPZ/NPY files are NumPy arrays. ARR/ENV/BTY/SSP files are acoustic propagation outputs/inputs. Angular MSE is expressed in degrees squared; columns explicitly ending in `_ms` are milliseconds. Success columns in the final compensation summary are proportions, and manuscript percentages use equal weighting across temporal groups rather than pooled counting.

The collection also includes development and diagnostic results. Use the manuscript's stated experiment, split, frontend, budget and context condition when selecting rows. Machine-specific absolute paths in two metadata files were replaced with `LOCAL_PATH/filename`; source and published hashes identify those changes. Numerical result values were not changed.

## Third-party data and software

SWellEx-96 source observations are available from the [UCSD experiment website](https://swellex96.ucsd.edu/). They are not redistributed here. This release includes data and documentation; it does not include the full analysis source code, BELLHOP executable or a complete runtime environment.

## Access and citation

The authors provide public download without granting an additional reuse license. No Creative Commons or open-source license is attached. Cite the authors, dataset title, version v1.0.0 (2026), and the release URL when referring to this collection. No DOI has been assigned.

Funding: National Natural Science Foundation of China, grant 62661063.
