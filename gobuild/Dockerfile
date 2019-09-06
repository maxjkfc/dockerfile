FROM golang:latest as binder

COPY . /app
WORKDIR /app

ARG COMMIT
ARG DATE
ARG TAG

# Input the origin package path

ENV GO111MODULE=on

RUN CGO_ENABLED=0 GOOS=linux go build -v -a -installsuffix cgo \
    -ldflags "-X main.VERSION=$TAG -X main.COMMIT=$COMMIT -X main.BUILD=$DATE" \
    -o app

# 
FROM alpine:latest 
RUN apk add --no-cache tzdata
ENV TZ Asia/Taipei

EXPOSE 1314

COPY --from=binder /app/app /app
#COPY --from=binder /app/config.yaml /config.yaml

WORKDIR /
ENTRYPOINT ["./app"]
CMD  ["version"]


