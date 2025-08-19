FROM rust:1-slim-bookworm

ARG FLUVIO_VERSION=

RUN rustup target add wasm32-wasip2
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl unzip tini openssl && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
    
RUN curl -fsS "https://hub.infinyon.cloud/install/install.sh?ctx=sdf-demo" | FLUVIO_VERSION=${FLUVIO_VERSION} bash

ENV PATH "$PATH:/root/.fluvio/bin"
ENV PATH "$PATH:/root/.fvm/bin"

RUN sdf setup || true