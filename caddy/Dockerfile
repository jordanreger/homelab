FROM caddy:builder AS builder

RUN apk add ca-certificates

RUN xcaddy build v2.9.1 \
    --with github.com/caddy-dns/porkbun

FROM caddy:latest

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
