# Do not edit! This file was generated via Makefile
FROM quay.io/projectquay/golang:1.19  as builder

COPY . .
RUN make install test-install

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
USER 65532

COPY --from=builder /go/bin/domain-mapping-webhook /ko-app/domain-mapping-webhook
ENTRYPOINT ["/ko-app/domain-mapping-webhook"]
