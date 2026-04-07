FROM python:3.11-alpine

WORKDIR /app

COPY backend.py .

ENV DB_HOST=db
ENV DB_PORT=5432
ENV APP_NAME=Backend

EXPOSE 5000

CMD ["python", "-u", "backend.py"]