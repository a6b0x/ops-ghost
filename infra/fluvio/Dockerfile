# FROM debian:bullseye-slim
# COPY fluvio /usr/local/bin/fluvio
# RUN chmod +x /usr/local/bin/fluvio

FROM ubuntu:20.04

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    curl \
    unzip \
    ca-certificates && \
    rm -rf /var/lib/apt/lists/*


# install Fluvio & FVM & SDF
RUN curl -fsS https://hub.infinyon.cloud/install/install.sh?ctx=dc | bash && \
    /root/.fvm/bin/fvm install sdf-beta11

ENV PATH="$PATH:/root/.fluvio/bin:/root/.fvm/bin"