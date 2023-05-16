Docker.
-

## How to download image?

1. Open a Git Bash terminal.
2. Use `docker run hello-world` to install the `hello world` image.
3. Use `docker images` to see all the images that are installed.

## How to run an image?

1. Use `docker run -d -p 80:80 nginx` to install nginx image.

- d is to make sure that we wont be locked in a terminal
- p is the port


2. Go to a browser and enter `http://localhost` to see the nginx page.

3. Commands that we can use on images:

- `docker ps` to show all the containers running
- `docker stop <name or ID of the image>` to stop the image
- `docker start <name or ID of the image>` to start the image
- `docker rm <name or ID of the image>` to terminate the image
- `alias docker="winpty docker` to create an alias for docker

### How to change Nginx HTML

1. Firstly use `docker ps` to find the container ID for Nginx
2. Create an alias for docker using `alias docker="winpty docker"`
3. Run `docker exec -it <container ID> sh` to go to container location
4. We can now use linux commands to navigate to the nginx location

Run this command to navigate to folder: 

`cd /usr/share/nginx/html`

5. You can use `pwd` to make sure you are in the correct location after command.
6. Now we need to run update: `apt update -y`
7. Then use `apt install sudo` to install sudo.
8. Run `sudo apt install nano` to install nano
9. Then use `sudo nano index.html` to go into the html file
10. We can then change what the nginx page shows. Under the header we can change it to `Welcome to the dream team of DevOps!`.
11. Then when we go to our browser and run `http://localhost` we will see the change.


![welcome.png](file%2Fwelcome.png)

### Adding our Sparta profile and pushing to DockerHub.

1. Create a index.html file by using: `nano index.html`
2. Now we need to entered the code that we want to be shown:

```commandline
<!DOCTYPE html>
<html>
<head>
<title>Matty's profile</title>
</head>
<body>
<h1>Welcome to Matty's profile v2.1, This website is hosted inside a container using docker to build a Micro-Service</h1>
</body>
</html>
```
3. From the same directory we need to docker copy this file into our nginx image `docker cp index.html <docker_image_id>:usr/share/nginx/html`
4. Now we need to commit those changes to the image with `docker commit <image_ID> <image_name>`
5. Then we then need to tag this image before we can push this with: `docker tag <image_name> <docker_hub_username>/<repository_name>:<tag>`
6. We need to make sure that we have new repo created on DockerHub
7. Now we can push to repo with: `docker push <docker_hub_username>/<repository_name>:<tag>`

### Automating creation of the image

1. First change directory location to where the `index.html` file is
2. Create new Docker file: `nano Dockerfile`
3. Within this we need to add the relevant info:

```commandline
# base image Nginx
# base image (parent) Nginx
FROM nginx

# who is the owner/creator
LABEL MAINTAINER=MATEUSZ@SPARTA

# copy index.html to /usr/share/nginx/html
COPY index.html /usr/share/nginx/html

# port 80
EXPOSE 80

# execute command run
CMD ["nginx", "-g", "daemon off;"]

# docker build
# docker images to confirm the name
# docker run image name
# docker ps as well as localhost:80

```
4. Create the image: `docker build -t <repo_name>/<image_name>:tag .`
5. We can verify on localhost with: `docker run -d -p 90:80  <repo_name>/<image_name>:tag`

Navigate to the localhost and should see ammended web page.

6. We can push this image to Docker hub: `docker push  <repo_name>/<image_name>:tag`

## Automating creation of the image for Node app:

1. First navigate to the directory where our app folder is and create a Dockerfile: `nano Dockerfile`
2. Paste this code:
```commandline
# base image Node
FROM node:16

# Create app directory
WORKDIR /app

# Who is the owner
LABEL MAINTAINER=MATEUSZ@SPARTA

# Copy app to work dir
COPY app/ .

# use port 3000
EXPOSE 3000

# install npm
RUN npm install

# excecute commands
CMD ["npm", "start", "daemon off;"]
```
3. We can now build the image: `docker build -t marix1993/sparta_app:v1 .`
4. We can verify this locally with: `docker run -d -p 3000:3000 marix1993/sparta_app:v1`

![app_web.png](file%2Fapp_web.png)

5. Once we can see it running locally we can push this image to docker hub with: `docker push marix1993/sparta_app:v1`

![docker_hub.png](file%2Fdocker_hub.png)