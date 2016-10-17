## jefferyb/islandora-enterprise-all-in-one
An install of [islandora enterprise](https://wiki.duraspace.org/display/ISLANDORA/Enterprise) in docker... Still need some work...

## Supported tags

-	[`latest` (*Dockerfile*)](https://github.com/jefferyb/islandora-7.x-docker/blob/master/enterprise/all-in-one/Dockerfile)

## How to use this image?

Run:

```console
docker run -d --name islandora-enterprise-all-in-one -p 80:80 -p 8080:8080 jefferyb/islandora-enterprise-all-in-one
```

Once it's up and running, visit your host/container's IP (or hostname, depending on your network setup) and login to Drupal (Islandora) with:

Username: admin

Password: islandora

