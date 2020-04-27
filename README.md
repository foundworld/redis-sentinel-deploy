## sentinel.conf ##
Include sentinel configuration.
* auth-pass is the password that is used for connecting to redis master.
* sentinel1.conf, sentinel2.conf, sentinel3.conf are three copies of sentinel.conf

## ymal files ##
* docker-compose-master-slave.yml - create redis one master with two slaves.
* docker-compose-sentinel.yaml - create redis three sentinels.
the master and slaves must be created first, then create sentinels.
the command:
```
# docker-compose -f docker-compose-master-slave.yml up &
# docker-compose -f docker-compose-sentinel.yaml up &
```
we didn't defined network in these files, so the default network name will be the directory name with '_default'. e.g. "redis-setup-directory_default".
** if you don't want to declare a network, and you want to deploy other containers which will connect to the redis sentinel group. You can copy your docker compose files to the same directory, then run docker-compose command in it. they will be in the same network. ;-)
