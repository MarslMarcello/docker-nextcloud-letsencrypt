# docker-nextcloud-letsencrypt
My Docker-Nextcloud-Setup for small self-hosted v-servers easy to use, easy to deploy. I will continue developing the settings and security.

Requirements: You will need [Docker](https://docs.docker.com/engine/install/) & [Docker-Compose](https://docs.docker.com/compose/install/) installed and configured. 

## **How to use/start**

1. clone the repo
2. open `docker-compose.yml`with your favorite editor
3. change the _domain_ and _email_ with your data
4. check name for _network_ and the _path_ for _volumes_ etc.
5. set your own _password_ for MySQL/MariaDB **root user** and **Nextcloud DB user**
6.  check `nextcloud.ini` and edit it with your values if necessary
7.  check `my_proxy.conf` and edit the values if necessary
8. start it with `docker-compose up -d`
9. open a browser and enter your preset domain 
10. finish the initial Nextcloud Setup
11. it might be to add `'overwriteprotocol' => 'https',` to the `config.php` for Nextcloud to get `https` only and make desktop and mobile authorization work
12. add `'filelocking.enabled' => false,` to the `config.php` to avoid filelocking
13. add `'default_phone_region' => 'DE',`to the `config.php` to enable default locale on your Nextcloud server (e.g. Germany)
14. navigate to `your-path/app/config` to open `config.php` with vi/vim and add the line from point 11. - 13.
15. optional: it might be you have to install manually SVG support. Exec it with `Docker exec -it nextcloud-app bash` and execute in the container `apt update && apt install -y libmagickcore-6.q16-6-extra` and reboot the service e.g. `docker-compose restart app` (use the name of your defined server from compose file.)

### Planned improvements:

* improving security by using passwords in a more secure way
* add point 11 - 13 automatically with the initial setup


The following Repos/Hub-images have been used:

###### JWILDER - Nginx-Proxy
https://hub.docker.com/r/jwilder/nginx-proxy/
https://github.com/nginx-proxy/nginx-proxy

###### JRCS - Let's encrypt Nginx-Proxy
https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion/
https://github.com/nginx-proxy/docker-letsencrypt-nginx-proxy-companion

###### MariaDB
https://hub.docker.com/_/mariadb
https://github.com/docker-library/mariadb

###### Nextcloud
https://nextcloud.com/
https://github.com/nextcloud

Thank you to the community for all open source software and public repositories.