# Great Lakes Tutorial
This is instruction on how to use GPU in greatlakes


[Great Lakes User Guide](https://arc-ts.umich.edu/greatlakes/user-guide/)



[Cheat Sheet](https://docs.google.com/document/d/1wsr3yzkkojUMBCCneCz-l413xBzU-SZFAqcFrAAjttk/export?format=pdf)


## Virtual Environment:

Great Lakes hasn't yet installed deep learning framework like PyTorch or Tensorflow. If you would like to use them or install some external package like pytorch-pretrained-bert or tqdm. You need to set one virtual environment to get permission to install them under your own folder.

Create the virtual env
`virtualenv -p python3 your_env_name` 

Activate your virtual env
`source your_env_name/bin/activate`

Deactivate current virtual env
`deactivate your_env_name`

Then you will get full permission of your folder to git clone repository or install what ever framework you want directly.

## Bash Script:

All tasks run in GreatLakes should be submitted in form of Bash Script similar to the command in terminal. You can refer the Cheat Sheet of Great Lakes to settle your commands.

Here is one example to use GPU. 

```
#!/bin/sh

#SBATCH --job-name= your_job_name

#SBATCH --account=vgvinodv
#SBATCH --partition=gpu 

#SBATCH --mail-user=youremail@umich.edu
#SBATCH --mail-type=BEGIN,END

#SBATCH --nodes=1
#SBATCH --gres=gpu:1
#SBATCH --mem=20G
#SBATCH --time=10:00:00

source ./your_env_name/bin/activate

python  your_code.py
```

Some instructions:
1. `#SBATCH --job-name= your_job_name` Give a name of your job.
2. `#SBATCH --partition=gpu ` For partitions, you can choose gpu,standard,viz,largemem for different useage.
3. `#SBATCH --mail-user=youremail@umich.edu` Set one email address to get notification of your job status.
  or you can use `squeue -u uniquename` to list all your jobs.
4. `#SBATCH --nodes=1`  Choose number of nodes you want.
5. `#SBATCH --gres=gpu:1` number of Gpu for this node, remember to remove this command when you use CPU only
6. `#SBATCH --time=10:00:00` max time you want to use this node, job will be ended anyway even if job hasn't been finished.

7. `source ./your_env_name/bin/activate` You need to activate your virtual environment to settle the env you want. You need to adjust the path based on your folder structure. 
For this bashfile, they are all in same level.
```
-your_env_folder
-your_code.py
-bashfile.sh
-xxxxx.out
```
8. You can see the log information or error traceback helping debug in jobnumber.out under the same folder of your bashfile.


## Actions command:

`sbatch xxx.sh` submit your bashfile

`squeue -u uniquemane` check your jobs status

`scancel jobid` delete your job, you will get one jobid after you submit.

More in Cheat sheet

## Document Management GUI on Mac

I recommand Cyberduck for document management uploading, downloading,etc.
When setting connections, use `FTP` protocal , server name `greatlakes.arc-ts.umich.edu` , your unique name and password.

