## Elastic Block Store
- attach to instances and allows for persisting data
- it's a network drive
- AZ wise
- Delete on Termination attribute

## EBS snapshots
- makes a backup of a volume at any point in time
- not necessary to detach volume to do a snapshot but recommended
- can copy snapshots across AZ or region

**EBS snapshot archives** - move snapshot to archive tier which is 75% cheaper; takes 24-72 hours to restore the archive

**Recycle bin for EBS snapshots** - setup rules to retain deleted snapshots; specify retention

**Fast snapshot restore** - force full initialisation of snapshot to have no latency on first use but costs a lot of moey
