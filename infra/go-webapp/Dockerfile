FROM golang:1.12.0-alpine3.9

RUN mkdir /app

COPY . /app
WORKDIR /app

RUN go build -o main .

EXPOSE 8080

RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

CMD ["/app/main"]
