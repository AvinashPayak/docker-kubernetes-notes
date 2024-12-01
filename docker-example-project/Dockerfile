# Use an existing docker image as a base
FROM alpine
# Download and install a dependency
RUN apk add --update nodejs npm
# Tell the image what to do when it starts as a container
CMD ["npm install"]