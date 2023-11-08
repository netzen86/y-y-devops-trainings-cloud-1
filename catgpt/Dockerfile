FROM golang:1.21 AS builder

ENV CGO_ENABLED 0

WORKDIR /build

# Download Go modules
COPY go.mod go.sum ./
RUN go mod download

# Copy the source code. Note the slash at the end, as explained in
# https://docs.docker.com/engine/reference/builder/#copy
COPY *.go ./
COPY *.png ./
COPY tpl ./tpl

RUN go build -o catgpt

FROM gcr.io/distroless/static-debian12:latest-arm64

WORKDIR /app

COPY --from=builder /build/catgpt /app/catgpt

EXPOSE 8080

EXPOSE 9090

CMD ["/app/catgpt"]

# for run  docker run --publish 8080:8080 --publish 9090:9090 catgpt
# docker tag catgpt cr.yandex/crpbccj0cfhnv6t6ocnd/catgpt:latest
# docker push cr.yandex/crpbccj0cfhnv6t6ocnd/catgpt:latest
