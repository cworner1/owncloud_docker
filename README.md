# owncloud_docker

Credit to: andrzejd-pl

I've tweaked the following example (https://github.com/andrzejd-pl/owncloud-docker/blob/master/docker-compose.yml) to suit my needs:

- Bind mount owncloud data folder to /mnt/owncloud so I can access my files easily from the host.
- Used version 3 yaml file configuration and more up to date containers.
- Added more variables in .env file so I have more flexibility on credentials.

## How to use

To use it you must:
1. Install certbot `sudo apt install certbot`
2. Generate SSL cert using [certbot](https://certbot.eff.org/), e.g. `sudo certbot certonly --manual --preferred-challenges dns`
3. (If you haven't) Generate dhparams with `openssl dhparam -out ssl-dhparams.pem 2048` and move to `/etc/letsencrypt/` folder.
4. Fill the following environment variables in '.env. file
	- `ADMIN_USERNAME` 
	- `ADMIN_PASSWORD` 
	- `OWNCLOUD_DOMAIN`
	- `MYSQL_ROOT_PASSWORD`
	- `MYSQL_USER`
	- `MYSQL_PASSWORD`
5. Replace `domain.com` to your domain in `nginx-conf/default.conf` file.
