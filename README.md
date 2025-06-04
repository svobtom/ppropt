# PPROpt
PPRopt is a Python application for the fast protein structure optimisation. It is rapid alternative to protein structure optimisation with constrained alpha carbons. During the PPROpt method, the entire structure is not optimised at once but individual residues are optimised sequentially. The main advantage of such approach is its linear time complexity with respect to the number of atoms. 

## How to install
To run PPROpt optimisation you will need to have [Python 3.12](https://www.python.org/downloads/) and package manager  [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html) installed.

Then, clone project and install the project dependencies by running:

```bash
$ git clone https://github.com/sb-ncbr/ppropt
$ conda install biopython=1.81 xtb=6.6.1
```

## How to run
Run the PPROpt optimisation by running the following command inside github repository:

```bash
$ python3.12 ppropt.py --cpu 1 --PDB_file example/AF-P0DL07-F1-model_v4_protonated_ph7.pdb --data_dir test --run_full_xtb_optimisation
```

## How to run in Docker container
If you prefer to run PPROpt in a Docker container, you can do so by following these steps:
```bash
# build image
docker build -t local/ppropt .

# or pull the image from our Docker registry
docker pull cerit.io/ceitec-biodata-pub/ppropt:latest

# create folder to store results (the folder must be empty)
mkdir results

# run the container with the PPROpt
docker run --rm --name PPRopt \
    -v ./example:/opt/ppropt/example \
    -v ./results:/opt/ppropt/results \
    local/ppropt \
    ppropt.py --cpu 1 --PDB_file example/AF-P0DL07-F1-model_v4_protonated_ph7.pdb --data_dir results --run_full_xtb_optimisation
```

## License
MIT
