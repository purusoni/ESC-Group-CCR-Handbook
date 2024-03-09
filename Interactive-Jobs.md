# Interactive Jobs
*Adopted from https://docs.ccr.buffalo.edu/en/latest/*

*When using the guide, if you think some information should be added, please let me, Puru Soni, know on slack. If you prefer to directly contribute to the handbook please start a pull request*

---

Interactive jobs are similar to the Lab Server. You can connect to a node in a manner similar to ssh-ing into the lab server.


## Launching an Interactive Job
The launch an interactive job, use the command `salloc` with suitable configuration.

Example:
```bash
salloc --qos=general-compute --partition=general-compute --job-name "Example" --mem=50G --time=48:00:00 --gpus-per-node=a100-pcie-40gb:1
```

where the configuration is similar in semantics to [Batch Job Configuration](Batch-Jobs.md)

## Attaching to an already running Interactive Job

A lot of times, for various reason, your ssh connection might terminate. To connect back to the Interactive Node,
1. Connect back to [CCR login node through ssh](README.md#quickstart).
2. Run `squeue -u <username>` and find the **JobID** of the Interactive Job you want to connect to.
3. Run `srun --jobid=<JobID> --pty /usr/bin/bash`. The terminal would connect to the Interactive Job.