About this project

A minimal Node.js + Express application containerized with Docker and deployed automatically using GitHub Actions CI/CD.

This project demonstrates a production-oriented DevOps pipeline: build, publish, and deploy a containerized application via a self-hosted GitHub Actions runner. The setup highlights reproducibility, container lifecycle management, and automated delivery on a Dockerized environment.

Built with

Node.js
Express
Terraform
GH actions

Prerequisites\installation

Setup self hosted runner

Project Workflow

The project workflow is started by a new commit being pushed to the CICD-GH repo main branch.

CI.yml then uses the push workflow trigger to authenticate to docker hub using credentials stored in GH secrets (DOCKER_USERNAME, DOCKER_PASSWORD). Then a docker image is built of the application and pushed to docker hub so it can be accessed remotely.

CD.yml uses the workflow_run workflow trigger after CI.yml is complete. CD.yml pulls the latest docker image from docker hub, removes existing containers (if they exist) and runs a new container on port 8080 using the up to date docker image.


