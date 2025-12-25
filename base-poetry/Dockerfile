FROM python:3.14-slim

ARG USERNAME="poetry"
ARG USER_UID=1000
ARG USER_GID=1000
ARG WORKDIR="/app"
ARG POETRY_VERSION="2.2.1"

RUN pip install --no-cache-dir poetry==${POETRY_VERSION}

RUN groupadd -g ${USER_GID} ${USERNAME} && \
    useradd -u ${USER_UID} -g ${USERNAME} -m -s /bin/bash ${USERNAME}

WORKDIR ${WORKDIR}
RUN chown ${USERNAME}:${USERNAME} ${WORKDIR}

USER ${USERNAME}

ENV POETRY_VIRTUALENVS_CREATE=false
