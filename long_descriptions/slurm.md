# Slurm

- `srun --ntasks=42 script.sh` allocates 42 tasks and runs the job in your terminal. The default is one task per node.
- `srun --ntasks=42 --pty bash` allocates 42 tasks and starts an interactive session. Use `exit` to exit the interactive session.
- `sbatch --ntasks=1 script.sh` allocates and runs script. script gets _copied_ to an other location and is executed, once there are enough resources available. In contrast to `srun` the script is _only_ run on the first node! You can use `srun` inside the batch script.
- `squeue` to see the current jobs in the job queue.
- `scancel` to kill your jobs or revoke them from the queue.
- `salloc --ntasks=42` allocate recources for yourself, but stay on login node. If you want to use the recources use `srun` afterwards. Useful if one job contains multiple `srun` commands, as you don't have to reallocate recources for each job. Use `exit` to exit the allocation.
- Use `--job-name="Bob"` to give your job a descriptive name.
- Use `--time=8:00:00` to set the upper limit for the runtime of your program.
- If you run a batch script with `srun` or `sbatch` you can also define the command line parameters inside the script using `##SBATCH --ntasks=42`.

```bash
srun -n4 hostname ## runs hostname on four nodes
## prints allocated compute nodes

salloc -n4 ## allocate four nodes
  hostname
  ## print the current login node
  srun hostname ## runs hostname on all allocated nodes
  ## prints allocated compute nodes
  srun -n2 hostname ## runs hostname on two of the allocated nodes
  ## prints allocated compute nodes
exit

echo -e '##!/usr/bin/env bash\nhostname' > script.sh
sbatch -n4 script.sh ## submits the script
## returns immediately and stores the output of the job into a file
## output file contains only the host name for the first node

echo -e '##!/usr/bin/env bash\nsrun hostname' > script.sh
sbatch -n4 script.sh ## submits a script to run hostname on four nodes
## returns immediately and stores the output of the job into a file
## output file contains the host names for all compute nodes

echo -e '##!/usr/bin/env bash\n##SBATCH -n4\n##SBATCH --output myoutfile\nsrun hostname' > script.sh
sbatch script.sh
## prints the host name of all four allocated nodes into `myoutfile`
```

Some more advanced stuff:

- Slurm sets various environment variables which you can use in your scripts.
- You can queue multiple versions of one `sbatch` job using [task arrays](https://slurm.schedmd.com/job_array.html) with `--array=0-17`. You can use the environment variable `SLURM_ARRAY_TASK_ID` in your scripts to find out which array task you are executing.

```bash
## program we want to run with different parameters
echo "sleep 3;echo $1" > smartprogram.sh
## batch script which uses the array id to change the parameters
echo -e '##!/usr/bin/env bash\nsrun bash smartprogram.sh $SLURM_ARRAY_TASK_ID' > script.sh
## run a program multiple times
sbatch -n1 --array=3-5 script.sh
## outputs the numbers 3,4 and 5 in three output files
```
