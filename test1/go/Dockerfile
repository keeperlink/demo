# Start from a Debian image with the latest version of Go installed
# and a workspace (GOPATH) configured at /go.
FROM golang

# Copy the local package files to the container's workspace.
ADD . /go/src/goserver

RUN mv /go/src/goserver/server.go .
RUN rm /go/src/goserver/*.go
RUN mv server.go /go/src/goserver/
RUN mv /go/src/goserver/*.key .
RUN mv /go/src/goserver/*.crt .

# Build the outyet command inside the container.
# (You may fetch or manage dependencies here,
# either manually or with a tool like "godep".)
RUN go install goserver

# Run the outyet command by default when the container starts.
ENTRYPOINT /go/bin/goserver

# Document that the service listens on port 8080.
EXPOSE 8080
