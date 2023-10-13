HPCG Rules and Validation
-------------------------

The HPCG run will produce a file named ``HPCG-Benchmark_<version>_<date>.txt`` You will need  to copy this file to your ``.rslts`` file. 

The HPCG output file shows validity by the following line:

.. code-block:: bash

   HPCG result is VALID with a GFLOP/s rating of: [GFLOP/s]

The HPCG time will be visible in the output file as follows. For the run to be valid, the time value must exceed 1800 seconds (30 minutes):

.. code-block:: bash

   ########## Performance Summary (times in sec) ##########: 
   Benchmark Time Summary: 
   ...
   Total: 2116.07
   Floating Point Operations Summary: 

**Files to submit**

- HPCG output saved to a file ``cert-{N}-hpcg.rslts``
- HPCG input file (``HPCG.dat``) saved to a file ``cert-{N}-hpcg.input``
- HPCG run timestamps saved to a file ``cert-{N}-hpcg.tstamps``
