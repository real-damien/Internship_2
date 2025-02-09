FROM golang:1.23-alpine as builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN go build -o pinger main.go

FROM alpine:latest

COPY --from=builder /app/pinger /pinger

CMD ["/pinger"]