# Snapshots
### List
```bash
vagrant snapshot list
```

### Save
- FIXME: Restore will hang if snapshot is taken of running VM
```bash
vagrant ssh -- sudo shutdown now
vagrant snapshot save snapshot1
```

### Restore
- FIXME: Sometimes network doesn't work after restore
```bash
vagrant snapshot restore --no-provision snapshot1
```