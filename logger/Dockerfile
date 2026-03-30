# build stage
FROM golang:1.16-alpine AS build-env
RUN apk --no-cache add build-base git mercurial gcc
ADD . /src
RUN cd /src/logger && go get -v . && go build -o orl-logger

# final stage
FROM alpine
WORKDIR /app
COPY --from=build-env /src/logger/orl-logger /app/
CMD [ "./orl-logger" ]