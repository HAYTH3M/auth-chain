# Simple auth-chain environement.
## An authentification chain using :
- traefik 
- traefik-forward-auth
- keycloak 
- whoami1

## 1- Prerequisites
  ```
  Docker version	 >= 19.03.9-3
  Docker-compose version >= 1.27.4
  ```

## 2- Components
  ##### There is 4 components in this environement:
  #
    a- traefik                   ==> A Strong reverse proxy, with alot of capabilities, like altering request, load balancing, etc..
    b- traefik-forward-auth      ==> An Oauth2/OIDC compatible reverse proxy (You can use anything else)
    c- keycloak                  ==> An open source technology that allows single sign-on with Identity and Access Management aimed at modern applications and services. 
    d- keycloak-db               ==> A simple postgresql database; you can use mysql or any SQL database if you want to.
    e- whoami1                   ==> An unsecure application that we aim to secure using this environement.
    
## 4- Port mapping
  ##### Make sure that these ports are available, before running the docker-compose or any container:
  #
    a- traefik              ==> 80/tcp, 443/tcp, 9000/tcp
    b- keycloak             ==> 8080/tcp, 8443/tcp
    c- keycloak-db          ==> 5432/tcp 
    d- whoami1              ==> 4000/tcp    

## 5- Usage
  ##### To use this environement, you need to :
  ```
  a- Clone the repo : git clone https://github.com/HAYTH3M/auth-chain.git
  b- Create the docker networks : docker network create auth-stack && docker network create appl-stack
  d- Bring the whole env up : docker-compose down && docker-compose up -d
  f- Create a realm under : http://YOUR-VM-IP:8080/auth/admin/master/console/#/realms/master 
  e- Create a client under : http://YOUR-VM-IP:8080/auth/admin/YOUR-CREATED-REALM/console/#/realms/YOUR-CREATED-REALM/clients
     You can follow this guide for realm and client setup : https://github.com/ibuetler/docker-keycloak-traefik-workshop
  g- Use the params in the docker-compose under the traefik-forward-auth config and restart the traefik-forward-auth container.
  ```
