FROM python:3.14.0-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
      build-essential \
      curl \
      git \
      gnupg \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://install.python-poetry.org | POETRY_HOME=/opt/poetry python -
ENV PATH="$PATH:/opt/poetry/bin"

RUN pip install --no-cache-dir \
    pytest \
    bandit \
    pylint

WORKDIR /app
