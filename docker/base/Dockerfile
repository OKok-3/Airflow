ARG AIRFLOW_VERSION=3.1.0
ARG PYTHON_VERSION=3.12

FROM apache/airflow:slim-${AIRFLOW_VERSION}-python${PYTHON_VERSION}
COPY --from=ghcr.io/astral-sh/uv:0.8.22 /uv /uvx /bin/

ARG AIRFLOW_VERSION
ARG PYTHON_VERSION
COPY constraints/${AIRFLOW_VERSION}-python-${PYTHON_VERSION}.txt /opt/airflow/constraints.txt
COPY docker/base/requirements.txt /opt/airflow/requirements.txt

ENV AIRFLOW__CORE__EXECUTOR=CeleryExecutor
ENV AIRFLOW__CORE__DAGS_ARE_PAUSED_AT_CREATION="true"
ENV AIRFLOW__CORE__LOAD_EXAMPLES="false"
ENV AIRFLOW__SCHEDULER__ENABLE_HEALTH_CHECK="true"
ENV AIRFLOW_CONFIG="/opt/airflow/config/airflow.cfg"
ENV AIRFLOW__WEBSERVER_REVERSE_PROXY_FIX="true"
ENV AIRFLOW__WEBSERVER__COOKIE_SECURE="true"

RUN uv pip install --no-cache-dir -c constraints.txt -r requirements.txt 

USER root
RUN rm -rf /bin/uv /bin/uvx

USER airflow
