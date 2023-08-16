# Do not edit! This file was generated via Makefile
FROM quay.io/projectquay/golang:1.19  as builder

ENV GOBIN=/go/bin
RUN mkdir -p /go/src/github.com/openshift/origin
COPY . /go/src/github.com/openshift/origin
WORKDIR /go/src/github.com/openshift/origin

RUN make install test-install

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
USER 65532

COPY --from=builder /go/bin/domain-mapping /ko-app/domain-mapping
ENTRYPOINT ["/ko-app/domain-mapping"]
