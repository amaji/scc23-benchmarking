WARNING: These instructions have been copied from SCC22. They have not yet been updated for SCC23.
---

SCC22 Benchmarking Procedure

Each team is allowed up to 5 hardware certification submission attempts. The SCC committee may at their discretion increase the allowable number of hardware certification submission attempts. Only one outstanding hardware certification submission attempt will be considered at a time.

Once a hardware certification has been submitted and verified, a team cannot modify their hardware or reboot any part of their cluster after submitting without invalidating their certification results. This would require the team to run the three required benchmarks (HPL, HPCG and MLPerf Inference) again in succession (any order) and recertify the result before the benchmark deadline in order to have a valid result. Only the last valid hardware certification result will be used in benchmarking scoring. This last certified hardware configuration will also be the hardware configuration used for the rest of the competition.

A hardware certification submission consists of a team:
- Configuring their cluster hardware as they see fit.
- Running HPL, HPCG and MLPerf Inference in succession (in any order), following the rules notes below for each, and receiving valid results that do not violate the 3000W PDU power limit for the entirety of both runs and any time in between. The time in between any two benchmark runs must be no more than 30 minutes. For each benchmark, the team should capture:
	- Timestamps immediately before and after the run, in a file named like cert-${NUMBER}-${BENCHMARK}submission.tstamps. Teams can capture these timestamps by running:
	`echo ``date -u`` > cert-${NUMBER}-${BENCHMARK}submission.tstamps` immediately before the run, and 
	`echo ``date -u`` >> cert-${NUMBER}-${BENCHMARK}submission.tstamps` upon completion of the run (note the ">>" to append rather than overwrite the file).
	- The input file used, copied to a file named like `cert-${NUMBER}-${BENCHMARK}submission.input`
	- The output produced, copied to a file named like `cert-${NUMBER}-${BENCHMARK}submission.rslts` 
Where `${NUMBER}` corresponds to the team’s current hardware certification attempt (i.e. 1, 2, 3, 4, or 5), and `${BENCHMARK}` is one of "hpl", "hpcg", "mlperf", for example: cert-1-hpcgsubmission.tstamps
	- The team should also record the information listed in "Configuration Description" below, in a file named like `cert-${NUMBER}-configuration.txt`. This information is needed to form a valid top500 submission. Clarification: You can put the configuration description with the HPL input and rslts.


Optionally, running the MLPerf benchmark and capturing the input file (correction: the command line you used, corresponding to the command shown at "Prepare MLPerf submission" in the instructions) and stdout output produced, in three files named like mlperfsubmission.input, mlperfsubmission.output the stdout) and mlperfsubmission.zip with the three files (open.tar.gz, summary.csv, summary.json) that the run produced.
 
Note that MLPerf can be run with any certification attempt, or after the hardware has been certified, and a single successful run is sufficient to earn the associated bonus points. 
Clarification: MLPerf can be run at any time during the benchmarking session, it does not need to be part of a certification attempt

Instructions for running the MLPerf benchmark can be found at https://github.com/mlcommons/ck/blob/master/docs/tutorials/sc22-scc-mlperf.md 


Uploading all of the files described above (`cert-*-*submission.*, mlperfsubmission.*` and `cert-*-configuration.txt`) to the location designated by the SCC committee.

Within 10 minutes of completing the set of benchmark runs, sending one team member to alert their team liaison that they are ready to have their hardware configuration certified (you can do this before the upload is complete).

The team liaison or another SCC committee member will then inspect the files described above to verify that the runs were valid and in conformance with SCC Benchmarking rules. For in-person teams, the liaison will visually inspect and document the team’s cluster hardware configuration, and may ask questions to understand the hardware configuration and/or changes from one certification attempt to another. For the result to be valid, all of the team's hardware, including spare replacement machines, must be either in the cluster’s rack or on the table with the rest of the cluster’s hardware. If any hardware is later found that was not visible during certification then the certification will be invalidated. 

Judges will determine based on the timestamps for each run whether there is a spike in the power usage of the team that correlates with the time result of the benchmark. Power usage will be checked at 1 second intervals to ensure that teams do not exceed the 3000W limit in order to comply with Top500 and SCC rules.

If all results are valid, the runs have stayed below power limits, and the team has complied with the directions in this document plus any addendums made by the SCC committee, the team’s hardware configuration will be considered certified. If one of these is not met, the configuration will not be considered certified but will still count against a team’s limit of hardware configuration certification attempts.
Configuration Description

In order to comply with the Top500 requirements for power measurements, the `cert-${NUMBER}-configuration.txt` file should contain the following information from teams for each hardware certification:

1) Cluster Name
2) Model Name of the System, (e.g. Cray CS300 or HP Moonshot)
3) Vendor, (e.g. IBM)
4) Number of compute nodes in the cluster (e.g. 4 nodes)
5) Compute node processor name and mode (e.g. Intel Xeon Platinum 8180 Processor)
6) Sockets per compute node (e.g. 2)
7) Cores per socket (e.g. 24)
8) Processor speed (in Mhz)
9) Accelerator/Co-Processor. If you have different Accelerators/Co-Processors please specify only the model HPL was executed on (e.g. NVIDIA V100 PCIe 32 GB)
10) Accelerator(s)/Co-Processor(s) per node that HPL was executed on (e.g. 2 NVIDIA V100s in node 1 and 2 NVIDIA P100s in node 2)
11) Cores Per Accelerator/Co-Processor that HPL was executed on, for GPUs this is usually the number of shader clusters and not the total number of shaders. (e.g. 2688 cores per GPU)
12) System peak power used in watts (e.g. 2950W)
13) Number of compute node cores that HPL was executed on (e.g. 6 cores per node)
14) Primary Operating System and version (e.g. CentOS 7.5 1804)
15) Primary high speed network interconnect, (e.g. Mellanox EDR, OmniPath)
16) Memory per Compute node (in GB)
17) Origin of HPL binary (e.g. received from Mr. Bob Smith of NVIDIA, source code obtained from Intel and built with modification, etc.)

### HPL Rules and Validation
The HPL benchmark is described at https://www.top500.org/project/linpack/.

The HPL output shows validity by the following line:
```
||Ax-b||_oo/(eps*(||A||_oo*||x||_oo+||b||_oo)*N)=        0.0020152 ...... PASSED
```

The time output will look like the following for HPL:
```
T/V                N    NB     P     Q               Time                 Gflops
--------------------------------------------------------------------------------
WR01C2L8      102144   192     8     8             514.92              1.380e+03
```

There is no minimum run time associated with HPL.

### HPCG Rules and Validation

The HPCG run will produce a file named `HPCG-Benchmark_<version>_<date>.txt` You will need  to copy this file to your `.rslts` file. 

The HPCG output file shows validity by the following line:
```
HPCG result is VALID with a GFLOP/s rating of: [GFLOP/s]
```

The HPCG time will be visible in the output file as follows. For the run to be valid, the time value must exceed 1800 seconds (30 minutes):
```
########## Performance Summary (times in sec) ##########: 
Benchmark Time Summary: 
...
  Total: 2116.07
Floating Point Operations Summary: 
```

## MLPerf Rules and Validation

The MLPerf benchmark instructions are at https://github.com/mlcommons/ck/blob/master/docs/tutorials/sc22-scc-mlperf.md

The MLPerf benchmark this year is optional, and for bonus points. You will get the bonus points even if the certification you run it in is not your final certification.

