# nodejs-demo-app
DAY-1
🧱 Step-by-Step Breakdown
1. Initialize Node.js App

Commands:

    npm init -y

    npm install express

Explanation:
Initializes a basic Node.js project.
Installs express to create a minimal web server for testing CI/CD.

2. Create Dockerfile

Command:
    No command — just create a file named Dockerfile in the root directory.

Explanation:
Defines how the app should be containerized (base image, dependencies, ports, and startup command).

3. Test Docker Image Locally (Optional but Recommended)

Commands:

    docker build -t node-ci-cd-app .

    docker run -p 3000:3000 node-ci-cd-app

Explanation:

Builds a Docker image named node-ci-cd-app.
Runs the container locally and maps it to your machine’s port 3000.

4. Create GitHub Repository & Push Code

Commands:

    git init
    git remote add origin https://github.com/your-username/your-repo.git
    git add .
    git commit -m "Initial commit"
    git branch -M main
    git push -u origin main

Explanation:
Pushes your local Node.js + Docker project to a GitHub repo, where you’ll later trigger workflows.

5. Set Up GitHub Actions Workflow

Steps:

    Create .github/workflows/main.yml in your repo.

    Define CI/CD steps in this file (test, build, push).

Explanation:
This YAML file is the core of your automation. GitHub Actions uses it to know what to do and when (on push to main).
6. Create DockerHub Access Token & Add GitHub Secrets

Steps:

Go to DockerHub → Account Settings → Security → Create Access Token.
Go to your GitHub repo → Settings → Secrets and Variables → Actions → Add the following secrets:

        DOCKERHUB_USERNAME

        DOCKERHUB_TOKEN

Explanation:
Allows GitHub Actions to securely authenticate with DockerHub and push your image.

7. Push Code to Trigger CI/CD

Command:

    git add .
    git commit -m "Trigger CI/CD"
    git push

Explanation:
Every push to main triggers the GitHub Actions workflow:

Installs dependencies
(Optionally) runs tests
Builds Docker image
Pushes image to DockerHub

8. Verify the Docker Image in DockerHub

Steps:

Go to your DockerHub account.
Look for the new image under your repository (e.g., your-username/node-ci-cd-app).

Explanation:
Confirms the automated deployment pipeline works from GitHub → DockerHub.
