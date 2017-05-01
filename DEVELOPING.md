Tips for Developers
===================

The notebook is designed to be run top-down. Settings in early cells are used
in later cells. Some variables are also cleared to free up memory. So, although
you can often run single cell repeatedly while testing changes, you may want
to start over from the top if anything seems to be missing.

building and running this notebook outside of Nimbix
-----------------------------------------------------
This notebook was designed to be built and run on an IBM Power Systems
platform. Since this environment is not readily available for most
developers, the notebook has been packaged up and hosted on the Nimbix Cloud
Platform. All of the data required by the notebook (financial indexes,
New York Times articles, IBM Watson service processing) have already
been collected and can be directly imported into the notebook.

If a developer wishes to run this notebook locally, all of the user files
can be found in this repository:

* /notebooks/Clean_Energy_Watson_V1.0.ipynb - python notebook.
* /data/*.csv - data files referenced in the notebook.
* /data/nyt_article_results.json - NTY articles processed by the IBM
Watson Natural Language Understanding service.

The notebook should run as long as all of the python packages listed
in the notebook are installed. Note that running on a standard x86
sytem will result in significantly slower processing times due to the lack
of system GPUs and processor speed.