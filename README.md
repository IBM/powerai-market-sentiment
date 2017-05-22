# Evaluating predictability of financial markets using New York Times sentiments and market data.

In this developer journey we will use a Jupyter notebook to showcase an
example of machine learning with time series on IBM Power8 systems. The
notebook will focus on evalulating the predictability of future
financial market values in the "renewable energy" sector by examining
related markets and sentiment detected in New York Times news articles.

When the reader has completed this journey, they will understand how to:

* Extract and format structured data from various external sources.
* Extract and format unstructured data and use IBM Watson cognitive
services to extract data sentiment.
* Build and train Neural Networks.
* Display and share results in Jupyter notebooks.

The intended audience for this journey is application developers who need
to efficiently build powerful deep learning applications, but who may
not have an abundance of time or data science experience.

![](doc/source/images/architecture.png)

## Included components

* [IBM Watson Natural Language Understanding](https://www.ibm.com/watson/developercloud/natural-language-understanding.html): A Bluemix service that can analyze text to extract meta-data from content such as concepts, entities, keywords, categories, sentiment, emotion, relations, semantic roles, using natural language understanding.
* [IBM Power AI](https://www.ibm.com/ms-en/marketplace/deep-learning-platform): A software platform that includes the most popular machine learning frameworks with IBM Power Systems.
* [IBM Power Systems](https://www-03.ibm.com/systems/power/): IBM Power Systems is IBM's Power Architecture-based server line, built with open technologies and designed for mission-critical applications.
* [Nimbix Cloud Computing Platform](https://www.nimbix.net/): An HPC & Cloud Supercomputing platform enabling engineers, scientists & developers, to build, compute, analyze, and scale simulations in the cloud

## Featured technologies

* [Data Science](https://medium.com/ibm-data-science-experience): An open-source web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.
* [Tensorflow](https://www.tensorflow.org/): An open source software library for numerical computation using data flow graphs.

# Steps

Follow these steps to setup and run this developer journey. The steps are
described in detail below.

1. [Register for a Nimbix Cloud Platform account](#1-register-for-nimbix-cloud-platform-account)
2. [Deploy and run the TensorFlow Demo](#2-deploy-and-run-tensorflow-demo)
3. [Access and start the Jupyter notebook](#3-access-and-start-the-jupyter-notebook)
4. [Run the notebook](#4-run-the-notebook)
5. [Analyze the results](#5-analyze-the-results)
6. [Save and share](#6-save-and-share)
7. [Shut down the TensorFlow Demo](#5-shut-down-demo)

## 1. Register for a Nimbix Cloud Platform account

IBM has partered with Nimbix to provide journey developers a trial
account that provides 10 hours of free processing time on the Power AI
platform.

The sign-ip process is as follows:

1) Go to the [IBM Congnitive Journey Demonstration Registration](https://www.nimbix.net/cognitive-journey)
page on the Nimbix site and register.

2) Nimbix will email you a confirmation message that will include a
link to confirm your registration. Click on the provided link within 24
hours to continue the process.

3) The provided link will take you to a Nimbix registration page where
you will need to create and confirm your account password.

4) Nimbix will then email you another message that will contain a link to
activate your account and instructions for logging into Nimmbix.

## 2. Deploy and run TensorFlow demo

Once signed into Nimbix, deploy the demo on an IBM Power8 server.

* From the Nimbix dashboard, switch to the ``PushToCompute`` panel and
click on the ``TensorFlow-Demo`` application:

![](doc/source/images/nimbix-select-demo.png)

* From the ``TensorFlow-Demo`` drop-down menu, select option to launch
server:

![](doc/source/images/nimbix-launch-server.png)

* Confirm all default configuration options and launch the server:

![](doc/source/images/nimbix-server-config.png)

![](doc/source/images/nimbix-confirm-server.png)

![](doc/source/images/nimbix-response.png)

* From the ``Dashboard`` panel, select the ``TensorFlow-Demo: Server``
to view the server job information. Take note of the server IP address
and password:

![](doc/source/images/nimbix-server-creds.png)

Using the information obtained from the previous step, launch the server
session:

* Open a terminal session on the same host that accessed the Nimbix Cloud.

* Enter the following ssh command, substituting the values provided in
the previous step.

    ``ssh -L 8888:localhost:8888 nimbix@<server ip addr>``

* When prompted, enter the supplied password.

![](doc/source/images/nimbix-ssh-session.png)

From the same terminal window, enter the command ``ipython notebook`` to
launch the Jupyter notebook:

![](doc/source/images/nimbix-launch-notebook.png)

Take note of the URL provided. Use this link to access the notebook.

## 3. Access and start the Jupyter notebook

Proceed to the provided notebook URL and click on the
``Clean_Energy_Watson_V1.0.ipynb`` link to start the Jupyter notebook.

![](doc/source/images/jupyter-nb-contents.png)

![](doc/source/images/nb-start-page.png)

## 4. Run the notebook

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.

Notes:

- Regading cell `[4]`: For the journey we import already collected
stock market data. This can be done inside the notebook, but requires
access to private financial websites (such as Bloomberg), which requires
a subscription fee.

- Regarding cell `[5]`: In an effort to speed up the
notebook processing time, the New York Times data has already
been collected and stored in a JSON file, and is imported by the notebook.

- The journey is based on the original Google Cloud Platform example
documented at https://cloud.google.com/solutions/machine-learning-with-financial-time-series-data.
The difference between this "IBM Demo" and the original "Google Demo" is noted
in the following table:

![](doc/source/images/demo-diffs.png)

## 5. Analyze the results

The result of running the notebook is a report which may be shared with or
without sharing the code. You can share the code for an audience that wants
to see how you came your conclusions. The text, code and output/charts are
combined in a single web page. For an audience that does not want to see
the code, you can share a web page that only shows text and output/charts.

The graphs and charts produced in this journey attempt to prove that the
closing value of the Nasdaq Clean Energy Index can be predicted by
examining various input sources, such as the New York Times and other
financial markets, both foreign and domestic. These markets include:

- Austrailian Clean Tech Index (asx_cti)
- Germany DAX (dax_eusdn)
- UK FTSE100 (ftse-eo100)
- UK Credit Suisse (n8wh)
- US First Trust Nasdaq Clean Edge ETF (qcln and cels)
- US S&P Global Clean Energy Index (icln and sp_gtced)
- US Equity Uncertainty Index (dei)

#### Collect Data

The notebook begins by collecting and formatting data:

* Collect and merge 3 years of stock market financial data.

* Collect 3 years of "green energy" articles from the New York
Times. This data is then feed into the Watson Natural Language Understanding
service to gather sentiment analysis - specifically by assigning a
relative positive or negative score to each article.

![](doc/source/images/sentiment-values.png)

#### Analyze Data

The notebook then utilizes EDA (exploratory data analysis) methods to
find correlations in the data. These findings include:

* Over a 3-year period, there is a correlation between all of the indexes.

![](doc/source/images/3-year-span.png)

* There is a correlation between current values of an index and lagged
values of the same index.

![](doc/source/images/correlation-data.png)

* There are 2 US indexes (qcln and icln) that correlate with the closing
values of other indexes available on the same day (i.e. non-US indexes).

![](doc/source/images/scatter-graph.png)

The final analysis from the EDA are as follows:
- The Austrailian Index close from the same day is a strong predictor
for the close of the Nasdaq Energy Index.
- European indices are a significant predictor for the close of the
Nasdaq Energy Index.
- Indices from previous days were not a good predictor for the Nasdaq
Energy Index.

#### Train and Test Data

After determining this correlation in the data, the notebook then
uses TensorFlow and the IBM PowerAI machine learning framework to train
and test the data.

After hundreds of thousands of interations over the data using multiple
models, the notebook is able to achieve a 70% success rate for
predicting whether the Nasdaq Energy Index would close up or down on any
given day.

## 6. Save and share

### How to save your work:

Because this notebook is running temporarily on a Nimbix
Cloud server, the options to saving and sharing the notebook are limited.

Under the `File` menu, there are options to:

* `Download as...` will download the notebook to your local system.
* `Print Preview` will allow you to print the current state of the
  notebook.

## 7. Shut down the TensorFlow demo

After completing the TensorFlow demo, please remember to shutdown the server
to free up resourses on the Nimbix Cloud Platform.

* From the Nimbix dashboard, select the `TensorFlow-Demo` application
to show job details.

* Click on the `Shutdown' button and confirm.

![](doc/source/images/nimbix-shutdown.png)

<!--
# Sample output

The following is a sample data visualization with code
 ![](doc/source/images/output.png)
 For a full example without code see [`data/examples/sample_output.pdf`](data/examples/sample_output.pdf).
-->

# Troubleshooting

[See DEBUGGING.md.](DEBUGGING.md)

# License

[Apache 2.0](LICENSE)
