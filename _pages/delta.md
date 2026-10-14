# Using NCSA Delta

For more information, see the [complete Delta user guide](https://docs.ncsa.illinois.edu/systems/delta/en/latest/index.html).

## Logging in

1. Create an account with NSF ACCESS at [access-ci.org](access-ci.org).
2. Tell Prof. Ventura your username and ask him to add you to the relevant ACCESS allocation.
3. To login via SSH: `ssh <username>@login.delta.ncsa.illinois.edu`
4. Enter your password, and then at the next prompt enter "1" and complete multi-factor authentication using the Duo app on your phone.

## Using VS Code

I recommend you use VS Code to connect to Delta rather than SSH via the terminal.

1. Use "Remote-SSH: Add New SSH Host" to set up the Delta connection.
2. Once the host has been added, use "Remote-SSH: Connect Current Window to Host" and select Delta.
3. You will need to enter your password and then do multi-factor authentication as described above each time you log in.

## Setting up a Python environment

I recommend using `conda` to create a Python environment and install dependencies for your project.  Be sure to activate the conda environment before running any batch jobs.

## Downloading data to Delta

You should not use `scp` to move data to Delta or run long downloads through the login node.

One option is to a CPU batch job to download data, for example using `wget` or `curl` or the Kaggle CLI.

Alternatively, you can use Globus Connect to transfer data to Delta:

1. Install [Globus Connect Personal](https://www.globus.org/globus-connect-personal) onto your personal machine.
2. Start the app and login with your credentials
3. Login to the [Globus web interface](https://www.globus.org) to set up transfer jobs between your machine and Delta.
   
## Running jobs

You need to know your project ID, which can be found by running `accounts`.  The project ID is the four letter code before `-delta-cpu` or `-delta-gpu`.

## Running a batch job

Any significant task or computation needs to be run either as a batch job or in an interactive session (see below).

Please choose the least expensive partition and configuration that meets your requirements.  The partition types and their charge factors are listed [on this page](https://docs.ncsa.illinois.edu/systems/delta/en/latest/user_guide/running_jobs.html).  GPU jobs are more expensive than CPU, and the higher-end GPUs are more expensive than the lower-end ones.

To run a batch job, you need to make a `.slurm` file that contains the job configuration and the commands to run.

To queue the job, use `sbatch <filename>.slurm`.

You can check the status of jobs you have submitted with: `queue -u <username>`

Here is an example Slurm file for a CPU job:

```sh
#!/bin/bash
#SBATCH --job-name="<job name>"
#SBATCH --partition=cpu
#SBATCH --mem=50G
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=1
#SBATCH --cpus-per-task=1
#SBATCH --constraint="scratch"
#SBATCH --account=<project>-delta-cpu
#SBATCH -t 04:00:00
#SBATCH -e sout/slurm-%j.err
#SBATCH -o sout/slurm-%j.out

srun <your command here>
```

Here is an example for a GPU job:

```sh
#!/bin/bash
#SBATCH --job-name="<job name>"
#SBATCH --partition=<partition: could be gpuA40x4,gpuA100x4,gpuA100x8, or gpuH200x8>
#SBATCH --mem=50G
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=1
#SBATCH --cpus-per-task=16
#SBATCH --constraint="scratch"
#SBATCH --gpus-per-node=<number of gpus>
#SBATCH --gpu-bind=closest
#SBATCH --account=<project>-delta-gpu
#SBATCH -t 04:00:00
#SBATCH -e sout/slurm-%j.err
#SBATCH -o sout/slurm-%j.out

srun <your command here>
```

## Starting an interactive session

Interactive sessions are more expensive than batch jobs and are limited to one hour per session and one session at a time.  But, they can be useful for debugging your code before you set up a long run.

To start an interactive CPU session for 30 minutes:

```sh
#!/bin/bash
PROJECT=<project id>
srun --mem=16g \
     --nodes=1 \
     --ntasks-per-node=1 \
     --cpus-per-task=16 \
     --partition=cpu-interactive  \
     --account=${PROJECT}-delta-cpu \
     --time=00:30:00 \
     --pty \
     /bin/bash
```

To start an interactive GPU session for 30 minutes:

```sh
#!/bin/bash
PARTITION=<partition: could be gpuA40x4,gpuA100x4,gpuA100x8, or gpuH200x8>
PROJECT=<project id>
srun --mem=16g \
     --nodes=1 \
     --ntasks-per-node=1 \
     --cpus-per-task=16 \
     --gpus-per-node=1
     --partition=${PARTITION}-interactive  \
     --account=${PROJECT}-deltapcu \
     --time=00:30:00 \
     --pty \
     /bin/bash
```






