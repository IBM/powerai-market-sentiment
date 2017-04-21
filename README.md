# powerai-notebook

In this developer journey we will use a Jupyter notebook to showcase an
example of machine learning with time series on IBM Power8 systems. The
notebook will focus on evalulating the predictability of future
financial market values in the "renewable energy" sector by examining
related markets and sentiment detected in New York Times news articles.

When the reader has completed this journey, they will understand how to:

* Extract and format structured data from various external sources.
* Extract and format unstructured data and use IBM Watson cognitive
services to data sentiment.
* Build and train Neural Networks.
* Display and share results in Jupyter notebooks.

The intended audience for this journey is application developers who need
to efficiently build powerful deep learning applications, but who may
not have an abundance of time or data science experience.

NICE ARCHITECTURE DIAGRAM GOES HERE !!!

## Included Components

* IBM Watson Cognitive Service
* IBM Power AI / TensorFlow
* Nimbix Cloud Computing Platform
* Jupyter Notebooks
* Python
* pandas (Python Data Analysis Library)
* Matplotlib

# Steps

Follow these steps to setup and run this developer journey. The steps are
described in detail below.

1. [Register for a Nimbix Cloud Platform account](#1-register-for-nimbix)
2. [Deploy and run the TensorFlow Demo](#2-deploy-tensor-flow-demo)
3. [Access and start the Jupyter notebook](#3-start-notebook)

## 1. Register for a Nimbix Cloud Platform account

Register for Power AI on the [Nimbix Cloud](https://platform.jarvice.com/login-page).

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

    ssh -L 8888:localhost:8888 nimbix@<server ip addr>
* When prompted, enter the supplied password.

![](doc/source/images/nimbix-ssh-session.png)

From the same terminal window, enter the command "ipython notebook" to
launch the Jupyter notebook:

![](doc/source/images/nimbix-launch-notebook.png)

Take note of the URL provided. Use this link to access the notebook.

## 3. Access and start the Jupyter notebook

Proceed to the provided notebook URL and click on the
``Clean_Energy_Watson_V1.0.ipynb`` link to start the Jupyter notebook.

![](doc/source/images/jupyter-nb-contents.png)

![](doc/source/images/nb-start-page.png)

## 4. Analyze the results

## 5. Save and Share

### How to save your work:

Under the `File` menu, there are several ways to save your notebook:

* `Save` will simply save the current state of your notebook, without any version
  information.
* `Save Version` will save your current state of your notebook with a version tag
  that contains a date and time stamp. Up to 10 versions of your notebook can be
  saved, each one retrievable by selecting the `Revert To Version` menu item.

### How to share your work:

You can share your notebook by selecting the “Share” button located in the top
right section of your notebook panel. The end result of this action will be a URL
link that will display a “read-only” version of your notebook. You have several
options to specify exactly what you want shared from your notebook:

* `Only text and output`: will remove all code cells from the notebook view.
* `All content excluding sensitive code cells`:  will remove any code cells
  that contain a *sensitive* tag. For example, `# @hidden_cell` is used to protect
  your dashDB credentials from being shared.
* `All content, including code`: displays the notebook as is.
* A variety of `download as` options are also available in the menu.

# Sample output

The following is a sample data visualization with code:

![](doc/source/images/output.png)

For a full example without code see [`data/examples/sample_output.pdf`](data/examples/sample_output.pdf).

# Troubleshooting

[See DEBUGGING.md.](DEBUGGING.md)

# License

[Apache 2.0](LICENSE)