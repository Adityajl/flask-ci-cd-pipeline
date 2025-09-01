## Flask CI/CD Pipeline with Jenkins and Docker
This repository contains a simple Flask web application integrated with a robust Continuous Integration/Continuous Deployment (CI/CD) pipeline using Jenkins and Docker. The project is designed to demonstrate how to automate the build, test, and deployment process, ensuring that every code change is validated before being released.

### Features
Continuous Integration: Automated builds and tests are triggered on every code push to the main branch.

Containerization: The application is containerized using Docker, providing a consistent and isolated environment for development and deployment.

Automated Testing: The pipeline includes a dedicated stage for running unit tests to ensure code quality.

Staging & Production Deployment: The pipeline is configured to deploy the application to a staging environment for review and requires manual approval before deploying to production.

Infrastructure as Code (IaC): The entire pipeline is defined in a Jenkinsfile, which is version-controlled alongside the application code.

### Getting Started
To run this pipeline locally, you will need to have Docker and Docker Compose installed on your machine.

1. Clone the Repository
git clone [https://github.com/Adityajl/flask-ci-cd-pipeline.git](https://github.com/Adityajl/flask-ci-cd-pipeline.git)
cd flask-ci-cd-pipeline


2. Set up the Jenkins Environment
The project includes a docker-compose.yml file to quickly set up a Jenkins instance with the necessary configurations. This setup mounts the host's Docker socket, allowing Jenkins to build and run containers.

docker-compose up -d


Once the containers are up, Jenkins will be available at http://localhost:8080.

3. Configure the Jenkins Pipeline
Open Jenkins in your browser and log in.

Create a new Pipeline job and configure it to use Pipeline script from SCM.

Set the SCM to Git and enter the repository URL: https://github.com/Adityajl/flask-ci-cd-pipeline.git.

Specify the branch to build from (e.g., master).

Save the job.

4. Run the Pipeline
After configuring the job, trigger a build. The pipeline will automatically execute the stages defined in the Jenkinsfile:

Build & Test: Builds the application and runs unit tests inside a Python Docker container.

Build Docker Image: Creates a Docker image of the application and pushes it to your Docker Hub repository.

Deploy to Staging: Deploys the container to a mock staging environment.

Manual Approval: Halts the pipeline to wait for manual approval before proceeding.

Deploy to Production: Deploys the container to a mock production environment.

Repository Structure
.
├── .github/workflows/           # Optional:

