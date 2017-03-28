# aptly-scripts

Script to manage aptly repositories.

Basic workflow is:

- initialize a mirror of your repositories (only done once): `init-mirror`
- update your mirrors (done regularly): `update-release-mirror`
- create a snapshot of your mirrors: `create-release-snapshot`
- merge your snapshots into one snapshot: `merge-release-snapshot`
- publish your merged snapshot: `snapshot-publish`

## init-mirror

Initialize a mirror.  We sync from http://ftp.de.debian.org/debian the amd64,i386 architectures and "main non-free contrib" components.  We also sync the security mirror for that release.

```
init-mirror squeeze|wheezy|jessie
```

## update-release-mirror

Sync from upstream, you can just give the release name (e.g. wheezy) or a specfic mirror.
```
update-release-mirror <release-name|mirror-name>
```

## create-release-snapshot

Create "release snapshots".  We create for every snapshot of a specific release (e.g. wheezy) a dated snapshot.  You can also override the date.
```
create-release-snapshot <release-name|mirror-name> [date]
```

## merge-release-snapshot

Merge the snapshots into one snapshot that can be published.  We give the snapshot a basename and must give the date.

```
merge-release-snapshot <release-name|mirror-name> <date> <basename> 
```

## snapshot-publish

Publish a merged snapshot.  Use the basename and date you gave in the previous command.
```
snapshot-publish  <release-name|mirror-name> <date> <basename> <latest|prd>
``` 

## cleanup-snapshots

Delete old snapshots and cleanup the db
```
cleanup-snapshots <release-name|mirror-name> <date>
``` 
