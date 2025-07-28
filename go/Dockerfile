FROM golang:1.16
WORKDIR /app
COPY main.go .
RUN go mod init my-go-app
RUN go build -o my-go-app .
CMD ["./my-go-app"]
EXPOSE 8080