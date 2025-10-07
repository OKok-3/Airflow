ARG AIRFLOW_VERSION=3.1.0
ARG PYTHON_VERSION=3.12

FROM apache/airflow:slim-${AIRFLOW_VERSION}-python${PYTHON_VERSION}
COPY --from=ghcr.io/astral-sh/uv:0.8.22 /uv /uvx /bin/

ARG AIRFLOW_VERSION
ARG PYTHON_VERSION
COPY constraints/${AIRFLOW_VERSION}-python-${PYTHON_VERSION}.txt /opt/airflow/constraints.txt
COPY docker/base/requirements.txt /opt/airflow/requirements.txt

ENV AIRFLOW__CORE__EXECUTOR=CeleryExecutor

RUN uv pip install --no-cache-dir -c constraints.txt -r requirements.txt 

USER root
RUN rm -rf /bin/uv /bin/uvx

USER airflow
