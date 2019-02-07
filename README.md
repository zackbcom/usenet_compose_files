# compose_files

My docker-compose files for various applications. Feel free to use them as templates for yours.
Note all of these applications assume that you're using my traefik compose file and have it up and running first as it creates the docker network that the rest of the applications communicate on. Traefik assumes you have a wildcard ssl certificate for your domain, located in /etc/letsencrypt/live/some_domain. Be sure to check and edit all the compose.yml and .env files as needed. I'll get around to providing more detailed docs and comments some day.
