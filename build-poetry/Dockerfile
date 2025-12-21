FROM python:3.14.0-slim

ARG USERNAME=appuser
ARG USER_UID=1000
ARG GROUPNAME=$USERNAME
ARG GROUP_UID=$USER_UID
ARG USER_HOME=/home/$USERNAME

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
      build-essential \
      curl \
      git \
      gnupg

RUN curl -sfL https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor -o /usr/share/keyrings/trivy.gpg \
    && echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | tee /etc/apt/sources.list.d/trivy.list \
    && apt-get update \
    && apt-get install -y trivy

RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://install.python-poetry.org | POETRY_HOME=/opt/poetry python -
ENV PATH="$PATH:/opt/poetry/bin"

RUN pip install --no-cache-dir \
    pytest \
    bandit \
    pylint

RUN groupadd -r -g ${GROUP_UID} ${GROUPNAME} \
    && useradd -r -u ${USER_UID} -g ${USERNAME} -m -d ${USER_HOME} ${USERNAME} \

ENV TRIVY_CACHE_DIR=/opt/trivy-cache
RUN mkdir -p ${TRIVY_CACHE_DIR} \
    && trivy image --download-db-only \
    && chown -R ${USERNAME}:${GROUPNAME} ${TRIVY_CACHE_DIR}

USER ${USERNAME}
WORKDIR ${USER_HOME}
