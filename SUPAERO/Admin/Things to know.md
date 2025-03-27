# Websites
- https://iris.isae.fr - main webpage to access others
- https://pando-visu.isae.fr - access to virtual machines on the PANDO cluster
- https://icare.isae.fr - access to some shell which gives access to files... (??)
- https://gitlab.isae-supaero.fr - Gitlab da Supaero
- https://nextcloud.isae.fr - Cloud storage

# Information aboud PANDO
https://iris.isae.fr/pando-comment-debuter-sur-le-supercalculateur?lang=en

* **/home/daep/s.santos**: it is your local home on the supercomputer, it is accessible from the access nodes and all computing nodes. The default quota for users is 50GB.
* **/scratch/daep/s.santos**: it’s a fast parallel storage space. The I/O speed are higher on this file system. The default quota for users is 100GB. (**not backed up!**)

> The two spaces previously described have two different vocations, the space “home” is a permanent space, it must be privileged to place codes that you compile/install yourself.
The “scratch” space is a fast storage space, it should be used for the input/output files of your jobs. It is particularly effective for applications having a lot of writing/reading on disk to use this storage space because these performances are much better.

- **To move files from and to PANDO**: $ scp

- Pando cheat sheet: https://iris.isae.fr/IMG/pdf/pando_cheat_sheet_en.pdf

## Executing code in PANDO

The execution of a calculation code must be done on the compute nodes. Access to these compute nodes is done using PANDO job scheduler: **Slurm**.
Two modes are available :

* Batch mode (via a submission script)
* Interactive mode

```
#SBATCH --nodes=4
#SBATCH --ntasks=96
#SBATCH --ntasks-per-node=24
#SBATCH --time=24:00:00
#SBATCH --begin=now
#SBATCH --job-name=starccm_run
#SBATCH --output=slurm.%j.out
#SBATCH --error=slurm.%j.err
```


- **NODES**: Request that a minimum of minnodes nodes be allocated to this job. A maximum node count may also be specified with maxnodes. If only one number is specified, this is used as both the minimum and maximum node count.

- **NTASKS**: sbatch does not launch tasks, it requests an allocation of resources and submits a batch script. This option advises the Slurm controller that job steps run within the allocation will launch a maximum of number tasks and to provide for sufficient resources. The default is one task per node, but note that the --cpus-per-task option will change this default. 

- **NTASKS-PER-NODE**: Request that ntasks be invoked on each node. If used with the --ntasks option, the --ntasks option will take precedence and the --ntasks-per-node will be treated as a maximum count of tasks per node. Meant to be used with the --nodes option. 

# Running Python scripts in PANDO

# PANDO MODULES
`module load python/3.7`
`module load starccm/13.04`

# CONDA ENVIRONMENT (IMOTHEP)
(in pando, it is activated with `source activate imothep`)

`conda install -c dlr-sc tigl3`



