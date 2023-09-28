HPCG Rules and Validation
-------------------------

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

