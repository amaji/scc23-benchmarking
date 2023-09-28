HPL Rules and Validation
------------------------

The HPL benchmark is described at https://www.top500.org/project/linpack/.

The HPL output shows validity by the following line:

.. code-block:: bash

   ||Ax-b||_oo/(eps*(||A||_oo*||x||_oo+||b||_oo)*N)=        0.0020152 ...... PASSED

The time output will look like the following for HPL:

.. code-block:: bash

   T/V                N    NB     P     Q               Time                 Gflops
   --------------------------------------------------------------------------------
   WR01C2L8      102144   192     8     8             514.92              1.380e+03

There is no minimum run time associated with HPL.

