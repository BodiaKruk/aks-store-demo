# Trivy Vulnerability Scan Report

**Date:** April 21, 2026  
**Source:** aks-store-all-in-one.yaml

---

## Scanned Images and Key Findings

1. **mongo:4.2**
   - Multiple CRITICAL and HIGH vulnerabilities (Debian, OpenSSL, zlib, etc.).
   - Recommendation: Use a newer MongoDB image and update all dependencies.

2. **rabbitmq-server:3.13**
   - CRITICAL vulnerabilities in Erlang, OpenSSL, and system libraries.
   - Recommendation: Update RabbitMQ and base image to the latest version.

3. **order-service:2.1.0**
   - Node.js and npm-related CRITICAL/HIGH vulnerabilities.
   - Recommendation: Update Node.js, npm, and all dependencies.

4. **busybox:1.37.0**
   - Several HIGH and MEDIUM vulnerabilities in BusyBox utilities.
   - Recommendation: Use the latest BusyBox image.

5. **makeline-service:2.1.0**
   - Go-related and system library vulnerabilities (CRITICAL/HIGH).
   - Recommendation: Rebuild with updated Go base image and dependencies.

6. **product-service:2.1.0**
   - Rust and system library vulnerabilities (CRITICAL/HIGH).
   - Recommendation: Update Rust toolchain and dependencies.

7. **store-front:2.1.0**
   - Node.js, npm, and system library vulnerabilities (CRITICAL/HIGH).
   - Recommendation: Update Node.js, npm, and all dependencies.

8. **store-admin:2.1.0**
   - Node.js, npm, and system library vulnerabilities (CRITICAL/HIGH).
   - Recommendation: Update Node.js, npm, and all dependencies.

9. **virtual-customer:2.1.0**
   - CRITICAL vulnerabilities in OpenSSL, zlib, systemd, ncurses, etc.
   - Recommendation: Update Debian base image and all system packages.

10. **virtual-worker:2.1.0**
    - CRITICAL vulnerabilities in OpenSSL (RCE, DoS), zlib, systemd, ncurses, util-linux, etc.
    - Recommendation: Update Debian base image and all system packages.

---

## General Recommendations

- Always use the latest stable base images.
- Regularly update all dependencies and system packages.
- Rebuild and redeploy images after patching vulnerabilities.
- Consider using minimal base images to reduce the attack surface.

---

If you need a detailed vulnerability list for each image or a formatted export (CSV, HTML, etc.), please specify your requirements.
