# Use an existing docker image as a base
FROM node:14-alpine
# Set the working directory inside the container
WORKDIR /app
# Copy your project files to the container
COPY . .
# Download and install a dependency
RUN npm install
# Tell the image what to do when it starts as a container
CMD ["npm", "start"]

# docker run -p 8080/8080 avinashpayak/node 