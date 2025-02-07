FROM python:3.8.12

# LABEL
LABEL maintainer="tobias@anti-gravity.as"
LABEL version="0.1"
LABEL description="This is custom Docker Image for creating a jupyterlab container in the pysystemtrade_ecosystem"

ARG GIT_TOKEN
ARG ECHO_PATH=$ECHO_PATH

ENV ECHO_PATH=$ECHO_PATH

RUN mkdir /opt/projects
RUN git clone -b my_branch https://${GIT_TOKEN}:@github.com/GITUSERNAME/private_pysystemtrade_repo.git /opt/projects/pysystemtrade

RUN apt-get update
RUN yes | apt-get install vim

RUN pip3 install --upgrade pip
RUN pip3 install sqlalchemy==1.3.22
RUN pip3 install psycopg2-binary
RUN pip3 install pandas==1.0.5
RUN pip3 install matplotlib>=3.0.0
RUN pip3 install pyyaml==5.4
RUN pip3 install numpy>1.19.4
RUN pip3 install scipy>=1.0.0
RUN pip3 install pymongo==3.9.0
RUN pip3 install arctic==1.79.2
RUN pip3 install ib-insync==0.9.70
RUN pip3 install psutil==5.6.6
RUN pip3 install pytest>6.2
RUN pip3 install Flask>=2.0.1
RUN pip3 install Werkzeug>=2.0.1
RUN pip3 install statsmodels==0.12.2
RUN pip3 install jupyterlab

COPY ./jupyter_server_config.py /usr/jupyter_server_config.py
WORKDIR /opt/projects/pysystemtrade
RUN pip install -e .

RUN mkdir $ECHO_PATH
 
ENTRYPOINT jupyter-lab --allow-root --no-browser --port=8888  --ip=0.0.0.0 --config=/usr/jupyter_server_config.py