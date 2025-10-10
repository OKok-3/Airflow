# Airflow

This repository contains the configuration, Dockerfiles, and supporting scripts for running Apache Airflow in a semi-single-node setup on my own infrastructure:

* **Orchestrator VM**: scheduler, webserver (api server), triggerer, DAG processor, metadata DB (PostgreSQL), redis
* **Worker VM(s)**: Celery workers for running tasks

The goal is to keep images and configs centralized in one location to make it easier to maintain and restore in case of a disaster.

---

*If you are viewing this repo on GitHub, please note that this is a duplicate of what I have on [my own Gitea server](https://gitea.tguan.xyz/OKok-3/Airflow). The reason being it is not meant to be deployed in cloud providers (AWS, Azure, GCP, Hetzner, etc.), but on my own infrastructure, so it's easier for me to manage and deploy.*
