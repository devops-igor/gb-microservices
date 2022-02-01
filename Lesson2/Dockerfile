FROM golang:1.17-alpine AS build
RUN mkdir /app
WORKDIR /app

COPY ./golang/go.mod ./golang/go.sum ./

RUN go mod download

COPY ./golang .

RUN go build -o myapp .

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=build /app/myapp .

CMD [ "/root/myapp"]