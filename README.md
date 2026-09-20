# quorum-kv-storage-raft-engine

`quorum-kv-storage-raft-engine` is a multi-language distributed systems project that combines:

- **Track A (`/storage`)**: a Rust LSM-style key-value storage engine with WAL, memtable, SSTables, bloom filtering, and compaction.
- **Track B (`/consensus`)**: a Go Raft consensus layer for replicated state machine behavior and fault-tolerant cluster coordination.
- **Dashboard (`/dashboard`)**: a Flask app to run tests and interact with a live Raft sandbox visually.

## Repository layout

- `/storage` — Rust crate (`quorumkv-storage`) and tests
- `/consensus` — Go module (`quorumkv/consensus`) and tests
- `/dashboard` — Python dashboard for test orchestration and sandbox controls

## Getting started

### Prerequisites

- Rust toolchain (`cargo`)
- Go toolchain (`go`)
- Python 3 (`pip`)

### Run storage tests (Rust)

```bash
cd /home/runner/work/quorum-kv-storage-raft-engine/quorum-kv-storage-raft-engine/storage
cargo test
```

### Run consensus tests (Go)

```bash
cd /home/runner/work/quorum-kv-storage-raft-engine/quorum-kv-storage-raft-engine/consensus
go test ./...
```

### Run the dashboard

```bash
cd /home/runner/work/quorum-kv-storage-raft-engine/quorum-kv-storage-raft-engine/dashboard
pip install -r requirements.txt
python app.py
```

Open: `http://127.0.0.1:5055/`

## Design intent

This project separates **local storage concerns** (Rust engine) from **distributed consensus concerns** (Go Raft) to keep each subsystem focused, testable, and independently evolvable while still enabling end-to-end experimentation through the dashboard sandbox.
