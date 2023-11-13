General submission instructions
-------------------------------

A hardware certification submission consists of a team:

1. Configuring their cluster hardware as they see fit.
2. Running HPL, HPCG and MLPerf-BERT Inference in succession (in any order), following the rules noted below for each, and receiving valid results that do not violate the 4000W compute power limit for the entirety of benchmark runs and any time in between. *Note that for SCC23, there is also a per-node power limit of 2000W, implying that the power consumption by any single node must not exceed 2000W when the benchmarks are run.* The time in between any two core benchmark runs must be no more than 30 minutes. For each benchmark, the team should capture:

   - Timestamps immediately before and after the run, in a file named like ``cert-${NUMBER}-${BENCHMARK}.tstamps``.  Here, ``${NUMBER}`` corresponds to the team’s current hardware certification attempt (i.e. ``1``, ``2``, ``3``, ``4``, or ``5``), and ``${BENCHMARK}`` is one of ``hpl``, ``hpcg``, ``mlperf``, for example: ``cert-1-hpcg.tstamps`` Teams can capture these timestamps by running:

	``echo `date -u` > cert-${NUMBER}-${BENCHMARK}.tstamps`` immediately before the run, and 
	``echo `date -u` >> cert-${NUMBER}-${BENCHMARK}.tstamps`` upon completion of the run (note the ``>>`` to append rather than overwrite the file). 

   - The input file used, copied to a file named like ``cert-${NUMBER}-${BENCHMARK}.input``
   - The output produced, copied to a file named like ``cert-${NUMBER}-${BENCHMARK}.rslts``. 
   - The script used to run the benchmark (or the sequence of commands), copied to a file named like ``cert-${NUMBER}-${BENCHMARK}.run``. 
   - For HPL, The team should also record the information listed under the section :ref:`Configuration file<Configuration file>` below, in a file named like ``cert-${NUMBER}-configuration.txt``. This information is needed to form a valid `top500 submission <https://top500.org/>`_ and must be submitted with the HPL input and results files.

3. **In general, teams must use at least 2 nodes for running HPL and HPCG and 1 or more nodes for running MLPerf Inference.** An exception to this rule may be granted if (you have hardware that cannot be physically reconfigured) AND (you have only one node containing GPUs) AND (the power consumption for the GPU node is within the 2000W power limit). In this scenario, please contact the SCC23 committee and get approval to use 1 node for HPL and HPCG.

4. Running STREAM and OSU microbenchmarks at any time before or during the certification runs and including the corresponding ``*.rslts``, ``*.run``, ``*.tstamps``, and ``*.info`` files with the other benchmark results. *Check the details for each benchmark to see what information must be included.*
5. Uploading all of the files described above (``cert-*-*.*``, and ``cert-*-configuration.txt``) to the file server designated by the SCC committee. Teams are encouraged to organize their results into separate directories for each benchmark. An example is shown below.

     .. code-block::

	cert1-submission/
	|-- hpcg
	|   |-- cert-1-hpcg.input
	|   |-- cert-1-hpcg.rslts
	|   |-- cert-1-hpcg.run
	|   `-- cert-1-hpcg.tstamps
	|-- hpl
	|   |-- cert-1-configuration.txt
	|   |-- cert-1-hpl.input
	|   |-- cert-1-hpl.rslts
	|   |-- cert-1-hpl.run
	|   `-- cert-1-hpl.tstamps
	|-- mlperf
	|   |-- mlperf_submission_short.tar.gz
	|   |-- mlperf_submission_short_summary.json
	|   |-- mlperf_submission_short.run
	|   |-- mlperf_submission_short.tstamps
	|   |-- mlperf_submission_short.md
	|   |-- mlperf_submission_1.tar.gz
	|   |-- mlperf_submission_1_summary.json
	|   |-- mlperf_submission_1.run
	|   |-- mlperf_submission_1.tstamps
	|   `-- mlperf_submission_1.md
	|-- osu
	|   |-- cert-1-osu.info
	|   |-- cert-1-osu.rslts
	|   |-- cert-1-osu.run
	|   `-- cert-1-osu.tstamps
	`-- stream
	    |-- cert-1-stream.info
	    |-- cert-1-stream.rslts
	    |-- cert-1-stream.run
	    `-- cert-1-stream.tstamps

6. Within 10 minutes of completing the set of benchmark runs, sending one team member to alert the SCC committee (ideally via their team liaison) that they are ready to have their hardware configuration certified (you can do this before the upload is complete).

The team liaison or another SCC committee member will then inspect the files described above to verify that the runs were valid and in conformance with the SCC23 Benchmarking rules. The team liaison or the benchmarking judges will visually inspect and document the team’s cluster hardware configuration, and may ask questions to understand the hardware configuration and/or changes from one certification attempt to another. For the result to be valid, all of the team's hardware, including spare replacement machines, must be either in the cluster’s rack or on the table with the rest of the cluster’s hardware. If any hardware is later found that was not visible during certification then the certification will be invalidated. 

Judges will determine based on the timestamps for each run whether there is a spike in the power usage of the team that correlates with running the benchmark. Power usage will be checked at 1 second intervals to ensure that teams do not exceed the power budget (maximum of 2000W per node and 4000W total for all nodes in the cluster) in order to comply with Top500 and SCC rules.

If all results are valid, the runs have stayed below power limits, and the team has complied with the directions in this document plus any addendums made by the SCC committee, the team’s hardware configuration will be considered certified. If one of these is not met, the configuration will not be considered certified but will still count against a team’s limit of hardware configuration certification attempts.

.. _Configuration file:

Configuration file description
------------------------------

In order to comply with the Top500 requirements for power measurements, the ``cert-${NUMBER}-configuration.txt`` file should contain the following information from teams for each hardware certification:

	1) Cluster Name
	2) Model Name of the System, (e.g. Cray CS300 or HP Moonshot)
	3) Vendor, (e.g. IBM)
	4) Number of compute nodes in the cluster (e.g. 4 nodes)
	5) Compute node processor name and mode (e.g. Intel Xeon Platinum 8180 Processor)
	6) Sockets per compute node (e.g. 2)
	7) Cores per socket (e.g. 24)
	8) Processor speed (in Mhz)
	9) Accelerator/Co-Processor. If you have different Accelerators/Co-Processors please specify only the model HPL was executed on (e.g. NVIDIA V100 PCIe 32 GB)
	10) Number and type of accelerator(s)/co-processor(s) per node that HPL was executed on (e.g. 2 NVIDIA V100s in node 1 and 2 NVIDIA P100s in node 2)
	11) Cores Per Accelerator/Co-Processor that HPL was executed on, for GPUs this is usually the number of shader clusters and not the total number of shaders. (e.g. 2688 cores per GPU)
	12) System peak power used in watts, including networking equipment (e.g. 2950W)
	13) Number of compute node cores that HPL was executed on (e.g. 6 cores per node)
	14) Primary Operating System and version (e.g. CentOS 7.5 1804)
	15) Primary high speed network interconnect, (e.g. Mellanox EDR, OmniPath)
	16) Memory per Compute node (in GB)
	17) Origin of HPL binary (e.g. received from Mr. Bob Smith of NVIDIA, source code obtained from Intel and built with modification, etc.)

Synchronizing your system clock
-------------------------------
An important aspect of configuring your cluster is to ensure that all nodes in the cluster uses the same time. Teams are strongly encouraged to synchronize the system clocks across their clusters using NTP. SC23 provides an NTP server at: ``ntp.scconf.org`` . Please use the command ``ntpdate ntp.scconf.org`` to update your clocks against this server or set up automatic clock synchronization. The purpose of this is to make sure that your cluster is using the local timezone at the conference venue (Mountain Standard Time at Denver, Colorado) and your clock is synchronized with the sever monitoring your power consumption. **Without proper clock synchronization it may take significantly longer to validate your results.** Teams will not be allocated additional time due to delays in validation/certification arising due to clock skew. 
