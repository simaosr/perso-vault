
# SLURM TEMPLATE FOR STARCCM+
```
#!/bin/bash
## Version 01/2020
## by Sebastian Engel
##
## Runs an array of jobs = one submission for x jobs
## Tailored to run StarCCM+ simulations
## expects a simdirs.csv containing relative paths starting from ROOTDIR to locate the sim files,
## one line per task.
## The sequence of tasks (which lines in simdirs.csv shall be run) has to be created manually.
## 
#################### Job Settings #################################################################
#SBATCH -J myJobArray         # Setting the display name for the submission
#SBATCH -N 1                  # Number of nodes to reserve, -N 2-5  for variable number of requested node count
#SBATCH --ntasks-per-node 16  # typically 16, range: 1..16 (max 16 cores per node)
#SBATCH -t 30:00              # set walltime in hours, format:    hhh:mm:ss, days-hh, days-hhh:mm:ss
#SBATCH -p short              # Desired Partition
#SBATCH --mem 100G            # Requested Memory. Neumann gives priority bonus under 120G 
#SBATCH --signal=B:USR1@180   # Sends a signal 180 seconds before the end of the job to this script,
							  # to write a stop file for StarCCM
#SBATCH --array=1-4           # Sequence of task IDs


#################### Simulation Settings ##########################################################
## Root directory for the job array to be run. No "/" at the end.
## It should be the directory where simdirs.csv is located.
ROOTDIR=/scratch/tmp/myusername

## Simulation file, selected by TASK ID given by SLURM. 
SIMULATIONFILE=$ROOTDIR/$(sed -n "${SLURM_ARRAY_TASK_ID}p" $ROOTDIR/simdirs.csv)

## Work directory. Filterd from the sim file path
WORKDIR=${SIMULATIONFILE}

## Macro file. Must be located in WORKDIR. Leave empty if no macro is used.
MACROFILE="macro.java"

## Personal POD key
PERSONAL_PODKEY="XXXXXXX"

## Decide which version by commenting out the desired version. 
#module load starCCM/11.06.011
#module load starCCM/12.02.011
#module load starCCM/13.02.013
module load starCCM/14.04.013

## Application. Can be kept constant if modules are used.
APPLICATION="starccm+"

## Select which options you need. Leave only the required options uncommented.
##
## you are using a macro and a sim file
#USROPT="$SIMULATIONFILE -batch $WORKDIR/$MACROFILE"
## you are using a macro and are creating a new sim file
#USROPT="-new -batch $WORKDIR/$MACROFILE"
## you want to just run the simulation
USROPT="$SIMULATIONFILE -batch run"

#################### Printing some Debug Information ##############################################
## Debug information
/cluster/apps/utils/bin/slurmProlog.sh 

#################### Signal Trap ##################################################################
## Catches signal from slurm to write an ABORT file in the WORKDIR.
## This ABORT file will satisfy the stop file criterion in StarCCM.
## Change ABORTFILENAME if you changed the stop file Criterion.
ABORTFILENAME="ABORT"
## Location where Starccm is looking for the abort file
ABORTFILELOCATION=$WORKDIR/$ABORTFILENAME

# remove old abort file
rm -rf $ABORTFILELOCATION
# Signal handler
write_abort_file()
{
		echo "$(date +%Y-%m-%d_%H:%M:%S) The End-of-Job signal has been trapped."
		echo "Writing abort file..."
		touch $ABORTFILELOCATION
}
# Trapping signal handler
echo "Trapping handler for End-of-Job signal"
trap 'write_abort_file' USR1

#################### Preparing the Simulation #####################################################
## creating machinefile 
MACHINEFILE="machinefile.$SLURM_JOBID.txt"
scontrol show hostnames $SLURM_JOB_NODELIST > $WORKDIR/$MACHINEFILE

## Default options plus user options
OPTIONS="$USROPT -mpi openmpi -licpath 1999@flex.cd-adapco.com -power -podkey $PERSONAL_PODKEY -collab -time -rsh /usr/bin/ssh"

## Let StarCCM+ wait for licenses on startup
export STARWAIT=1


#################### Running the simulation #######################################################
## Run application (StarCCM+) in background to allow signal trapping
echo "$(date +%Y-%m-%d_%H:%M:%S) Now, running the simulation ...."

## Command to run application (StarCCM+)
$APPLICATION $OPTIONS -np $SLURM_NPROCS -machinefile $WORKDIR/$MACHINEFILE > $SIMULATIONFILE.$SLURM_JOBID.output.log 2>&1 &
wait

## Final time stamp
echo "Simulation finalized at: $(date +%Y-%m-%d_%H:%M:%S_%s_%Z)" 

## Waiting briefly, to give starccm server processes time to quit gracefully.
sleep 120

## Clean-Up
/cluster/apps/utils/bin/slurmEpilog.sh 

echo "done."
```

# OTHER

```
#!/bin/bash
#  This is a sample job script for running STAR-CCM+
#SBATCH -J MyJobName
#SBATCH -D /work/mygroup/myproject
#SBATCH -N 4             # Number of nodes
#SBATCH -n 64            # Number of processors across all nodes
#SBATCH --ntasks-per-node=16
#SBATCH --partition=freecompute
#SBATCH --time=10:00:00
#SBATCH --error=MyJobName.%j.error
#SBATCH --output=MyJobName.%j.output
#SBATCH --mail-type=BEGIN,FAIL,END
#SBATCH --mail-user=username@iastate.edu

cd  /work/mygroup/myproject

# The commands below gets the list of compute nodes allocated to this job by Slurm and
# uses it to create a simple machine file which is just the list of compute nodes for
# this job.

MACHINEFILE=/work/mygroup/myproject/machinefile.$SLURM_JOBID
scontrol show hostname $SLURM_NODELIST > $MACHINEFILE

# Set the path to the STAR-CCM+ simulation file:
SIMFILEPATH=/work/mygroup/myproject/MyInput.sim

# Purge any loaded modules
module purge

# Load the starccm module.  Note: to see what versions are available, Type the command:

module load starccm/14.04.011-R8

# Use the following form for launching starccm+ if you use a Java script in addition to
# the simulation .sim file:
starccm+ -batch MyJava.java -np 60 -machinefile $MACHINEFILE $SIMFILEPATH

# Use the following for the launching starccm+ if you don't use a Java script to run the simulation:

starccm+ -batch -np 60 -machinefile $MACHINEFILE $SIMFILEPATH

module purge
```


# bbb
scontrol show job jobid

pando-visu..... /ganglia