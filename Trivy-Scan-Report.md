# Trivy Vulnerability Scan Report

**Date:** April 21, 2026  
**Source:** aks-store-all-in-one.yaml

---

## Scanned Images and Key Findings

### 1. mongo:4.2
- **CRITICAL:**
   - CVE-2023-45853 (zlib): Integer overflow and heap-based buffer overflow. [Details](https://avd.aquasec.com/nvd/cve-2023-45853)
   - CVE-2025-15467 (openssl): Remote code execution or DoS via oversized Initialization Vector. [Details](https://avd.aquasec.com/nvd/cve-2025-15467)
- **HIGH:**
   - Multiple vulnerabilities in system libraries (Debian, OpenSSL, etc.)
- **Recommendation:** Use a newer MongoDB image and update all dependencies.

### 2. rabbitmq-server:3.13
- **CRITICAL:**
   - CVE-2025-15467 (openssl): Remote code execution or DoS. [Details](https://avd.aquasec.com/nvd/cve-2025-15467)
- **HIGH:**
   - Vulnerabilities in Erlang, OpenSSL, systemd.
- **Recommendation:** Update RabbitMQ and base image to the latest version.

### 3. order-service:2.1.0
- **CRITICAL/HIGH:**
   - Node.js/npm vulnerabilities (RCE, DoS, privilege escalation).
   - Example: CVE-2024-27980 (Node.js): HTTP request smuggling. [Details](https://avd.aquasec.com/nvd/cve-2024-27980)
- **Recommendation:** Update Node.js, npm, and all dependencies.

### 4. busybox:1.37.0
- **HIGH/MEDIUM:**
   - BusyBox utilities vulnerabilities (DoS, buffer overflow).
- **Recommendation:** Use the latest BusyBox image.

### 5. makeline-service:2.1.0
- **CRITICAL:**
   - CVE-2023-45853 (zlib): Integer overflow. [Details](https://avd.aquasec.com/nvd/cve-2023-45853)
- **HIGH:**
   - CVE-2025-15467 (openssl): RCE/DoS. [Details](https://avd.aquasec.com/nvd/cve-2025-15467)
   - CVE-2026-29111 (systemd): Arbitrary code execution or DoS. [Details](https://avd.aquasec.com/nvd/cve-2026-29111)
- **Recommendation:** Rebuild with updated Go base image and dependencies.

### 6. product-service:2.1.0
- **CRITICAL/HIGH:**
   - Rust and system library vulnerabilities (RCE, DoS, buffer overflow).
- **Recommendation:** Update Rust toolchain and dependencies.

### 7. store-front:2.1.0
- **CRITICAL/HIGH:**
   - Node.js, npm, and system library vulnerabilities (RCE, DoS, XSS).
- **Recommendation:** Update Node.js, npm, and all dependencies.

### 8. store-admin:2.1.0
- **CRITICAL/HIGH:**
   - Node.js, npm, and system library vulnerabilities (RCE, DoS, XSS).
- **Recommendation:** Update Node.js, npm, and all dependencies.

### 9. virtual-customer:2.1.0
- **CRITICAL:**
   - CVE-2025-15467 (openssl): RCE/DoS. [Details](https://avd.aquasec.com/nvd/cve-2025-15467)
   - CVE-2023-45853 (zlib): Integer overflow. [Details](https://avd.aquasec.com/nvd/cve-2023-45853)
- **HIGH:**
   - CVE-2026-29111 (systemd): Arbitrary code execution or DoS. [Details](https://avd.aquasec.com/nvd/cve-2026-29111)
   - CVE-2025-69720 (ncurses): Buffer overflow. [Details](https://avd.aquasec.com/nvd/cve-2025-69720)
- **Recommendation:** Update Debian base image and all system packages.

### 10. virtual-worker:2.1.0
- **CRITICAL:**
   - CVE-2025-15467 (openssl): RCE/DoS. [Details](https://avd.aquasec.com/nvd/cve-2025-15467)
   - CVE-2023-45853 (zlib): Integer overflow. [Details](https://avd.aquasec.com/nvd/cve-2023-45853)
- **HIGH:**
   - CVE-2026-29111 (systemd): Arbitrary code execution or DoS. [Details](https://avd.aquasec.com/nvd/cve-2026-29111)
   - CVE-2025-69720 (ncurses): Buffer overflow. [Details](https://avd.aquasec.com/nvd/cve-2025-69720)
   - CVE-2026-27456 (util-linux): TOCTOU in mount. [Details](https://avd.aquasec.com/nvd/cve-2026-27456)
- **Recommendation:** Update Debian base image and all system packages.

---

## General Recommendations

- Always use the latest stable base images.
- Regularly update all dependencies and system packages.
- Rebuild and redeploy images after patching vulnerabilities.
- Consider using minimal base images to reduce the attack surface.

---

If you need a full vulnerability table for each image or a different format, please specify your requirements.
