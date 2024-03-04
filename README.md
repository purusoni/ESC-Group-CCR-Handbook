# ESC Group CCR Handbook (In Progress)

***Adopted from https://docs.ccr.buffalo.edu/en/latest/***

In this handbook, I will provide an overview of the resources in CCR and how to make a quick start. Then, I will structure an outline Q&A section and list the common questions and troubleshooting solutions.

## What is CCR?
“The Center for Computational Research (CCR) at the University at Buffalo is a high-performance research computing center offering faculty, staff, students, and local businesses access to supercomputing environments, high-end visualization services, an on-premise research cloud infrastructure, and experienced staff to help you move your research forward.” (source: https://docs.ccr.buffalo.edu/en/latest/) 

*TLDR: CCR is a high-performance research computing center at the University at Buffalo. We will use the computing nodes CCR offers to run our programs, and the project storage to store data and collaborate on projects.*

## What resources does CCR offer?
 
CCR offers a variety of resources, but only HPC Clusters and Project Storage are important to us. *(Rest can be found at https://docs.ccr.buffalo.edu/en/latest/available-resources/)*

### HPC Clusters

HPC stands for High Performance Computing and UB CCR provides bulk access to high performance CPUs and GPUs.

HPC has several partitions, out of which the most important ones are:

- **debug**: for debugging; virtually no queue wait time (Does not have GPUs)

- **general-compute**: Main partition; We'll use this most of the times; queue wait time depends on the resources requested and current CCR allocations.

- **scavenger**: Scavenge idle GPUs; your job would be cancelled as soon as the GPU owner starts his or her job; quick access to powerful GPUs if your job can be regularly checkpointed. (I use this with Weights & Biases Logging)

### Project Storage

CCR provides storage for faculty groups. All members of the group have access to it. We currently have 1TB group storage at `/projects/academic/wenyaoxu/`. 

Additinaly, CCR provides 10GB personal storage to each user. located at `/user/<username>/`. 


## QuickStart

For a brief overview for CCR you may watch https://www.youtube.com/watch?v=ryBqdeqTO4o. I would not cover the topics already covered in the video.

1. Create an CCR account at https://idm.ccr.buffalo.edu/signup
2. Share your CCR account with faculty so that your account can be granted access.
3. Set up SSH keys by following the guide at https://docs.ccr.buffalo.edu/en/latest/hpc/login/
4. 