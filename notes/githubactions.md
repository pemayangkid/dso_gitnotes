# GitHub Actions 

## Overview
GitHub Actions is an automation platform built directly into GitHub. It allows developers to define automated workflows using YAML configuration files stored inside the repository. These workflows are triggered by events such as pushing code, opening a pull request, or creating a release.

The key advantage of GitHub Actions is that it requires no external CI server. Since it is part of GitHub itself, the setup is minimal and the integration with the repository is seamless. GitHub provides free compute time (called runners) to execute the workflows.

## Key Concepts
Workflow:	An automated process defined in a .yml file inside .github/workflows/
Trigger (on:):	The event that starts the workflow, such as a push to the main branch
Job:	A group of steps that run together on the same machine
Step:	A single command or pre-built action within a job
Runner:	The virtual machine that executes the job (e.g., ubuntu-latest)
Action:	A reusable unit of code, such as actions/checkout or actions/setup-node
Secret:	Encrypted environment variables stored in GitHub settings (e.g., API keys)

## Workflow File Structure
A GitHub Actions workflow is written in YAML format and stored at .github/workflows/main.yml inside the repository. Below is a sample workflow that I studied and understood:

------
name: Build and Deploy

on:
  push:
    branches: ["main"]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Login to DockerHub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      - name: Build and Push Docker Image
        run: |
          docker build -t ${{ secrets.DOCKERHUB_USERNAME }}/todo-app:latest .
          docker push ${{ secrets.DOCKERHUB_USERNAME }}/todo-app:latest

      - name: Trigger Render Deployment
        run: |
          curl -X POST ${{ secrets.RENDER_DEPLOY_HOOK_URL }}
-----

## How to Set Up GitHub Actions
The following steps describe how to set up using GitHub Actions:

1.	Create a folder in your repository called .github/workflows/
2.	Inside that folder, create a file named main.yml (or any name ending in .yml)
3.	Write your workflow configuration specifying the trigger, jobs, and steps
4.	Push the file to your GitHub repository
5.	Navigate to the Actions tab in your GitHub repository to see the workflow running
6.	Review the logs of each step to confirm that tests pass and the build succeeds

# Conclusion
In this self-study, I learned the basics of GitHub Actions and how it is used to automate workflows in a GitHub repository. I understood how a workflow is created using YAML files and how it runs automatically based on events like code pushes. I also learned about key components such as jobs, steps, runners, and secrets. Overall, this helped me understand how GitHub Actions simplifies CI/CD and automates development tasks efficiently.