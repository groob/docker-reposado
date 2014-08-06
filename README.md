docker-reposado
===============

Docker container to run reposado and serve softwareupdates using nginx

sample usage. 

```bash
 docker run --rm -i -t groob/reposado python /reposado/code/repoutil --help
 ```
 To have persistent storage, use a volume container. Example:
 ```bash
 docker run --rm -i -t --volumes-from reposado-data groob/reposado python /reposado/code/repo_sync
 ```
You can schedule the above command via cron/systemd or run it manually.
