FROM golang:alpine

# Set necessary environmet variables needed for our image
ENV GO111MODULE=on \
  CGO_ENABLED=0 \
  GOOS=linux \
  GOARCH=amd64

WORKDIR /build

COPY go.mod .
COPY go.sum .
RUN go mod download

COPY . .
RUN go test ./...

RUN go build -o main .

WORKDIR /dist

RUN cp /build/main .

EXPOSE 5000

CMD ["/dist/main", "5000", "15"]