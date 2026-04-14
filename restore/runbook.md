# Restore Runbook

## Goal
Rebuild any node from scratch with minimal guesswork.

## General process
1. Install base OS (Ubuntu)
2. Set hostname
3. Configure network (static or DHCP reservation)
4. Mount `/mnt/collective`
5. Pull required configs/scripts
6. Restore services
7. Validate health

## Spot worker restore
- Install Ollama
- Restore model list
- Restore worker config
- Re-register with spot-core

## Spot-core restore
- Restore `spot-stack`
- Restore watcher scripts
- Restore fleet configuration
- Validate API endpoints

## Validation
- Node responds to ping
- Services are listening
- Spot sees node as healthy

## Rule
If a restore requires memory or guessing, document the missing step immediately.
