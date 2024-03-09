# Batch Jobs
*Adopted from https://docs.ccr.buffalo.edu/en/latest/*

*When using the guide, if you think some information should be added, please let me, Puru Soni, know on slack. If you prefer to directly contribute to the handbook please start a pull request*

---


These are the most common type of jobs. They are meant to be self contained.

Example:

```sh
 1| #!/bin/bash -l             # Must include this
 2| #SBATCH --time=70:00:00    # Hours requested.
 3| #SBATCH --nodes=1          # Number of nodes
 4| #SBATCH --mem=130G         # Memory Requested
 5| #SBATCH --job-name="multimodal_wandb_grid_search_sweep"
 6| #SBATCH --output="/output_files/slurm-multimodal_wandb_grid_search_sweep-%j.out"
 7| #SBATCH --mail-user=purusoni@buffalo.edu
 8| #SBATCH --mail-type=ALL
 9| #SBATCH --gres=gpu:a100-pcie-40gb:1   # Type of GPU requested
10| #SBATCH --partition=general-compute   # Partition
11| #SBATCH --qos=general-compute         # Same as Partition
12| #SBATCH --cluster=ub-hpc              # Cluster to run the job on (ub-hpc)
13| 
14| 
15| echo "On node: "`/usr/bin/uname -n`
16| 
17| # Load EasyBuild Modules
18| module load cuda/11.8.0
19| module load gcc/11.2.0
20| module load openmpi/4.1.1
21| module load python/3.9.6
22| module load tensorflow
23| module load numba/0.54.1
24|
25| # Execute the program
26| python multimodal_wandb_grid_search_sweep.py
```

Explanation

1. `#!/bin/bash -l`: Required as the first line for every Batch Job Script.
2. `#SBATCH --time=70:00:00`: Hours Requested. Format is DD-HH:MM:SS. Different partition have different max hours allowed. Image from UB CCR Website. ![Time Limits](images/Cluster%20Time%20Limits.png)
> Steps 3-5 are self explanatory.

6. `#SBATCH --output="/output_files/slurm-multimodal_wandb_grid_search_sweep-%j.out"`: I would reccomned including `%j` in the name for the output files so all you jobs, even the ones that use the same script, can have different output file. This makes it easier to debug. Slurm fills in `%j` with the actual JobID.
> Steps 7-8 are self explanatory.
9. `#SBATCH --gres=gpu:a100-pcie-40gb:1`: This is one of the ways to request a GPU though Slurm. Here I requested an single A100 with 40 GB of VRAM. Some other common GPU options for CCR are:
    - `gpu:a100-pcie-40gb:2`: Request two A100 attached to the same node. A node in CCR has a maximum of two GPUs. For more that 2 GPUs, you would have to request multiple nodes (line 3).
    - `gpu:tesla_v100-pcie-32gb:1 (or 2)`: One (or Two) NVIDIA V100 with 32GB VRAM.
    - `gpu:tesla_v100-pcie-16gb:1 (or 2)`: One (or Two) NVIDIA V100 with 16GB VRAM.
    - `gpu:nvidia_h100:1 (or 2)`: One (or Two) NVIDIA V100 with 16GB VRAM.
10. `#SBATCH --partition=general-compute`: The partition you want you job to run on. [More info here](README.md#what-resources-does-ccr-offer).
11. `#SBATCH --qos=general-compute`: Almost always the same as the partition name.
12. `#SBATCH --cluster=ub-hpc`:  Almost always `ub-hpc`.
13. After that you can start writing the actual script. An important part of the using CCR is loading the right software in the right way. [More info about software here](Software.md).

Addition Options are Detailed on the [CCR Website](https://docs.ccr.buffalo.edu/en/latest/hpc/jobs/)

## Submitting the Script
Run `sbatch path/to/script`. The script file should end with `.slurm.script`

## Monitoring Status
[See Here](README.md#run-jobs--access-the-nodes)

## Monitoring Node Resource Utilization
[Use OnDemand](README.md#ondemand-portal)