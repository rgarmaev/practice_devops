FROM cr.yandex/mirror/python:3.11-slim

WORKDIR /app

ENV REGISTRY="Yandex Mirror"

COPY app.py .

RUN groupadd -r appuser && \
    useradd -r -g appuser -u 1001 appuser && \
    chown -R appuser:appuser /app   

USER appuser

EXPOSE 8080


CMD ["python","app.py"]

