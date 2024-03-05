# Batch Jobs
*If you want to contributing to the handbook please start a pull request*

---
***Adopted from https://docs.ccr.buffalo.edu/en/latest/***


These are the most common type of jobs. They are meant to be self contained.

Example:
```sh
#!/bin/bash -l             # Must include this
#SBATCH --time=70:00:00    # Hours requested.
#SBATCH --nodes=1          # Number of nodes
#SBATCH --mem=130G         # Memory Requested
#SBATCH --job-name="multimodal_wandb_grid_search_sweep"
#SBATCH --output="/output_files/slurm-multimodal_wandb_grid_search_sweep-%j.out"
#SBATCH --mail-user=purusoni@buffalo.edu
#SBATCH --mail-type=ALL
#SBATCH --gres=gpu:a100-pcie-40gb:1   # Type of GPU requested
#SBATCH --partition=scavenger         # Partition
#SBATCH --qos=scavenger               # Same as Partition
#SBATCH --cluster=ub-hpc              # Cluster to run the job on (ub-hpc)


echo "On node: "`/usr/bin/uname -n`

# Load EasyBuild Modules
module load cuda/11.8.0 
module load gcc/11.2.0   
module load openmpi/4.1.1
module load python/3.9.6
module load tensorflow
module load numba/0.54.1

# Execute the program
python multimodal_wandb_grid_search_sweep.py
```


