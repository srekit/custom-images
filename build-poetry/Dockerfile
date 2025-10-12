FROM python:3.11-slim-bookworm

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       git \
       curl \
       build-essential \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://install.python-poetry.org | POETRY_HOME=/opt/poetry python -
ENV PATH="$PATH:/opt/poetry/bin"

# Validate workflow8
RUN pip install --no-cache-dir \
    pytest \
    bandit \
    pylint

WORKDIR /app
