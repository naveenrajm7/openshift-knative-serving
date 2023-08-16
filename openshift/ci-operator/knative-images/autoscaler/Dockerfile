# Do not edit! This file was generated via Makefile
FROM quay.io/projectquay/golang:1.19  as builder

ENV GOBIN=/go/bin
RUN mkdir -p /go/src/github.com/openshift/origin
COPY . /go/src/github.com/openshift/origin
WORKDIR /go/src/github.com/openshift/origin

RUN make install test-install

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
USER 65532

COPY ./cmd/autoscaler/kodata /var/run/ko
COPY --from=builder /go/bin/autoscaler /ko-app/autoscaler
ENTRYPOINT ["/ko-app/autoscaler"]
