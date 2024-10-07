# Connect DB with IntelliJ and PostgreSQL

## Docker

Check the Docker Compose File (docker-compose.yml)
If you're using Docker Compose, the database name is often defined in the docker-compose.yml file. 
Look for the PostgreSQL service definition, which might look something like this:
```yaml
services:
  postgres:
    image: postgres:latest
    environment:
      POSTGRES_DB: mydatabase
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
    ports:
      - "5432:5432"
```
Or:
```yaml
   db:
     image: mdillon/postgis
     environment:
       - POSTGRES_USER=postgres
       - POSTGRES_DB=postgres
     ports:
       - 5433:5432
```
> [mdillon/postgis](https://hub.docker.com/r/mdillon/postgis/)
> mdillon is a popular image for Docker to have PSQL access.

In the second case, we can add the datasource URL with IntelliJ as:
`jdbc:postgresql://localhost:5433/postgres`

**Notice that the port is 5433 not the default 5432! That's because it was changed in the compose.yml file.**

