Troubleshooting
===============

Jupyter Notebooks
-----------------

* Set ``DEBUG = True`` in the cell near the top. Run that cell and then re-run
  cells as needed to get more printed output.
* Make sure the pip install ran correctly. You might need to restart the
  kernel and run the cells from the top after the pip install runs the first
  time. Run the cell after the pip install with ``DEBUG = True`` to see the status.
* Many of the cells rely on variables that are set in earlier cells. Some of these
  are cleared in later cells. Start over at the top when troubleshooting.
