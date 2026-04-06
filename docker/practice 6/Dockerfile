
FROM python:3.11-slim AS bilder

LABEL maintainer="worker@ubuntu.local"\
      description="python-app"\
      version="1.0"

WORKDIR /app 

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \ 
        wget \
        git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

RUN python -m venv /venv && \
    . /venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt 

COPY . . 

FROM python:3.11-alpine

WORKDIR /app 

COPY --from=bilder /venv /venv

COPY --from=bilder /app /app

RUN adduser -D appuser && chown -R appuser /app
USER appuser

ENV PATH="/venv/bin:$PATH"

EXPOSE 8080

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD python -c "import urllib.request; urllib.request.urlopen('http://localhost:8080')" || exit 1



CMD ["python","app.py"]

