# Use the required OS as the base
FROM ubuntu:24.04

# Set working directory inside the container
WORKDIR /opt/pipe

# Install curl (useful for debugging inside the container) and update package list
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

# Download and install the binary (included for self-contained image builds)
RUN curl -L https://pipe.network/p1-cdn/releases/latest/download/pop -o pop
RUN chmod +x pop

# Copy your local .env file into the container
COPY .env .

# Expose the necessary ports from the container
EXPOSE 80 443 8081 9090

# Command to run the node when the container starts
CMD ["/bin/bash", "-c", "source .env && /opt/pipe/pop"]