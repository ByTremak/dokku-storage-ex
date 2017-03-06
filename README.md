# dokku-storage-ex

Create and remove host directories for persistent storage. Companion for `storage:mount` and `storage:unmount`.

By default, takes an `app-name` and appends it to the default persistent storage path: `/var/lib/dokku/data/storage`

## commands

|Command|Description|
|---|---|
|`dokku storage-ex:exists <app-name or host-dir>`|Check if host path exists.|
|`dokku storage-ex:create <app-name or host-dir>`|Create host directory for app-name or host-dir.|
|`dokku storage-ex:remove <app-name or host-dir>`|Remove host directory for app-name or host-dir.|


> :warning: **WARNING:** _storage-ex:remove_ recursively deletes the requested directory. It requires **root** or **admin** access and will ask for confirmation before continuing, but it **WILL** cause data loss if you're not careful. Use the **app-name** version of the commands when possible.

## requirements

- dokku 0.4.x+
- docker 1.8.x

## installation

```shell
# on 0.4.x+
sudo dokku plugin:install https://github.com/ByTremak/dokku-storage-ex.git storage-ex
```

## usage

```shell
# verify 'lolipop' app exists, create /var/lib/dokku/data/storage/lolipop if necessary
dokku storage-ex:create lolipop
# create designated host directory
dokku storage-ex:create /var/lib/dokku/data/storage/any-dir

# verify 'lolipop' app exists, confirm /var/lib/dokku/data/storage/lolipop exists
dokku storage-ex:exists lolipop
# confirm designated host directory exists
dokku storage-ex:exists /var/lib/dokku/data/storage/any-dir

# verify 'lolipop' app exists, remove /var/lib/dokku/data/storage/lolipop after requesting confirmation
dokku storage-ex:remove lolipop
# remove designated host directory after requesting confirmation
dokku storage-ex:remove /var/lib/dokku/data/storage/any-dir
```
