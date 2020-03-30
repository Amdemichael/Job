1.	Create Django project
Create an empty director named docker-django. Inside the folder create additional three folders, i.e. src, config, and compose. Src should contain the Django project. Config folder contains configuration for nginx (mydjango.conf). Compose folder containes Docker file for both Django and postgres. 
	Create a requirements.pip file inside src.  Requirements.pip file contains the required packages for Django application.
	Inside config folder create nginx folder. Inside nginx folder create mydjango.conf file. This file holds configuration for nginx.
	Inside compose folder create django and postgres folders. In both folders create Dockerfile file. Dockerflie files in both folders used for creation docker image django and postgres image.
	Project folder structure:

── docker-django
    ├── src
    │   ├── folders
    │   ├── manage.py
    │    ├── requirements.pip
    ├── config
    │   ├── nginx
    │      ├── mydjango.conf
    ├── compose
    │   ├── django
    │      ├── Dockerfile
    │    ├── postgres
    │      ├── Dockerfile
    │ 
    └── docker-compose.yml

2.	Add configuration to ‘docker-compose.yml’
Create a file named docker-compose.yml in docker-django (root directory). This file describes the services that makes our app. Here we need a web service (Django + uWGSI), a database (Postgres), and Proxy Server (Nginx). It also describes which Docker images these services will use, how will link together, any volumes they might need mounted inside the containers. The docker-compose.yml file describes which ports these service expose. 
There are three services for this project: nginx, web, db. Nginx depends on web, web depends on db, db container uses postgres’s latest image. Default username for db is postgress and password is postgres web container is build using project’s Dockerfile. It mounts src directory into it and exposes port 8000
3.	Create NGINX config
Write a nginx configuration config file named mydjango.config inside config/nginx folder. Nginx acts as a reverse proxy for any connections going to Django server all connection goes through nginx to reach Django server.
4.	Start and stop docker Compose
	Run :  docker-compose build in terminal with the project directory
	Run:   docker-compose up 
	Type localhost:8000 in browser to access the project.


