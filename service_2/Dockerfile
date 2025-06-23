FROM python:3.10-slim

WORKDIR /app
COPY . .

RUN pip install flask

RUN apt-get update && apt-get install -y curl
CMD ["python", "app.py"]
