# GitHub-Actions-Tutorial-Basic-Concepts-and-CICD-Pipeline-with-Docker

https://www.youtube.com/watch?v=R8_veQiYBjI&list=PLy7NrYWoggjzSIlwxeBbcgfAdYoxCIrM2&index=1&t=625s 

GitHub Actions 

What are GitHub Actions?
Developer workflow use cases
Basic Concepts: GitHub Events and Actions 
How GitHub Actions automates those workflows?
CI/CD pipeline with GitHub Actions 
Benefits of GitHub Actions CI/CD
Demo
Syntax

Java App  with Grandle    ->   Docker Image   ->  Private Repository 
Build Artifact                            Build Image            Push Docker repo

What are GitHub Actions?
Platform to automate developer workflows
CI/CD Workflow 

What are those workflows ?
Github 
Platform for open-source projects
Publically available to use and contribute to the project 
Add new contributors
Pull requests are created 

Issues
Pull Requests
Merge to master branch 

CI/CD Pipeline 
Merged Code / Test / Build / Deployment 

How GitHub Actions automate these workflows ?
When somethings happens In or To your repository 
Automatic ACTIONS are executed in response 

Listen to Events 
PR Created / Contr. joined / Other apps / Issue created / PR merged 

Trigger Workflow 
Issue created

            Sort             - Action
Label            - Action
Assign It       - Action 
Reproduce   - Action 

CI/CD with GitHub Actions 
Most common workflow for your repository 
Commit code / Test / Build / Push / Deploy 

Pipeline / Node.js App / Build Docker Image / push to Nexus Repo / Deploy to DigitalOcean Server 

Pipeline / Java App with Maven / Integrations Tests Linux and Windows / Build Docker Image / push to AWS Repo / deploy to AWS EKS 

CI/CD Demo
Java App with Grandle / Build Docker Image / push to Private Repo

Github UI
Github Repository 
https://github.com/nanuchi/my-project 

Github Actions 
Categories 
Continuous Integration 
Java with Gradle

Visual Studio Code
Explorer
Open Editors 
ci.yml 

ci.yml
# This workflow will build a Java project with Gradle
# For more information see: https://help.github.com/actions/language-and-framework-guides/building-and-testing-java-with-gradle

name: Java CI with Gradle

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build-java:

    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v2

    - name: Set up JDK 1.8
      uses: actions/setup-java@v1
      with:
        java-version: 1.8

    - name: Grant execute permission for gradlew
      run: chmod +x gradlew

    - name: Build with Gradle
      run: ./gradlew build

    - name: Build and Push Docker Image
      uses: mr-smithers-excellent/docker-build-push@v4
      with:
        image: nanajanashia/demo-app
        registry: docker.io
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

https://github.com/marketplace/actions/build-and-push-docker-images 
https://github.com/marketplace?type=actions 
         
Github Repository 
https://github.com/nanuchi/my-project 
Settings 
Secrets
Secrets / New secret 
Name
DOCKER_USERNAME
Docker Hub
Docker commands
	Value
nanajanashia
Add secret

Secrets / New secret 
Name
DOCKER_PASSWORD
Docker Hub
Docker commands
	Value
nanajanashia
Add secret

Commit changes …

Commit new file
Create a new branch
new-ci-workflow
Propose new file
Open a pull request
Create a pull request
Java CI with Grandle / build (pull request)
This branch has no conflicts with the base branch
Details 
build
Set up job 
Run actions/checkout@v2
Set up JDK 1.8
Build with Grandle
Post Run actions/checkout/v2

Build Docker Image and push to private repository 
Java app with Gradle / Build Docker Image / push to private repository 

Github Repository 
https://github.com/nanuchi/my-project 

Actions
Update ci.yml
build-java
Build with Gradle
Build and Push Docker Image

Docker Hub
Tags
master-b109fe9







