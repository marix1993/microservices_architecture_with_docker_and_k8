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

## Pushing a Container Image and any changes, to your Docker Hub repo
1. Run the command `docker commit <container_id> <your_new_image_name>`

2. Run `docker tag <your_new_image_name> <dockerhub_username>/<repository_name>:<newtag>`

3. Run docker `login` and log in to your docker hub

4. Run `docker push <dockerhub_username>/<repository_name>:<tag>`
5. To save and push any changes after completing this, run `docker commit <container id>` and then `docker push <dockerhub_username>/<repository_name>:<tagname>`

Your changes will now be pushed to your Docker Hub repo

**To download and run an image on port 90, use `docker run -d -p 90:80 <username>/<repo>:<tagname>`**






