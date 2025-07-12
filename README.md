
This is a web-based Tic Tac Toe Game 🎮 using Node.js & Express

This is a lightweight two-player Tic Tac Toe game built using Node.js and Express, designed to run in the browser. The entire UI and game logic are contained in a single HTML file, served via an Express server.

The project is fully containerized using Docker and integrated with Jenkins for automated CI/CD pipelines using a Jenkinsfile.


📁 Project Structure

nodejs-tic-tac-toe/
├── public/
│   └── index.html       # Game UI + script
├── server.js            # Express server
├── package.json         # App metadata and dependencies
├── Dockerfile           # Docker build instructions
├── Jenkinsfile          # Jenkins pipeline definition
└── README.md            # Project documentation


🚀 Features

    Simple 3x3 Tic Tac Toe gameplay in the browser

    Two-player support on the same device

    Win/draw detection

    Lightweight setup using Express

    CI/CD ready with Docker and Jenkins integration


🔧 Prerequisites
    Before running or building this project, ensure the following are installed:

    Node.js (only if running without Docker)

    npm (comes with Node.js)

    Docker

    Jenkins (for pipeline execution)

    sudo usermod -aG docker jenkins  #This will add jenkins user to docker group

    ✅ If deploying to a cloud server, make sure port 3000 is open to public access.


🧪 Local Development (Without Docker)

    Optional — only for testing locally without containerization.

    # 1. Install dependencies
	npm install

    # 2. Run the server
	node server.js

    # 3. Access the app
	Visit: http://localhost:3000


🐳 Running with Docker(For testing locally without Jenkins)

    1. Build the Docker Image
	docker build -t tic-tac-toe . 	#Builds the docker image with name tic-tac-toe

    2. Run the Container
    	docker run -d -p 3000:3000 tic-tac-toe 	#Expose the container's port 3000 to the host’s port 3000

    3. Access the app at:
 	http://localhost:3000 (local machine)
    	or
    	http://<your-public-ip>:3000 (if on a cloud server)


⚙️ Jenkins Pipeline (CI/CD)

    This project includes a Jenkinsfile to automate the build and deployment process via Jenkins.
    ✅ What the Pipeline Does

    Pulls the latest code from the repository
 
    Builds the Docker image for the Node.js app

    Runs the container exposing port 3000


💡 Jenkins Job Setup

    Create a Pipeline job in Jenkins

    Point the job to this repository

    Jenkins will automatically detect and use the Jenkinsfile

    Ensure the Jenkins agent has:

       - Docker installed
       - Permission to run Docker (e.g., jenkins in docker group) #sudo usermod -aG docker jenkins


🌐 Accessing the Game

    Once running, open your browser and visit:

    http://localhost:3000 (local environment)

    http://<your-public-ip>:3000 (cloud environment or server)


🖱️ How to Play

    The game runs directly in the browser

    Two players alternate turns by clicking on the board

    Player X always starts

    Game will display the results

