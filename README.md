## jefferyb/islandora-enterprise-all-in-one
An install of [islandora enterprise](https://wiki.duraspace.org/display/ISLANDORA/Enterprise) in docker... 

## Supported tags

-	[`7.x` (*Dockerfile*)](https://github.com/jefferyb/islandora-7.x-docker/blob/master/enterprise/all-in-one/islandora-7.x/Dockerfile)
-	[`7.x-1.8, latest` (*Dockerfile*)](https://github.com/jefferyb/islandora-7.x-docker/blob/master/enterprise/all-in-one/islandora-7.x-1.8/Dockerfile)
-	[`7.x-1.7` (*Dockerfile*)](https://github.com/jefferyb/islandora-7.x-docker/blob/master/enterprise/all-in-one/islandora-7.x-1.7/Dockerfile)
-	[`7.x-1.6` (*Dockerfile*)](https://github.com/jefferyb/islandora-7.x-docker/blob/master/enterprise/all-in-one/islandora-7.x-1.6/Dockerfile)
-	[`7.x-1.5` (*Dockerfile*)](https://github.com/jefferyb/islandora-7.x-docker/blob/master/enterprise/all-in-one/islandora-7.x-1.5/Dockerfile)

## How to use this image?

Run:

```bash
docker run -d --name islandora-enterprise-all-in-one -p 80:80 -p 8080:8080 jefferyb/islandora-enterprise-all-in-one
```
## Volumes:

Here are the available volumes (Please let me know if there's one that I might have missed and I can add it... Thanks)

##### MYSQL
VOLUME /var/lib/mysql

##### FEDORA
VOLUME /usr/local/fedora/data
VOLUME /usr/local/fedora/server/config

##### DRUPAL
VOLUME /var/www/html/sites

##### SOLR
VOLUME /usr/local/fedora/solr

## Docker Compose example:

```yaml
version: '2'

services:
  islandora:
    image: jefferyb/islandora-enterprise-all-in-one
    hostname: islandora.example.com
    restart: always
    container_name: islandora-enterprise-server
    ports:
      - 80:80
      - 8080:8080
    volumes:
      - islandora-mysql:/var/lib/mysql
      - islandora-drupal:/var/www/html/sites/default
      - islandora-fedora-data:/usr/local/fedora/data
      - islandora-fedora-config:/usr/local/fedora/server/config
      - islandora-solr:/usr/local/fedora/solr
    environment:
      - "TZ=America/Chicago"

volumes:
  islandora-solr:
  islandora-mysql:
  islandora-drupal:
  islandora-fedora-data:
  islandora-fedora-config:
```

## Login:

Once it's up and running, visit your host/container's IP (or hostname, depending on your network setup) and login to Drupal (Islandora) with:

Username: **admin**

Password: **islandora**

