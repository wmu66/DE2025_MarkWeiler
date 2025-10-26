FROM spark:3.5.0

USER root

RUN apt-get update -y
RUN apt-get install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev wget libbz2-dev
RUN wget https://www.python.org/ftp/python/3.11.3/Python-3.11.3.tgz && tar -xvf Python-3.11.3.tgz
RUN cd Python-3.11.3 && ./configure --enable-optimizations && make -j $(nproc) && make install
ENV PYSPARK_DRIVER_PYTHON=/usr/local/bin/python3.11
ENV PYSPARK_PYTHON=/usr/local/bin/python3.11

RUN  apt-get update -y && apt-get install -y python3-wheel
# Copy requirements.txt  to the working directory
COPY requirements.txt .
# Install required python packages
RUN pip install --no-cache-dir -r requirements.txt

# Update the guava library needed by the gcs connector
RUN mv /opt/spark/jars/guava-14.0.1.jar /opt/spark/jars/guava-14.0.1.jar.bk
COPY *.jar /opt/spark/jars/       
