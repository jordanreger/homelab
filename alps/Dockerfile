FROM golang:alpine AS builder

WORKDIR /app

RUN apk update && apk add git && rm -rf /var/cache/apk/*

RUN git clone https://git.sr.ht/~migadu/alps .

RUN CGO_ENABLED=0 go build -v -o alps ./cmd/alps

FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/alps /usr/local/bin/alps 

COPY --from=builder /app .

EXPOSE 1323

CMD ["alps"]
