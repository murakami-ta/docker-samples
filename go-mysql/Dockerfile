FROM golang:1.13.8-alpine3.11 as build-env

WORKDIR /go/src/sample

COPY go.mod .
COPY go.sum .

RUN go mod download
COPY . .
RUN go build -o /go/bin/sample

FROM scratch

COPY --from=build-env /go/bin/sample .
ENTRYPOINT ["./sample"]
