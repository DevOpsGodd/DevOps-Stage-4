# Use the official Golang image with version 1.21.1
FROM golang:1.21.1-alpine AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the Go module files
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the rest of the application code
COPY . .

# Build the application
RUN go build -o auth-api .

# Use a lightweight Alpine image for the final stage
FROM alpine:latest

# Set the working directory
WORKDIR /app

# Copy the built binary from the build stage
COPY --from=build /app/auth-api .

# Copy the .env file (if needed)
COPY .env .

# Expose the port the application will run on
EXPOSE 8081

# Command to run the application
CMD ["./auth-api"]
