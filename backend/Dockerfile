FROM python:3.14-slim

WORKDIR /app

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv

# Install dependencies first (cached layer — only re-runs when pyproject.toml/uv.lock change)
COPY pyproject.toml uv.lock ./
RUN uv sync --frozen --no-dev --no-install-project

# Copy application code and install the project
COPY mgaserver/ ./mgaserver/
RUN uv sync --frozen --no-dev

# Copy data files
COPY data/ ./data/

EXPOSE 8000

CMD ["/app/.venv/bin/uvicorn", "mgaserver.main:app", "--host", "0.0.0.0", "--port", "8000"]
