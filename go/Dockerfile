ARG GO_VERSION=1.23.4
ARG DEBIAN_VERSION=bookworm

FROM golang:${GO_VERSION}-${DEBIAN_VERSION} AS go

FROM debian:bookworm-slim

COPY --from=go /usr/local/go/ /usr/local/go/

# Install additional packages and Go tooling
RUN apt-get update && apt-get install -y --no-install-recommends git gopls && \
    apt-get autoremove -y && \
    apt-get clean -y && \
    rm -r /var/cache/* /var/lib/apt/lists/*

ENV GOPATH=/go

ENV PATH=$GOPATH/bin:/usr/local/go/bin:$PATH

WORKDIR $GOPATH