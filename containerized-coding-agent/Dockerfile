FROM ubuntu:latest

WORKDIR /code

# Install coding tools and create non-root user
RUN apt update \
    && apt install -y nodejs npm python3 git curl librsvg2-bin sudo dotnet-sdk-10.0 \
    && rm -rf /var/lib/apt/lists/*

RUN npm install -g \
    ccusage \
    @mermaid-js/mermaid-cli \
    @openai/codex \
    @github/copilot

# Create a non-root user with sudo access
RUN useradd -m -s /bin/bash appuser && \
    usermod -aG sudo appuser && \
    echo "appuser ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && \
    chown -R appuser:appuser /code

USER appuser

# Install claude code as appuser so it lands in /home/appuser/.local/bin
RUN curl -fsSL https://claude.ai/install.sh | bash

# Add ~/.local/bin to PATH for appuser
RUN echo 'export PATH="$HOME/.local/bin:$PATH"' >> /home/appuser/.bashrc
