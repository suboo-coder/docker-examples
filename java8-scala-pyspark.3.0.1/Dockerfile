FROM ubuntu:16.04

RUN apt-get update && \
    apt-get install -y \
    scala \
    openjdk-8-jdk \
    curl \
    python3 \
    python3-pip \
    wget \
    gnupg2 \
    lsb-release \
    software-properties-common \
    build-essential \
    libatlas-base-dev \
    libblas-dev \
    liblapack-dev

# Update pip
# RUN pip3 install --upgrade pip setuptools wheel
RUN python3 -m pip install --upgrade pip setuptools wheel

# Install pandas
# RUN pip3 install pandas
RUN pip3 install pandas

# Make python 3 the default python
RUN ln -s /usr/bin/python3 /usr/bin/python

# Install spark 3.0.1
RUN mkdir /opt/spark && \
    curl -O https://archive.apache.org/dist/spark/spark-3.0.1/spark-3.0.1-bin-hadoop2.7.tgz -o spark-3.0.1-bin-hadoop2.7 && \
    tar xvzf spark-3.0.1-bin-hadoop2.7.tgz --directory /opt/spark --strip-components 1

# Set up environment variables
ENV SPARK_HOME=/opt/spark
ENV HADOOP_HOME=/opt/spark
# Add /opt/spark to path
ENV PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin

# Move the helloworld-example directory to the container
COPY . /pyspark-examples

CMD ["bin/bash"]
