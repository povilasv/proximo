FROM alpine:3.5

ENV GOPATH=/go

WORKDIR /go/src/app
ADD . /go/src/app/

RUN apk --no-cache add ca-certificates git go musl-dev \
  && go get ./... \
  && CGO_ENABLED=0 go build -ldflags '-s -extldflags "-static"' -o /proximo-server . \
  && apk del go git musl-dev \
  && rm -rf $GOPATH

CMD [ "/proximo-server" ]