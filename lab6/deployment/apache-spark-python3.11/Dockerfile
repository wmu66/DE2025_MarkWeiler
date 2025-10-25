FROM python:3.11 as build

FROM apache/spark:3.5.0

COPY --from=build /usr/bin/python3/ /usr/bin/python3/

USER root

RUN  apt-get update && apt-get install -y python3-wheel
# Copy requirements.txt  to the working directory
COPY requirements.txt .
# Install required python packages
RUN pip install --no-cache-dir -r requirements.txt

# Update the guava library needed by the gcs connector
RUN mv /opt/spark/jars/guava-14.0.1.jar /opt/spark/jars/guava-14.0.1.jar.bk
COPY *.jar /opt/spark/jars/       
