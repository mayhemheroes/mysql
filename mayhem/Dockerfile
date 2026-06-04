# Build in a stock Go builder container
FROM golang:1.21 AS builder

ENV GOTOOLCHAIN=auto

ADD . /mysql
WORKDIR /mysql

RUN go test -c -fuzz=FuzzFormatDSN -o fuzz.test .

FROM ubuntu:22.04
COPY --from=builder /mysql/fuzz.test /fuzz.test
