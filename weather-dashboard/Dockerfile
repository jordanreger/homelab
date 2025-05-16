FROM golang:alpine AS builder

WORKDIR /app

RUN apk update && apk add git && rm -rf /var/cache/apk/*

RUN git clone https://git.sr.ht/~jordanreger/weather-dashboard .

RUN CGO_ENABLED=0 go build -v -o weather-dashboard .

FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/weather-dashboard /usr/local/bin/weather-dashboard 

COPY --from=builder /app .

EXPOSE 1324

CMD ["weather-dashboard"]
