FROM golang:latest

ENV SRC_DIR=/go/src/github.com/mohohewo/

ENV GOBIN=/go/bin

WORKDIR $GOBIN

ADD . $SRC_DIR

RUN cd /go/src/

# mysql のドライバ
RUN go get github.com/go-sql-driver/mysql && \
    go get github.com/gorilla/mux && \
    go install github.com/mohohewo/

ENTRYPOINT ["./mohohewo"]

EXPOSE 8080