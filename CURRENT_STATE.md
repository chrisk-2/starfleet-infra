# Current State

## Status
Active and authoritative for infrastructure truth.

## What is currently true
- Active Spot control-plane workflow uses `spot-core` and `spot-worker-*` naming.
- Shared fleet storage is mounted from Unimatrix at `/mnt/collective`.
- Worker inventory and current role mapping are tracked in this repository.
- Backups are intended to be append-only and created before system changes.
- Restore expectations are documented here and should be expanded whenever rebuilds expose missing steps.

## Immediate priorities
1. Keep worker inventory current.
2. Add per-node service manifests.
3. Add backup verification status.
4. Add restore priority order and dependency chains.

## Consumer
Spot should treat this repository as the source of truth for infrastructure, backup, restore, storage, and network state.
