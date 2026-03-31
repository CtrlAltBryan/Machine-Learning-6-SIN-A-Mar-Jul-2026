FROM python:3.12-slim

RUN apt-get update && apt-get install -y \
    curl \
    git \
    git-lfs \
    && rm -rf /var/lib/ap/lists/*

RUN git lfs install --system
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
ENV PATH="/root/.local/bin:$PATH"
WORKDIR /app
RUN uv venv .bryan_venv
COPY requirements.txt .
RUN uv pip install --python .bryan_venv/bin/python -r requirements.txt
ENV VIRTUAL_ENV=/app/.bryan_venv
ENV PATH="/app/.bryan_venv/bin:$PATH"