FROM python:3.14-slim

ARG USERNAME="poetry"
ARG USER_UID=1000
ARG USER_GID=1000
ARG WORKDIR="/app"

RUN groupadd -g ${USER_GID} ${USERNAME} && \
    useradd -u ${USER_UID} -g ${USERNAME} -m -s /bin/bash ${USERNAME}

WORKDIR ${WORKDIR}
RUN chown ${USERNAME}:${USERNAME} ${WORKDIR}

USER ${USERNAME}
