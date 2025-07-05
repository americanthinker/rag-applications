# Use Python 3.12 base image
FROM ghcr.io/astral-sh/uv:python3.12-bookworm-slim

# Set environment variables
ENV PIP_DISABLE_PIP_VERSION_CHECK=on
ENV UV_HTTP_TIMEOUT=300
# ENV VIRTUAL_ENV=/opt/venv
# RUN python3 -m venv $VIRTUAL_ENV
# ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory in the container
WORKDIR /workspaces/rag_app
ENV PATH="/workspaces/rag_app/.venv/bin:$PATH"

# Copy the rest of the application code into the container and sync dependencies
COPY . /workspaces/rag_app/
RUN uv sync --locked
# Set entrypoint
CMD ["bash"]
