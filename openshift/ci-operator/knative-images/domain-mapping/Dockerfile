# Do not edit! This file was generated via Makefile
FROM docker.io/library/golang:1.19  as builder

COPY . .
RUN make install test-install

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
USER 65532

COPY --from=builder /go/bin/domain-mapping /ko-app/domain-mapping
ENTRYPOINT ["/ko-app/domain-mapping"]
