# SPRITE pipeline (Princeton fork) Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

## [1.0.0] - 2017-06-20
### Added
- `CHANGELOG.md` created
- Added `environment.yml` to facilitate the installation of Snakemake
- Added a ciona genome (`ci_ht_ky19`) to the list of allowed genomes

### Changed
- Use Bioconda to install Hi-Corrector software
- Request 8GB memory for `make_clusters` rule
- Updated `README.md` to include installation and setup instructions
- Updated `LICENSE.md` to include Princeton University
- Skip the `add_chr` step for the ciona genome

### Removed

### Deprecated

### Fixed

### Security

## [1.0] - 2021-07-28
Guttman Lab release v1.0 - First published release of the SPRITE pipeline

## [0.3] - 2021-07-28
Guttman Lab release 0.3 - Latest release of SPRITE pipline corresponding to
description published in Quinodoz et al. 2021 Nature Protocols

## [0.2] - 2020-09-01
Guttman Lab release 0.2 - Snakemake pipeline to automate the analysis from
fastq to heatmaps

## [0.1] - 2019-10-27
Guttman Lab release 0.1 - Initial pipeline release

[Unreleased]: https://github.com/Princeton-LSI-ResearchComputing/sprite-pipeline/compare/v1.0...hic_bioconda
[1.0]: https://github.com/GuttmanLab/sprite-pipeline/compare/0.3...v1.0
[0.3]: https://github.com/GuttmanLab/sprite-pipeline/compare/0.2...0.3
[0.2]: https://github.com/GuttmanLab/sprite-pipeline/compare/0.1...0.2
[0.1]: https://github.com/GuttmanLab/sprite-pipeline/releases/tag/0.1
