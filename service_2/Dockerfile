FROM python:3.10-slim

WORKDIR /app
COPY . .

RUN pip install -r requirements.txt

RUN apt-get update && apt-get install -y curl
CMD ["python", "app.py"]
