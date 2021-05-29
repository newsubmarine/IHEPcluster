# IHEPCluster
Manual: http://afsapply.ihep.ac.cn/cchelp/

## Quick start

### Account Application 

- https://login.ihep.ac.cn/afsApply.jsp
  - Identify: 外籍人员（Foreign ersonnel); Department: 所外; Experiment: ATLAS; Group: atlas
  
### Login Cluster
```Bash
$ ssh –l username lxslc7.ihep.ac.cn
```
### HTCondor jobs
- Setup
```Bash
$ export PATH=/afs/ihep.ac.cn/soft/common/sysgroup/hep_job/hep_job.sl7/bin/:$PATH
```
- Submitting Jobs
```Bash
$ chmod +x job.sh
$ hep_sub job.sh # Submit job
$ hep_q -u username # Job query
$ hep_rm -a # delete all current jobs
```

- Running gn2 framework jobs on grid

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


