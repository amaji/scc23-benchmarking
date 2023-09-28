.. You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. .. |project_caps| replace:: '%s' % project

2023 Student Cluster Competition (SCC23) Benchmark submission instructions
==========================================================================

WARNING: These instructions have been copied from SCC22. They have not yet been updated for SCC23.

-----

Each team is allowed up to 5 hardware certification submission attempts. The SCC committee may at their discretion increase the allowable number of hardware certification submission attempts. Only one outstanding hardware certification submission attempt will be considered at a time.

Once a hardware certification has been submitted and verified, a team cannot modify their hardware or reboot any part of their cluster after submitting without invalidating their certification results. This would require the team to run the three required benchmarks (HPL, HPCG and MLPerf Inference) again in succession (any order) and recertify the result before the benchmark deadline in order to have a valid result. Only the last valid hardware certification result will be used in benchmarking scoring. This last certified hardware configuration will also be the hardware configuration used for the rest of the competition.


.. toctree::
   :maxdepth: 1
   :caption: Table of Contents:
   :numbered:
   :glob:

   benchmarks/general.rst
   benchmarks/hpl.rst
   benchmarks/hpcg.rst
   benchmarks/mlperf.rst
   benchmarks/optional.rst


.. Indices and tables
.. ==================

.. * :ref:`genindex`


