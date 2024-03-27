# ---- stage1 ----
FROM golang:alpine  AS builder

WORKDIR /go/src/app 
COPY main.go .


RUN go mod init
RUN go build -o webserver .

CMD ["./webserver"]

# ---- stage2 ----
FROM scratch

WORKDIR /app
COPY --from=builder /go/src/app /app/

# EXAMPLE
# RUN apt update
# RUN apt install -y nginx
# RUN apt install -y pkg2
# => Layer 3개 생성

# RUN apt update && apt install -y nginx pkg2 => Layer 1개 생성

CMD ["./webserver"]