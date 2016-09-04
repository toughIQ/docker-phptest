# docker-phptest
Simple PHP Test Container

Can be used to demo serivce upgrades.

`:latest`/`:7` tag uses PHP 7 Apache base image.
`:5` tag is based on PHP 5.6 Apache base image.

Example for upgrade demo:

Using Docker 1.12 in Swarm mode:

`docker service create --name phpdemo --publish 80:80 --replicas 10 toughiq/phptest:5`

Now you have 10 instances running on Port 80. 
Check: `docker service ps phpemo`

If you access the server and hit Reload, you should
see different container IDs.

Now lets upgrade:
`docker service update --update-delay 5s --image toughiq/phptest:7 phpdemo`

We update our 10 instances to version 7. Interval between each container is 5 seconds.
During this update you should see different versions of the app, if you hit reload in your browser.
