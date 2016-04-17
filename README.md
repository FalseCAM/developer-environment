# developer-environment
*Docker Containers for Developing*

 * gitlab
 * jenkins
 * nginx

## Quick Start

Clone repository
	`git clone https://github.com/FalseCAM/developer-environment`

Change into source directory
	`cd developer-environment`

Edit compose for your needs
	`vim docker-compose.yml`

Build docker compose
	`docker-compose build`

Run docker compose
	`docker-compose up -d`

Stop docker compose
	`docker-compose stop`

## Tipps

To test locally change `127.0.0.1	localhost jenkins.localhost lam.localhost gitlab.localhost`
in your /etc/hosts file.

## lam (ldap account manager)

Open ldap account manager in browser: http://lam.localhost

## Jenkins

Open Jenkins in browser: http://jenkins.localhost

Paste password you get by this command in the console:
`docker exec -it developerenvironment_jenkins_1 cat /var/jenkins_home/secrets/initialAdminPassword && echo ''`

## Gitlab

Open Gitlab in browser: http://gitlab.localhost
