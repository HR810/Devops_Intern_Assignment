FROM golang:1.24.4-alpine

WORKDIR /app
COPY . .

RUN go build -o service1

RUN apk add --no-cache curl
CMD ["./service1"]

