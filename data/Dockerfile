FROM jarvice/ubuntu-ibm-mldl-ppc64le

#add Jupyter
RUN pip install --upgrade pip
RUN pip install notebook pyyaml
RUN pip install jupyter
RUN pip install ijson
RUN pip install pandas

RUN pip install pandas_datareader
RUN pip install httplib2
RUN apt-get install -y build-essential
RUN apt-get install -y libssl-dev
RUN apt-get install -y libffi-dev
RUN apt-get install -y python-dev
RUN apt-get install -y python-matplotlib
RUN apt-get install -y python-lxml
RUN apt-get install -y openssh-server
RUN pip install cython
RUN apt-get install -y python-scipy
RUN pip install scikit-learn
RUN apt-get install -y libxml2-dev libxmlsec1-dev
RUN pip install dragnet

#add startupscripts
RUN apt-get install -y supervisor
WORKDIR /etc/skel

ADD cels.csv /etc/skel/
Add CTIUS.csv /etc/skel/
ADD DAX-SP-FTSE-index.csv /etc/skel/
ADD eui.csv /etc/skel/
ADD icln.csv /etc/skel/
ADD n8wh.csv /etc/skel/
ADD qcln.csv /etc/skel/
ADD watson.csv /etc/skel/
ADD watson-results.csv /etc/skel/
ADD watson-results-test.csv /etc/skel/
ADD binary-classification.png /etc/skel/
ADD feed-forward.png /etc/skel/
ADD IBM-Google-Demo-Env.png /etc/skel/
ADD NN-Results.png /etc/skel/
ADD Clean_Energy_Watson_V1.0.ipynb /etc/skel/
ADD nyt_article_results.json /etc/skel/

