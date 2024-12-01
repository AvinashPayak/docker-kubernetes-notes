## Images

### Process of creating a custom image
- Build a Dockerfile - config to define how the container behaves
- Send it to Docker Client
- Sends it to Docker Server which builds a usable image

### Flow for creating a Dockerfile

- Specify a base image
- run commands to install additional dependencies
- specify command to run on container setup

### Example project - Create an image which runs redis-server

- Create a `redis-image` folder
- Create a `Dockerfile` file inside it
- add following code in it:
```
FROM alpine
RUN apk add --update redis
CMD ["redis-server"]
```
- open terminal inside `redis-image` folder
- run command `docker build .`
- run command `docker run [container-id]`

### How Dockerfile works
- `FROM | RUN | CMD` etc instructions tell docker what to do
- command ahead of these instructions are the arguments
- base image needs to be specified in an empty image to provide a set of programs or starting point 
- alpine is used as a personal preference
- `apk` is a package manager which comes installed with alpine which can be used to install dependencies
- `apk add --update redis` made use of apk to install redis

### Build process of Dockerfile
- Step[1/3] checked if `alpine` image is already downloaded or not
- Step[2/3] to run `apk add --update redis` alpine needs to be executed. For that to happen a temporary alpine container was created and was run. Then redis installation command was executed inside the container.
- snapshot of all the filesystem and code execution that happened inside temporary container is now saved as another image and the temporary container is removed.
- Step[3/3] image created in previous step is run and a new temporary container is created and executed
- Then `CMD` sets the primary command of the container. It doesnt execute `redis-server` command but it sets that command as the primary process of the container whenever the container is run. 
- snapshot of this execution is created and new image is generated which is the final image for our Dockerfile
- temporary container is deleted

### Docker rebuilds with cache
- if we are rebuilding an image and if any of its steps remain unchanged from its previous execution then docker makes use of cache to retrieve data from previous execution instead of fetching again
