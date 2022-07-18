Purpose
This docker container is meant to be used for learning purpose for programming PySpark. It has the following components.

Hadoop v3.2.1
Spark v2.4.4
Conda 3 with Python v3.7
After running the container, you may visit the following pages.

HDFS
YARN
Spark
Spark History
Jupyter Lab
Airflow
Use docker image

Pull docker image
docker pull avnish327030/spark-hadoop-airflow

Rename pulled docker image
docker image tag  avnish327030/spark-hadoop-airflow spark-hadoop-airflow

To run the docker image
window system:
[D:\Project\big_data] is the path and can be replaced based on what you want in below command or you can create this directory and use same command.

docker run -it -p 9870:9870 -p 8088:8088 -p 8080:8080 -p 18080:18080 -p 9000:9000 -p 8888:8888 -p 9864:9864 -p 8085:8085 -p 8793:8793 -p 8081:8081 -v "C:\Users\DHEMANNA\Oracle_Content_Accounts\Oracle Content\Darshan\DataScience\Ineuron\MLDL\Bigdata\notebook":/root/ipynb -v "C:\Users\DHEMANNA\Oracle_Content_Accounts\Oracle Content\Darshan\DataScience\Ineuron\MLDL\Bigdata\airflow":/home/airflow -v "C:\Users\DHEMANNA\Oracle_Content_Accounts\Oracle Content\Darshan\DataScience\Ineuron\MLDL\Bigdata\data":/data --name mldl-spark-class spark-hadoop-airflow

Linux system
PROJECT_DIR=$(pwd)

All the ports mentioned below in the docker run command is basically linked to a application running in docker, for example ports 9870:9870, port of left is local system port and port number on right is of application running in docker
Bascially in the below command the port mapping between application in docker container to desktop, so we can access the docker application using port mapped to windows using say http://localhost:9870 or http://0.0.0.0:9870
Also folders seen in below command is folder mapping between the docker container folders to desktop folders, so anything changed/added in windows/docker folders will sync in one other
http://localhost:8888/lab? --> this is used to load a docker container jupyter lab notebook, anything written in notebook will be sync with windows folder 
similarly other application available in respective ports

docker run -it \
    -p 9870:9870 \
    -p 8088:8088 \
    -p 8080:8080 \
    -p 18080:18080 \
    -p 9000:9000 \
    -p 8888:8888 \
    -p 9864:9864 \
    -p 8085:8085 \
    -p 8793:8793 \
    -p 8081:8081 \
    -v $PROJECT_DIR/project/notebook:/root/ipynb \
    -v $PROJECT_DIR/project/airflow:/home/airflow \
    -v $PROJECT_DIR/data:/data \
    spark-hadoop-airflow


[Name Node](http://localhost:9870/)
[Airflow](http://localhost:8085/)
[Hadoop Data Node](http://localhost:9864/)
[Jupyter lab](http://localhost:8888/)
[Hadoop Cluster](http://localhost:8088/)
[Spark Master](http://localhost:8080/)



To List docker images
```
docker images
```

To list all running container
```
docker ps
```

To Build docker images
Note: We must have a Dockerfile in current directory 
```
docker build -t image_name:tag_name .
```

to stop running container
```
docker stop container_id
```

To start stop container
```
docker start container_name
```

```
airflow user: admin
airflow pass: airflow
```