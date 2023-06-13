# Getting Started - Docker Compose

### Prerequisites <br>
You need to have Docker Engine and Docker Compose on your machine. You can either: <br>

- Install Docker Engine and Docker Compose as standalone binaries 
- Install Docker Desktop which includes both Docker Engine and Docker Compose 

You don’t need to install Python or Redis, as both are provided by Docker images.<br>

### Step 1: Define the application dependencies<br>

1. Create a directory for the project:

<div align="center"><img src="gambar/Screenshot(1).jpg"></div><br>

2. Create a file called app.py in your project directory <br>

3. Create another file called requirements.txt in your project directory<br>

### Step 2: Create a Dockerfile<br>

1. In your project directory, create a file named Dockerfile<br>

### Step 3: Define services in a Compose file<br>

1. Create a file called docker-compose.yml in your project directory<br>

2. Finally, the files in your project directory will be like this. <br>


### Step 4: Build and run your app with Compose<br>

1. From your project directory, start up your application by running docker compose up.<br>

<div align="center"><img src="gambar/Screenshot(3).jpg"></div><br>
<div align="center"><img src="gambar/Screenshot(4).jpg"></div><br>

2. Enter http://localhost:8000/ in a browser to see the application running.<br>

<div align="center"><img src="gambar/Screenshot(5).jpg"></div><br>

3. Refresh the page. The number should increment.<br>

<div align="center"><img src="gambar/Screenshot(6).jpg"></div><br>

4. Switch to another terminal window, and type docker image ls to list local images.<br>

<div align="center"><img src="gambar/Screenshot(7).jpg"></div><br>

5. Stop the application, either by running docker compose down from within your project directory in the second terminal, or by hitting CTRL+C in the original terminal where you started the app. <br>


### Step 5: Edit the Compose file to add a bind mount<br>

1. Edit docker-compose.yml in your project directory to add a bind mount for the web service<br>

### Step 6: Re-build and run the app with Compose <br>

1. From your project directory, type docker compose up to build the app with the updated Compose file, and run it. <br>


2. Check the Hello World message in a web browser again, and refresh to see the count increment.<br>

<div align="center"><img src="gambar/Screenshot(10).jpg"></div>

### Step 7: Update the application <br>

1. Because the application code is now mounted into the container using a volume, you can make changes to its code and see the changes instantly, without having to rebuild the image. Change the greeting in app.py and save it. For example, change the Hello World! message to Hello from Docker!.<br>

<div align="center"><img src="gambar/Screenshot(11).jpg"></div><br>

### Step 8: Experiment with some other commands

1. If you want to run your services in the background, you can pass the -d flag (for “detached” mode) to docker compose up and use docker compose ps to see what is currently running. <br>

<div align="center"><img src="gambar/Screenshot(12).jpg"></div><br>

2. The docker compose run command allows you to run one-off commands for your services. For example, to see what environment variables are available to the web service. <br>

<div align="center"><img src="gambar/Screenshot(13).jpg"></div><br>

3. If you started Compose with docker compose up -d, stop your services once you’ve finished with them. <br>

<div align="center"><img src="gambar/Screenshot(14).jpg"></div><br>

4. You can bring everything down, removing the containers entirely, with the down command. Pass --volumes to also remove the data volume used by the Redis container. <br>

<div align="center"><img src="gambar/Screenshot(16).jpg"></div>


