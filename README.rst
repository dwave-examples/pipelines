Pipelines Demo
=============

Pipeline networks can be viewed as a graph built up of edges (pipeline segments) and nodes (junctions of pipeline segments).  Suppose that within this network of pipelines, we want to determine a set of junctions from which we can monitor every pipeline segment.  This problem can be modeled as a vertex cover problem in which we want to find a subset of nodes in a graph such that every edge has at least one end point in our subset.

Let's look at a simple example.  Below we have a graph representing a simple network of pipelines with seven junctions.  Note that each junction is identical in terms of its utility as a monitoring location.

.. image:: readme_imgs/example_original.png

Problem: Given the above set of junctions, which ones should you choose such that you minimize the number selected for monitoring, while still monitoring every segment?

Solution: One possible solution is indicated by the red nodes below.

.. image:: readme_imgs/example_solution.png

Usage
-----
To run the demo:
::
  python pipelines.py

Code Overview
-------------

The program ``pipelines.py`` creates a graph using the Python package ``networkx``, and then uses the Ocean software tools to run the ``minimum_vertex_cover`` function from within the ``dwave_networkx`` package.

Inside the Code: The Lagrange Parameter
------ --- ----  --- -------- ---------
Gamma, our Lagrange parameter, weights the constraints in the problem versus
the energy term (objective). If the Lagrange parameter is too small, relative
to the strength of the energy term, the constraints may be violated.

In this code, the default of the Lagrange parameter is 2. Repeated runs showed
sets which were too small - visual inspection shows that we should see
minimum vertex covers of size 4. The Lagrange parameter value of 5 was set
large enough to balance the rest of the terms in the QUBO.

License
-------
Released under the Apache License 2.0. See `LICENSE <../LICENSE>`_ file.
