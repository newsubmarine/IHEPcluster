# IHEPCluster
Manual: http://afsapply.ihep.ac.cn/cchelp/

## Quick start

### Account Application 

- https://login.ihep.ac.cn/afsApply.jsp
  - Identify: 外籍人员（Foreign personnel); 
  - Department: 所外; 
  - Experiment: ATLAS; 
  - Group: atlas.
  - Contact Person Information: Yaquan Fang; fangyq@ihep.ac.cn
  
### Login Cluster
```Bash
$ ssh username@lxslc7.ihep.ac.cn
```

### Systematic samples will be saved in  
```Bash
/publicfs/atlas/atlasnew/higgs/HHML 
```


### Pesonal disk space 
- AFS home directory: /afs/ihep.ac.cn/users/a-z/username; 500MB
- User personal files: /workfs2/atlas/username; 5GB
- User temporary files: /scratchfs/atlas; 500GB, keep in 2 Weeks
- ATLAS shared disk: /publicfs/atlas/; several hundred GB

One have to make a directory he/her self if his/her directory isn't automatic created: mkdir 
### HTCondor jobs
- Setup
```Bash
$ export PATH=/afs/ihep.ac.cn/soft/common/sysgroup/hep_job/hep_job.sl7/bin/:$PATH
```
- Jobs submission
```Bash
$ chmod +x job.sh
$ hep_sub job.sh # Submit job
$ hep_q -u username # Job query
$ hep_rm -a # delete all current jobs
```
- Detailed guide http://afsapply.ihep.ac.cn/cchelp/en/local-cluster/jobs/HTCondor/

### Running gn2 framework jobs on IHEP cluster using HTCondor

To submit jobs using ATLAS environment，the setup has to be embodied in the job script. Do not setupATLAS directly in shell!
```Bash
$ cat job.sh
----------------------------
#!/bin/bash
###ALTAS environment
export ATLAS_LOCAL_ROOT_BASE=/cvmfs/atlas.cern.ch/repo/ATLASLocalRootBase
alias setupATLAS='source ${ATLAS_LOCAL_ROOT_BASE}/user/atlasLocalSetup.sh'
setupATLAS

python fw2_hhml.py -o output.root -s branchList.txt <rootFile1>,<rootFile2>

```


