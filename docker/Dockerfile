FROM python:3.13-slim-bookworm

ENV UV_COMPILE_BYTECODE=1

ENV UV_HTTP_TIMEOUT=300

ENV PYTHONUNBUFFERED=1

ENV UV_LINK_MODE=copy

COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

WORKDIR /app

# These paths are relative to the 'context' (the parent dir)
COPY pyproject.toml uv.lock ./

RUN uv sync --frozen --no-install-project

COPY . .

RUN uv sync --frozen

CMD ["uv", "run", "python", "main.py"]
