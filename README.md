# Declarative Jenkins Pipeline with Multi-Container Setup

This project demonstrates a Jenkins declarative pipeline that automates the setup of multiple Docker containers for a Node.js and Maven environment. The pipeline automates cloning a GitHub repository, starting multi-container services, and verifying installed versions of Node.js and Maven inside the containers.

## Features
- **Jenkins Declarative Pipeline**: Uses Jenkins for continuous integration
- **Multi-Container Setup**: Runs Node.js and Maven inside separate Docker containers
- **Automatically clones**: The repository and starts the necessary containers
- **Version Verification**: Confirms and Prints the installed versions of Node.js and Maven

## Technologies Used
- Jenkins
- Docker
- Docker Compose
- Node.js (v14.1.0)
- Maven (3.8.1)
- Git

## Prerequisites
- Docker and Docker Compose installed
- Jenkins configured and running
- GitHub repository containing the pipeline code

## Setup
### Clone the Repository
```sh
git clone https://github.com/hasan914/declarative_pipeline.git
cd declarative_pipeline
```

## Start Jenkins Container
Before running the pipeline, start the Jenkins container with the following command that run jenkins-Container 'jenkins_A4_B' from "my-jenkins:docker-dockerCompose-preInstalled" image which already have docker and docker-compose preInstalled:
```sh
docker run -d \
  --name jenkins_A4_B \
  --user root \
  -p 8080:8080 -p 50000:50000 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v jenkins_home:/var/jenkins_home \
  my-jenkins:docker-dockerCompose-preInstalled
```

## Run the Pipeline
1. Open Jenkins (`http://localhost:8080`).
2. Create a new pipeline project.
3. Use the `Jenkinsfile` from this repository.
4. Run the pipeline and observe the output.

## Verify the Running Containers
After a successful pipeline run, check the running containers using:
```sh
docker ps -a
```
Expected container names:
- `node_container`
- `maven_container`

## Check Installed Versions
The pipeline logs should display:
```sh
Node.js Version: v14.1.0 Hasan
Maven Version: Apache Maven 3.8.1 Hasan
```

## Project Structure
```
/
├── Jenkinsfile
├── docker-compose.yml
├── README.md
└── Instructions
└── Devops_A4_B.jpeg
```

## Contributions
Feel free to fork the repository, submit issues, or create pull requests to improve this project.

## License
This project is licensed under the MIT License.

## Author
Hasan Javed