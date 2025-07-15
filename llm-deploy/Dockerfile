# Base image — use Ubuntu
FROM ubuntu:22.04

# Non-interactive for apt
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && \
    apt-get install -y curl sudo && \
    rm -rf /var/lib/apt/lists/*

# Install Ollama
RUN curl -fsSL https://ollama.com/install.sh | bash

# Expose Ollama API port
EXPOSE 11434

# Start Ollama service and keep container running
CMD ["ollama", "serve"]

