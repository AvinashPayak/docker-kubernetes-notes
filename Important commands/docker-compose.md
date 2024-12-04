
### Docker compose commands
- `docker run myimage` - `docker-compose up`
- `docker build .` + `docker run myimage` = `docker-compose up --build`
- `docker-compose up` to start all containers in yml together
- `docker-compose down` to shut down all containers in yml together
- `docker-compose up -d` to run all containers in detached mode so the same terminal can be used for other purpose
- `docker-compose ps` to view all the containers running of docker-compose.yml

### Restart policies
- `no` - never restart container if it stops or crashes
- `always` - restart it always if it stops for any reason
- `on-failure` - restart only if it stops with an error code
- `unless-stopped` - always restart unless we developers stop it
