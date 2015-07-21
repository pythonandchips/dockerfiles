FROM debian:sid

RUN apt-get update && apt-get install -y gcc curl git mercurial
ENV GO_VERSION 1.4.2
RUN curl -sSL https://golang.org/dl/go${GO_VERSION}.src.tar.gz | tar -v -C /usr/local -xz \
  && mkdir -p /go/bin /go/src
ENV PATH /go/bin:/usr/local/go/bin:$PATH
ENV GOPATH /go
RUN cd /usr/local/go/src && ./make.bash --no-clean 2>&1

ENTRYPOINT ["go"]
