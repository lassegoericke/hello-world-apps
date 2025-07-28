FROM ubuntu:22.04
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y golang-go=2:1.18~0ubuntu2 ca-certificates && update-ca-certificates 2>/dev/null || true
COPY * .
RUN CGO_ENABLED=0 go build main.go

FROM alpine:3.17.1
RUN addgroup -S appgroup && adduser -S appuser -G appgroup -h /home/appuser
RUN rm -rf /bin/sh && rm -rf /usr/bin/bash
COPY --from=0 /main /home/appuser/app
USER appuser
CMD ["/home/appuser/app"]
EXPOSE 8080