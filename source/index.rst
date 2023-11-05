.. You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. .. |project_caps| replace:: '%s' % project

2023 Student Cluster Competition (SCC23) benchmark submission instructions
==========================================================================

During the 2023 Student Cluster Competition (SCC23), each team is required to run three core benchmarks (HPL, HPCG, and MLPerf-BERT Inference) and two secondary benchmarks (STREAM and OSU Microbenchmarks). The core benchmarks must be run during the benchmarking window of 8:00am--5:00pm MDT on Nov 13 (Mon), 2023, and must be run with the same hardware configuration. The secondary benchmarks can be run at any time between Nov 12, 2023, 8:00am MDT and Nov 13, 2023, 5:00pm MDT, and have no hardware configuration constraint except the power limit rules. All benchmark results must be submitted together following the instructions given below. The benchmark results submission process is also referred to as "hardware certification" in the rest of the document.

Each team is allowed up to 5 hardware certification submission attempts. The SCC committee may at their discretion increase the allowable number of hardware certification submission attempts. Only one outstanding hardware certification submission attempt will be considered at a time.

Once a hardware certification has been submitted and verified, a team cannot modify their hardware configuration (for example, power on additional nodes or shutdown existing nodes) without invalidating their certification results. Such modification would require the team to run the three core benchmarks (HPL, HPCG and MLPerf-BERT Inference) again in succession (any order) and recertify the results before the benchmarking deadline in order to have a valid result. Only the last valid hardware certification result will be used in benchmark scoring. This last certified hardware configuration will also be the hardware configuration used for the rest of the competition.


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
   benchmarks/interview.rst
   benchmarks/faq.rst
   https://github.com/mlcommons/ck/blob/master/docs/tutorials/scc23-mlperf-inference-bert.md


.. Indices and tables
.. ==================

.. * :ref:`genindex`


