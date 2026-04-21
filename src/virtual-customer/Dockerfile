FROM rust:1.80 AS builder

RUN USER=root cargo new --bin virtual-customer


# Create a new directory for our application
WORKDIR /virtual-customer


# Copy the manifest and lock files first for better caching
COPY Cargo.toml Cargo.lock ./
RUN cargo build --release || true
# Remove the .rs files created by cargo
RUN rm src/*.rs
# Copy the source files to the container
COPY . ./
# Remove the dummy target directory created by cargo and build the application
RUN rm ./target/release/deps/virtual_customer* && cargo build --release

# Create a new stage and copy the binary from the builder stage
FROM debian:bookworm-slim AS runner
WORKDIR /app


# Set the build argument for the app version number
ARG APP_VERSION=0.1.0


# Install OpenSSL (pin version, use --no-install-recommends)
RUN apt-get update \
	&& apt-get install -y --no-install-recommends libssl-dev=1.1.1n-0+deb11u3 \
	&& rm -rf /var/lib/apt/lists/*
# Add non-root user for security
RUN addgroup --system appgroup && adduser --system --ingroup appgroup appuser


# Copy the binary from the builder stage
COPY --from=builder /virtual-customer/target/release/virtual-customer /app


# Set the environment variable for the app version number
ENV APP_VERSION=$APP_VERSION

# Change to non-root user
USER appuser

# Run the application
CMD ["./virtual-customer"]