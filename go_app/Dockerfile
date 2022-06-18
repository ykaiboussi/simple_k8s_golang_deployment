# syntax=docker/dockerfile:1
FROM golang:1.16-alpine

WORKDIR /app

COPY go.mod ./

COPY go_app/*.go ./

RUN go build -o /go_app