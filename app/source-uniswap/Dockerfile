FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY source-uniswap /app/source-uniswap
COPY ../config/source-uniswap.toml /app/config/source-uniswap.toml

RUN chmod +x /app/source-uniswap