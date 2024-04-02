# Used the official Go image as the base
FROM golang:1.19 AS builder

# Changed the working directory inside the container
WORKDIR /app

# Copy the Go application source code into the container
COPY . .

# Build the Go application
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

# Expose port 8080
EXPOSE 8080

# Command to start the Go application
CMD ["./app"]
