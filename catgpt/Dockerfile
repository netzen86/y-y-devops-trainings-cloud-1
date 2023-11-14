FROM golang:1.21 AS builder

ENV CGO_ENABLED 0
ARG GOARCH=amd64

WORKDIR /build

# Download Go modules
COPY . .
RUN go mod download

# Copy the source code. Note the slash at the end, as explained in
# https://docs.docker.com/engine/reference/builder/#copy
# COPY *.go ./
# COPY *.png ./
# COPY tpl ./tpl

RUN GOARCH=${GOARCH} go build -o catgpt

FROM gcr.io/distroless/static-debian12:latest-${GOARCH}

WORKDIR /app

COPY --from=builder /build/catgpt /app/catgpt

EXPOSE 8080 9090

CMD ["/app/catgpt"]