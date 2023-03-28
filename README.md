# VueJswithDocker
To set up a Vue.js application and deploy it using Docker
Here are the steps I followed to set up a Vue.js application and deploy it using Docker:

1.	First, I created a Vue.js app inside the src folder, as shown in my Github repository.


2.	Next, I created four files: docker-compose.yml, Dockerfile, Dockerfile-build-app, and Dockerfile-create-app.



3.	In the docker-compose.yml file, I created an app service with the following content:
	![image](https://user-images.githubusercontent.com/99163931/228205987-a8f3a64a-f8a6-4762-8d63-f423f49f2dfb.png)



4.	In the Dockerfile, I specified the base image as node:lts-alpine and set the working directory as /app. I copied the package.json file to the working directory, installed the app dependencies, exposed port 8080, and set the command to run the npm run serve script.

![image](https://user-images.githubusercontent.com/99163931/228206095-5e925178-c9e6-4c01-b36e-e019d9fec910.png)


 

5.	In the Dockerfile-build-app, I first specified a base image as node:lts-alpine and set the working directory as /app. I then copied the package.json file and installed the app dependencies. Next, I added the app by copying everything in the current directory to the /app directory. Finally, I generated the build by running the npm run build command.

![image](https://user-images.githubusercontent.com/99163931/228206121-dec492f5-0d6a-4c9d-87ea-c52b1c4b647d.png)

 

6.	In the Dockerfile-create-app, I specified the base image as node:lts-alpine and set the working directory as /app. I installed the Vue CLI and created a new Vue.js project using the vue create command. Finally, I changed the ownership of all files in the current directory to the current user using sudo chown -R $USER:$(id -gn $USER) ./*.

![image](https://user-images.githubusercontent.com/99163931/228206141-77d86593-06ba-4071-a848-2aef84a1e2d0.png)

 

7.	Finally, I ran the commands in the comments at the end of each file to build and run the Docker containers. For example, to build the production Docker image, I ran the following command:
docker build -t vue-prod -f Dockerfile-build-app .

 
	![image](https://user-images.githubusercontent.com/99163931/228206170-46e9381c-28b3-4c81-a7b4-031077572375.png)



