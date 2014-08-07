docker-reposado
===============

Docker container to run reposado and serve softwareupdates using nginx

sample usage. 

```bash
 docker run --rm -i -t macadmins/reposado python /reposado/code/repoutil --help
 ```
 To have persistent storage, use a volume container. Example:
 ```bash
 docker run --rm -i -t --volumes-from reposado-data macadmins/reposado python /reposado/code/repo_sync
 ```
You can schedule the above command via cron/systemd or run it manually.

##Note/Todo
Currently, the port *has* to be 8080 for both the container and the host.
