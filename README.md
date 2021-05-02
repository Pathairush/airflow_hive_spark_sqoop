# Customize airflow docker

## Project milestones

- Build an airflow docker image with `postgres`, `sqoop`, `spark`, and `hive` components.
- Publish to the docker hub for `arm64` archietecture contribution.
- Used it in the following project to build a data engineer challenge pipeline.

## Learning objectives

### Docker
- Understanding how to build a docker image from other built images with `dockerfile` configuration.
- Able to change or modify the parameter from the existing built image.
- Learn how to structure a docker project. e.g., `.dockerignore`, `docker-compose.yml`

### Hadoop
- Understanding the basic need for configuring hadoop ecosystem. e.g., configuration files `core-site.xml`, `hdfs-site.xml`, etc. 
- Be able to work around for the dependency issues between hadoop components. For example which hive version should we use with the hadoop 3.2.1.
