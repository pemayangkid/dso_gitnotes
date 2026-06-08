# Render

## Overview
Render is a modern cloud hosting platform that makes it easy to deploy web applications, APIs, static sites, and databases. It connects directly to a GitHub repository and automatically redeploys the application whenever new code is pushed to a specified branch. This makes Render a natural partner for GitHub Actions in a CI/CD pipeline.

Render supports a wide variety of application types including Node.js, Python, Ruby, Go, static HTML/CSS/JS sites, and Docker containers. It provides free-tier hosting suitable for learning and small projects, and paid tiers for production applications.

## Key Features of Render
Automatic deployments triggered by pushes to a connected GitHub branch
Free SSL certificates (HTTPS) provided automatically for every deployment
Custom domain support so you can connect your own domain name
Environment variables management through the Render dashboard
Built-in logging and monitoring for debugging deployed applications
Support for databases such as PostgreSQL with managed backups
Zero-downtime deployments so users are not interrupted when new code is released

## How to Deploy on Render
The following steps describe how to set up a deployment on Render:

7.	Create an account at render.com and sign in
8.	Click New and select Web Service from the dashboard
9.	Connect your GitHub account and select the repository to deploy
10.	Configure the service: choose the branch (e.g., main), set the Build Command and Start Command
11.	Add any required environment variables (e.g., DATABASE_URL, PORT, API keys)
12.	Click Create Web Service and Render will start the first deployment
13.	Once deployed, Render provides a live URL such as https://your-app.onrender.com
14.	Every subsequent push to the connected branch automatically triggers a new deployment

# Conclusion
In this self-study, I learned about Render and how it is used as a cloud hosting platform for deploying web applications and APIs. I understood how Render connects with GitHub to automatically deploy projects whenever code is pushed to a repository. I also learned about its key features like automatic deployments, SSL certificates, environment variables, and support for different types of applications. Overall, this helped me understand how Render simplifies deployment and works effectively in a CI/CD workflow.
