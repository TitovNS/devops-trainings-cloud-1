FROM golang:1.21 as builder

WORKDIR /pub/www/app
# COPY ../catgpt/ ./
COPY ./ ./
RUN go mod download
RUN CGO_ENABLED=0 go build -o ./build


FROM gcr.io/distroless/static-debian12:latest-amd64


WORKDIR /pub/www/app
COPY --from=builder /pub/www/app/build/* ./

EXPOSE 8080

CMD ["./catgpt"]