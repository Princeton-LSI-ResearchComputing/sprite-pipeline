# Snakemake for sprite-pipeline (Princeton fork)

This repository is a fork of the original [Guttman Lab SPRITE
pipeline](https://github.com/GuttmanLab/sprite-pipeline). See `CHANGELOG.md`
for a list of changes.

For detailed documentation of all the steps performed within the Snakemake
please refer to: https://github.com/GuttmanLab/sprite-pipeline/wiki

## Requirements

1. [Install and configure Bioconda](https://bioconda.github.io/user/install.html#)

2. Install `git`

## Installation

1. Clone the GitHub repository

    ```bash
    git clone https://github.com/Princeton-LSI-ResearchComputing/sprite-pipeline.git
    ```

2. Create and activate the required `sprite-pipeline` conda environment

    ```bash
    cd sprite-pipeline
    conda env create -f environment.yml
    conda activate sprite-pipeline
    ```

## Configuration

1. Create barcodes file `config.txt` (see `example_config.txt`).

2. Edit `config.yaml` - See [Setup
   `config.yaml`](https://github.com/GuttmanLab/sprite-pipeline/wiki/0.-Snakemake-Pipeline#2-setup-configyaml)
   on the wiki for more information.

    Note: Ensure the appropriate Bowtie2 index exists in the location indicated in the
   `config.yaml` file.

3. Create `samples.json` to identify input fastq files - See [Set samples to be
   processed](https://github.com/GuttmanLab/sprite-pipeline/wiki/0.-Snakemake-Pipeline#2-setup-configyaml)
   for more information.

    ```bash
    python fastq2json.py --fastq_dir <path_to_fastq_directory>
    ```

4. Setup Conda dependencies - Have Snakemake create any required conda
   environments. Note: While this step is optional (conda environments will be
   created as needed by Snakemake), doing it separately ensures there are no
   problems when running in cluster environments where individual nodes may not
   have the required internet access.

    ```bash
    snakemake --conda-create-envs-only --use-conda --configfile config.yaml --cores 1
    ```

## Run the pipeline

* Run the pipeline locally using 8 cores

    ```bash
    snakemake --use-conda --configfile config.yaml --cores 8
    ```

* Run the pipeline using `sbatch` and `cluster.yaml` configuration to submit jobs

    ```bash
    snakemake --use-conda --configfile config.yaml \
        --jobs 32 \
        --cluster-config cluster.yaml \
        --cluster "sbatch -c {cluster.cpus} \
        -t {cluster.time} -N {cluster.nodes} \
        --mem {cluster.mem} \
        --output {cluster.output} \
        --error {cluster.error}"


* Run the pipeline using a [cluster
  profile](https://snakemake.readthedocs.io/en/stable/executing/cli.html#profiles)
  called `slurm`

    When running on a cluster it is recommended that you create a [cluster
    profile](https://snakemake.readthedocs.io/en/stable/executing/cli.html#profiles)
    for specifying the various cluster options

    ```bash
    snakemake --profile slurm --use-conda --configfile config.yaml
    ```
