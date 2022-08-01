FROM golang:1.18-alpine3.16 as build

WORKDIR /
RUN mkdir -p /build
COPY ./hello.go /build

COPY go.mod /build
WORKDIR /build
RUN go mod download
RUN CGO_ENABLED=0 go build -o /app

FROM scratch
COPY --from=build /app /app
ENTRYPOINT ["/app"]








