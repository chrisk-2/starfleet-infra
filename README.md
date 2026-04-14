# Starfleet Infra

This repository is the infrastructure source of truth for the Starfleet environment.

## Purpose
This repo exists to describe how the real environment is built, backed up, restored, and operated.

It answers four questions:
1. What machines and services exist?
2. What is each machine supposed to do?
3. How do we back it up?
4. How do we rebuild it when something dies?

## What belongs here
- Node inventory
- Hardware profiles
- Network layout
- Storage layout
- Backup policy
- Restore procedures
- Service dependency maps
- Operational runbooks
- Environment standards
- Decision records affecting infrastructure

## What does not belong here
- Application feature code
- OS product code
- Raw brainstorming dumps
- Random one-off experiments with no operational value

## Core directories
- `inventory/` fleet-wide inventory and high-level manifests
- `nodes/` per-node profiles and rebuild notes
- `backups/` backup policy, destinations, schedules, validation
- `restore/` disaster recovery and rebuild runbooks
- `network/` topology, addressing, VLANs, and service reachability
- `storage/` mounts, shares, persistence rules
- `runbooks/` standard operational procedures
- `standards/` naming, baseline config rules, conventions
- `decisions/` dated records for why infra decisions were made

## Relationship to other repos
- `spotd` = live Spot runtime and automation
- `starfleet-os` = the actual product/platform code
- `starfleet-concepts` = design intent, ideas, and distilled planning history
- `starfleet-archive` = cold storage for deprecated or inactive material

## First build targets
1. Capture node inventory
2. Capture backup and restore policy
3. Capture network/storage truth
4. Document minimum rebuild path for each critical node

## Spot integration goal
Spot should be able to read this repository to understand:
- current environment state
- expected node roles
- backup locations
- restore order
- critical dependencies
