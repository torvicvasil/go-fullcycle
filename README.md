# go-fullcycle
Desafio Docker Go


Dockerfile

FROM golang:1.13-alpine3.11 AS builder 

WORKDIR /app
COPY . .
RUN go build main.go

FROM scratch
WORKDIR /app 
COPY --from=builder /app . 
CMD ["/app/main"]


main.go

package main
import "fmt"
func main() {
    fmt.Println("Code.education Rocks!")
}

Para rodar:

~$ docker build -t torvicvasil/codeeducation go
~$ docker run torvicvasil/codeeducation

docker images
REPOSITORY                  TAG       IMAGE ID       CREATED          SIZE
torvicvasil/codeeducation   latest    86c221d1cc9d   8 minutes ago    2.01MB

Refs.: 
https://hub.docker.com/_/scratch
https://tutorialedge.net/golang/go-docker-tutorial/
https://gobyexample.com/hello-world
https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes





