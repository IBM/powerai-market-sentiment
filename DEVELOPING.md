Tips for Developers
===================

The notebook is designed to be run top-down. Settings in early cells are used
in later cells. Some variables are also cleared to free up memory. So, although
you can often run single cell repeatedly while testing changes, you may want
to start over from the top if anything seems to be missing.

building and running this notebook outside of Nimbix
-----------------------------------------------------
This notebook requires that it be built and run on an IBM Power Systems
platform. Since this environment is not readily available for most
developers, the notebook has been packaged up and hosted on the Nimbix Cloud
Platform. All of the data required by the notebook (financial indexes,
New York Times articles, IBM Watson service processing) has already
been collected and can be directly imported into the notebook.

If a developer wishes to duplicate this effort in another Power System
environment, all of the files used to create this demo can be found in this
repository:

* /data/Dockerfile - used to build the docker container hosted in Nimbix.
* /data/*.csv - data files referenced in the notebook.
* /data/nyt_article_results.json - NTY articles processed by the IBM
Watson Natural Language Understanding service.



