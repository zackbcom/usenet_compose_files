# compose_files

My docker-compose files for various applications. Feel free to use them as templates for your own use, they will require some setup to work properly in your environment.

Note all of these applications assume that you're using my traefik compose file and have it up and running first as it creates the docker network that the rest of the applications communicate on. Traefik assumes you have a wildcard ssl certificate for your domain, located in /etc/letsencrypt/live/some_domain. Be sure to check and edit all the compose.yml and .env files as needed. I'll get around to providing more detailed docs and comments some day.

I have multiple applications for some services, like nzbget and sabnzbd, couchpotato and radarr. I recommend only running _one_ application for each service at a time. Choice is good.

I prefer running one service per compose file. This way I can have better control over what is running and what isn't. You can use portainer for web-based management, or combine what's in these files into consolidated files.

These compose files were built on a Linux server, they may or may not work properly on other operating systems, you are welcome to port them, but I only use Linux (Ubuntu 18.04 LTS).

I try to use official images from the application when I can, or the amazing containers from the Linuxserver.io team, a few are from other well-maintained sources. I make no guaratees, warranty or assume liability for any of the images and you're certainly free to use others.

# setup and configuration

### compose file configuration

.env file - SERVER_HOST should be your FQDN of your server, example: _server.domain.com_ It will be used by traefik and all of the servers.

You need to set up a few paths. I store all my media in /media and downloads generally go to /mnt/transfer/usenet, so you will probably need to change these paths to match your directory structure.


### application configuration

You will need to set up a path prefix in the configuration for most of these applications. Where/how to do that will vary, but look for something referring to "reverse proxy path" or the like and use "/application" or whatever you specify in the compose file. The easiest way is to first expose the port from the container, configure as needed, then remove the exposed port, or leave it open for direct access from your internal network.

I chose not to use Traefik's authentication generally because some applications had issues with it, instead I rely on user management within each applicaiton, also some applications store settings and such per-user, such as NZBHydra2.

### network configuration

Obviously you're going to need an internet connection, this all will work fine with a dynamic or static IP address but you will need a FQDN at the minimum, a few extra for some services that don't play well with reverse proxies. You will need port 80 open for http connections, 443 for https, and if you use the gitea instance 3022 for ssh if you use that as well. Taefik is set to re-direct http connections to https, so you can leave 80 closed. While I use a manually generated Let's Encrypt wildcard key you can subsitute in whatever key you wish by editing traefik's compose file. I do _not_ recommend running applications over an unencrypted http connection, even on a secure internal network.


# suggestions welcome

These files work for me but they could be better, please feel free to suggest improvements and report problems.
