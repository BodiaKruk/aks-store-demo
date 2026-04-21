# Use an official Golang runtime as a parent image
FROM golang:1.24-alpine AS builder


# Set the working directory to /app
WORKDIR /app


# Set the build argument for the app version number
ARG APP_VERSION=0.1.0


# Copy go.mod and go.sum first for better layer caching
COPY go.mod go.sum ./
RUN go mod download
# Copy the rest of the source code
COPY . .


# Build the Go app
RUN go build -ldflags "-X main.version=$APP_VERSION" -o main .

# Run the app on alpine
FROM alpine:3.22 AS runner


ARG APP_VERSION=0.1.0


# Add non-root user for security
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
# Copy the build output from the builder container
COPY --from=builder /app/main .


# Expose port 3001 for the container
EXPOSE 3001


# Set the environment variable for the app version number
ENV APP_VERSION=$APP_VERSION


# Change to non-root user
USER appuser
# Run the Go app when the container starts
CMD ["./main"]