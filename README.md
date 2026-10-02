# Task 2 - Jenkins CI/CD Pipeline

## Objective

Create a simple Jenkins pipeline to automate building,
testing and deploying an application.

## Tools Used

- Jenkins
- Docker
- GitHub
- Node.js

## Pipeline Stages

1. Checkout
2. Build
3. Test
4. Deploy

## Architecture

GitHub
   |
   v
Jenkins
   |
   +---- Build
   |
   +---- Test
   |
   +---- Deploy
   |
   v
Docker Container
   |
   v
Node.js Application

## How It Works

Whenever code is pushed to the GitHub repository,
Jenkins retrieves the source code and executes the
Jenkinsfile.

The pipeline builds a Docker image, tests the
application and deploys it as a Docker container.

## Result

Application is deployed using Jenkins and Docker.
