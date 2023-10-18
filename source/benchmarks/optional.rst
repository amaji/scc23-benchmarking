STREAM and OSU microbenchmark rules and validation
--------------------------------------------------

The secondary benchmarks (STREAM and OSU microbenchmarks) can be run at any time between Nov 12, 2023, 8:00 AM MDT and Nov 13, 2023, 5:00 PM MDT. You only need to run these once, but make sure to include the results with each certification submission.

STREAM
======
You can run STREAM on any single node within your cluster (hint: choose the node with the highest memory bandwidth).

**Files to submit**

- Output obtained by running STREAM in a file named ``cert-{N}-stream.rslts``
- Hardware and runtime information in a file named ``cert-{N}-stream.info``

    - Processor name
    - The sum (in MB) of last-level (L3) cache sizes used in the run
    - No. of cores used for STREAM run
    - Compiler and Compiler flags used for building STREAM
    - Array size in MB

- Timestamps for running STREAM in a file ``cert-{N}-stream.tstamps``

OSU Microbenchmarks
===================
You can run OSU microbenchmarks (``osu_latency`` and ``osu_bw``) between any two nodes in your cluster.

**Files to submit**

- Combine the output obtained by running ``osu_latency`` and ``osu_bw`` in a single file named ``cert-{N}-osu.rslts``
- Hardware and runtime information in a file named ``cert-{N}-osu.info``

    - Networking hardware details
    - Network bandwidth (as per specification)
    - Compiler used for building OSU microbenchmarks
    - Maximum bandwidth obtained
    - Latency with message size 4K

- Timestamps for running ``osu_latency`` and ``osu_bw`` in a file ``cert-{N}-osu.tstamps``
