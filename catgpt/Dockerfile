ARG GOARCH=amd64
FROM golang:1.21 AS builder

WORKDIR /build

# COPY go.mod go.sum ./
# https://docs.docker.com/engine/reference/builder/#copy
COPY . .
# Download Go modules
RUN go mod download

RUN CGO_ENABLED=0 GOARCH=${GOARCH} go build -o catgpt

FROM gcr.io/distroless/static-debian12:latest-${GOARCH}

WORKDIR /app

COPY --from=builder /build/catgpt /app/catgpt

EXPOSE 8080 9090

CMD ["/app/catgpt"]