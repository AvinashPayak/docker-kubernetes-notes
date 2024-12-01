# Use an existing docker image as a base
FROM node:14-alpine
# Set the working directory inside the container
WORKDIR /app
# Copy package.json
COPY ./package.json .
# Download and install a dependency
RUN npm install
# Copy your project files to the container
COPY . .
# Tell the image what to do when it starts as a container
CMD ["npm", "start"]

# docker run -p 8080/8080 avinashpayak/node 