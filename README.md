# FreeBSD Ports Collection for codebase-memory-mcp

This directory contains FreeBSD Ports Collection definitions for compiling and installing `codebase-memory-mcp` and `codebase-memory-mcp-ui` natively on FreeBSD under the `devel` category.

These ports build natively from source utilizing the comprehensive, production-grade `Makefile.cbm` (via GNU `gmake`).

---

## Ports Included

### 1. `devel/codebase-memory-mcp`
* **Description:** Standard, lightweight Model Context Protocol (MCP) server daemon.
* **Build Requirements:** GMake, C11 compiler, SQLite3.

### 2. `devel/codebase-memory-mcp-ui`
* **Description:** Model Context Protocol (MCP) server with an embedded 3D React/Vite-based three.js code-graph visualizer.
* **Build Requirements:** NPM/Node.js (for asset compilation), GMake, C11 compiler, SQLite3.

---

## Built-In Features & Enhancements

### 🛡️ Production Hardening Enabled by Default
As recommended by Martin, security hardening has been refactored to be fully generic (`HARDENING`) and is **enabled by default (`HARDENING=1`)** in the base `Makefile.cbm` for ELF builds. All downstream environments automatically build with:
* **Position-Independent Code & Executable (`-fPIE` / `-pie`)**: Generates dynamic position-independent machine code for defense-in-depth address space layout randomization (ASLR).
* **Stack Smash Protection (`-fstack-protector-strong`)**: Detects stack buffer overflows before execution.
* **Fortified Source (`-D_FORTIFY_SOURCE=2`)**: Performs compile-time and runtime validation on memory operations.
* **Read-Only Relocations (`-z relro`)**: Places critical sections of executable headers in read-only tables.
* **Immediate Binding (`-z now`)**: Resolves dynamic symbols on startup to protect against PLT/GOT attacks.

### 🧪 Full Regression Testing
Both ports fully implement the standard FreeBSD `do-test` regression target using the native test harness within `Makefile.cbm`.

---

## Installation Guide

### Step 1: Copy to your local Ports Collection
Copy these folders directly into `/usr/ports/devel/`:

```bash
sudo cp -R codebase-memory-mcp /usr/ports/devel/
sudo cp -R codebase-memory-mcp-ui /usr/ports/devel/
```

### Step 2: Generate Checksums (`distinfo`)
```bash
cd /usr/ports/devel/codebase-memory-mcp
sudo make makesum

cd /usr/ports/devel/codebase-memory-mcp-ui
sudo make makesum
```

### Step 3: Run Direct Tests (Optional but Recommended)
To run the full regression test suite (ASan + UBSan enabled):

```bash
cd /usr/ports/devel/codebase-memory-mcp
sudo make test
```

### Step 4: Build & Install

```bash
cd /usr/ports/devel/codebase-memory-mcp
sudo make install clean
```

Or for the UI-embedded variant:

```bash
cd /usr/ports/devel/codebase-memory-mcp-ui
sudo make install clean
```
