FROM golang:1.12.1-alpine

RUN apk update && apk upgrade && apk add --no-cache bash git openssh
RUN go get github.com/hashicorp/consul/api
RUN go get github.com/gorilla/sessions
RUN go get github.com/dgrijalva/jwt-go
RUN go get github.com/okta/okta-jwt-verifier-golang
RUN go get gopkg.in/gomail.v2
RUN go get github.com/lib/pq

ENV SOURCE=/go/src/microservices/
COPY . ${SOURCE}

RUN cd ${SOURCE}email-service/ && CGO_ENABLED=0 go build

WORKDIR ${SOURCE}
CMD ${SOURCE}email-service/email-service
EXPOSE 8083

