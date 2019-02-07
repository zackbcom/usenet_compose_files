# compose_files

My docker-compose files for various applications. Feel free to use them as templates for yours.

Note all of these applications assume that you're using my traefik compose file and have it up and running first as it creates the docker network that the rest of the applications communicate on. Traefik assumes you have a wildcard ssl certificate for your domain, located in /etc/letsencrypt/live/some_domain. Be sure to check and edit all the compose.yml and .env files as needed. I'll get around to providing more detailed docs and comments some day.

I have multiple applications for some services, like nzbget and sabnzbd, couchpotato and radarr. I recommend only running _one_ application for each service at a time. Choice is good.

# things to look for

.env file - SERVER_HOST should be your FQDN of your server, example: _server.domain.com_ It will be used by traefik and all of the servers.

You also need to set up a path prefix in the configuration for most of these applications. Where/how to do that will vary, but look for something referring to "reverse proxy path" or the like and use "/application" or whatever you specify in the compose file.
