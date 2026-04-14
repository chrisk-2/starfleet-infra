# Backup Policy

## Rule zero
Before any system change, a backup must exist.

## Backup target
- Primary: `/mnt/collective`
- Backend: Unimatrix (`192.168.50.10`)

## What gets backed up
- Spot configuration
- Worker configuration
- Model lists / manifests
- Critical scripts (`spot-stack`)
- Any state needed to rebuild node roles

## Backup structure
```
/mnt/collective/backups/
  <node-name>/
    <timestamp>/
      config/
      services/
      models/
      notes.json
```

## Rules
- Backups are append-only
- No deletion by automation
- Each change creates a new snapshot

## Validation
- Backups must be readable
- Restore must be tested periodically

## Future
- Add automatic pre-change backup hooks in Spot
- Add verification jobs
