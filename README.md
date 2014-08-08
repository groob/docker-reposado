docker-reposado
===============

Docker container to run reposado and serve softwareupdates using nginx

sample usage. 

```
 docker run --rm -i -t macadmins/reposado python /reposado/code/repoutil --help
 ```
 To have persistent storage, use a volume container. Example:
 ```
 docker run --rm -i -t --volumes-from reposado-data macadmins/reposado python /reposado/code/repo_sync
 ```
You can schedule the above command via cron/systemd or run it manually.

##Note
Currently, the port *has* to be 8080 for both the container and the host. The LocalCatalogBaseURL is http://reposado:8080

#Margarita 
[Margarita](https://github.com/jessepeterson/margarita) is also bundled in but not enabled by default. 
You can run the Margarita Flask server either together with nginx, by opening both -p 8080 and -p 8089 or separately like so:
```
/usr/bin/docker run --rm --name margarita --volumes-from reposado-data -p 8089:8089 macadmins/reposado python /home/app/margarita/margarita.py
```

#TODO
* passenger_wsgi script for margarita
* nginx configuration file for margarita
* move reposado.conf and margarita.conf to sites-available and symlink to sites-enabled as needed
* basic authentication for margarita
* allow using a different LocalCatalogBaseURL (suggestions welcome)
