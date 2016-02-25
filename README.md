# dmulligan/docker-example-nginx-tomcat-mysql

A docker compose project with a MySQL, three Tomcat and an nginx container all linked together.

To run:

        $ docker-compose up

Containers:
- MySQL: on startup, the container executes a simple database initialisation script `./db/mysql-init.sql`, which
  creates a database containing a single table that is populated with a few records.
- Tomcat: three tomcat containers with a simple web application, located within `./tomcat/webapps`, deployed. The
  web application contains JSPs to test the database link between the Tomcat and the MySQL containers.
- nginx: inspects the three Tomcat containers and automatically creates a load balancer for the first two containers
  (as they are setup with the same `VIRTUAL_HOST` environment variable) and a reverse proxy for the third container.

