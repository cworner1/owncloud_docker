
## Intro ##

- ownCloud is now ran in a docker container. Instructions from https://doc.owncloud.com/server/next/admin_manual/installation/docker/
- .yaml file builds the containers. I've modified the stock .yaml file to contain a bind mount instead of fixed volumes.
- Bind mount is located @ /mnt/owncloud, users files will be here.
- There is a hidden .env file that sets some variables for the yaml file.
- Name of the owncloud container as of writting this readme is "owncloud_server"

- There is a reverse proxy handling https traffic. Guide useed from here: https://owncloud.com/news/docker-owncloud-traefik-reverse-proxy-lets-encrypt-ssl/ 

	In a nutshell it's another container controlling the network. 
	At this current time I've got noip handling my DNS settings for cworner.com 
	It's been updated to direct the following hosts to my home server: "traefik.cworner.com" + "owncloud.cworer.com".

	mail.cworner.com should still be unaffected and directed to the server at work.


## Updating ownCloud ##

- Probably safer to check out the above link, or google. But there's a procedure to follow.

## Storage ##

- As previous mentioned, a bind mount sits in /mnt/opt. Therefore any user data can be transferred/backuped from there.

## Some commands ##

	View docker logs:
		docker logs owncloud_server

	Shut container down:
		docker kill owncloud_server

	Delete from local storage container:	
		docker rm owncloud_server
