FROM golang:1.7.3-alpine

RUN apk update && apk add git && go get github.com/erroneousboat/slack-term

ENTRYPOINT [ "slack-term" ]
