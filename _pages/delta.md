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

## Running jobs

You need to know your project ID, which can be found by running `accounts`

## Running a batch job

Any significant task or computation needs to be run either as a batch job or in an interactive session (see below).

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

srun python3 run_all_scenes.py
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






