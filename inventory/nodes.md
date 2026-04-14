# Fleet Inventory

This document is the current working inventory for the Spot fleet and adjacent Starfleet infrastructure.

## Working rule
This file tracks the **currently active** naming and role layout.
Older hostnames, retired names, and deprecated role mappings belong in the archive or decision log, not here.

## Core control-plane context

### spot-core
- Role: primary Spot control-plane / scheduler / API gateway
- Primary responsibilities:
  - fleet orchestration
  - worker admission and routing
  - watcher/remediation scripts
  - shared operational logic
- Active paths:
  - `~/spot-stack/spot-core`
  - `~/spot-stack/watch`
- Shared storage mount:
  - `/mnt/collective`

## Worker nodes

### spot-worker-01
- IP: `192.168.10.10`
- OS: Ubuntu 22.04.5 LTS
- CPU: AMD EPYC 4245P
- RAM: 32 GB
- GPU: RTX 3060 12 GB
- Current role:
  - primary: general
  - secondary: coding
- Installed models:
  - `mistral:7b`
  - `llama3.1:8b`
- Notes:
  - strong general-purpose worker
  - suitable for light-to-mid inference

### spot-worker-02
- IP: `192.168.10.11`
- OS: Ubuntu 24.04.4 LTS
- Hardware: Dell Precision T3610
- CPU: Xeon E5-1620 v2
- RAM: 32 GB
- GPUs:
  - Quadro M4000 8 GB
  - GTX 1060 6 GB
- Current role:
  - primary: utility
  - secondary: general
- Installed models:
  - `bge-m3`
  - `nomic-embed-text`
  - `phi3.5`
- Notes:
  - utility / embeddings / support node
  - not preferred for heavy role work

### spot-worker-03
- IP: `192.168.10.13`
- OS: Ubuntu 24.04.4 LTS
- CPU: Ryzen 7 2700X
- RAM: 32 GB
- GPUs:
  - GTX 1070 8 GB
  - RTX 3060 12 GB
- Current role:
  - primary heavy/coding worker candidate
- Installed models:
  - `qwen2.5-coder:7b`
  - `codellama:7b`
  - `deepseek-coder:6.7b`
  - `qwen2.5:14b`
- Notes:
  - strong coding and heavier inference node
  - dual-GPU worker with flexibility

### spot-worker-04
- IP: `192.168.10.14`
- OS: Ubuntu 24.04.4 LTS
- CPU: i7-13700KF
- RAM: 64 GB
- GPU: TITAN Xp 12 GB
- Extra storage: `/mnt/ai-data`
- Installed models:
  - `qwen2.5:14b`
- Current role:
  - monitoring / heartbeat / premium inference support
- Notes:
  - should not sit idle
  - preferred as monitoring / heartbeat node while still available for premium tasks

## Shared infrastructure

### Unimatrix
- Role: shared storage / persistence target
- Address: `192.168.50.10`
- Export: `192.168.50.10:/volume1/docker`
- Mounted at: `/mnt/collective`
- Usage:
  - shared fleet storage
  - backups
  - tools
  - repo mirrors
  - memory/state artifacts

## Immediate follow-up items
- Add spot-core hardware profile
- Add service inventory per node
- Add backup verification state per node
- Add restore priority ordering
