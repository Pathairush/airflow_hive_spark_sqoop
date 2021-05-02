# Customized airflow docker

## Dependencies

- `airflow==1.10.14`
- `hadoop==3.2.1`
- `hive==3.1.2`
- `spark==3.1.1`
- `sqoop==1.4.7`

## How to run

You can clone this repository and run the following command to start the airflow webserver.

```
docker compose up -d
```

You can access the airflow webserver with http://localhost:8080

It's already mount the `dags` and `plugins` parts to the docker volume, please feel free to change the configuration in the `docker-compose.yml` for you preference. 

To close the airflow container
```
docker compose down -v
```

## References

- Airflow docker based : https://github.com/puckel/docker-airflow
- Hadoop based configuration : https://github.com/pavank/docker-bigdata-cluster

## Todos

- [ ] build a `hive`, `spark`, and `sqoop` cluster for testing the `airflow` operators.

# Project milestones

- [X] Build an airflow docker image with `Postgres, `Sqoop`, `Spark`, and `Hive` components.
- [X] Publish to the docker hub for `arm64` architecture contribution.
- [ ] Used it in the following project to build a data engineer challenge pipeline.

# Learning objectives

## Docker
- Understanding how to build a docker image from other built images with `dockerfile` configuration.
    - understand the parameter difference in the docker file (`ENV`, `RUN`, `ARG`, `CMD`, etc.).
- Able to change or modify the parameter from the existing built image.
    - Successfully modify and build the image for the airflow container.
- Learn how to structure a docker project. e.g., `.dockerignore`, `docker-compose.yml`

## Hadoop
- Understanding the basic need for configuring the Hadoop ecosystem. e.g., configuration files `core-site.xml`, `hdfs-site.xml`, etc. 
- Be able to work around the dependency issues between Hadoop components. For example, which Hive version should we use with the Hadoop 3.2.1?

# Notes

1. The tricky part of this project is not a docker or Hadoop ecosystem. But it's to make all the components dependencies working together. For example, you have to understand why you have to use the `python:3.6-stretch version for building the Hadoop-based image instead of `python:3.7-slim-buster` provided in the original docker image.
    - Quick answer is that the `slim-buster` version doesn't support the JAVA 8, which we have to use for installing the Hadoop components.

2. You will face many dependency problems not only from the Linux-based but also from the python and pip environment. Almost all of the time, you have to find the workaround in the stack overflow and trust me you are not the first to face the issues.
    - Trial and error help you a lot in fixing each issue. Please don't give up that's all I learned from this process.





