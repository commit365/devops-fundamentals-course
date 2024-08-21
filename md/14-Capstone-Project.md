# Lesson 14: Capstone Project

## Overview

In this lesson, we will focus on applying the concepts learned throughout the course to a real-world project. The capstone project will encompass the entire software development lifecycle, including planning, execution, deployment, and post-deployment monitoring. We will also cover how to present and review the project with peers, receive constructive feedback, and iterate based on insights.

## Project Overview

The goal of the capstone project is to develop a simple web application using the principles of DevOps that you have learned. This project will allow you to demonstrate your understanding of CI/CD, containerization, orchestration, monitoring, and collaboration tools.

### Project Idea

For this capstone project, you will create a **Task Management Application** that allows users to create, read, update, and delete tasks. The application will be built using a web framework of your choice (e.g., Node.js, Python Flask, or Ruby on Rails) and will utilize a database (e.g., MongoDB, PostgreSQL) to store task data.

## Project Phases

### 1. Planning

- **Define Requirements**: Outline the features you want to implement in the application. For example:
  - User authentication (login and registration)
  - CRUD operations for tasks
  - Task categorization and prioritization
  - User interface for task management

- **Choose Technology Stack**: Select the technologies and tools you will use for the project, including:
  - Programming language and web framework
  - Database management system
  - CI/CD tools (e.g., GitHub Actions, Jenkins)
  - Containerization (e.g., Docker)
  - Orchestration (e.g., Kubernetes)

- **Create a Project Timeline**: Develop a timeline for the project, breaking it down into manageable tasks and milestones.

### 2. Execution

- **Set Up Version Control**: Create a Git repository for your project and initialize it.
  ```bash
  git init task-management-app
  cd task-management-app
  ```

- **Develop the Application**: Implement the features outlined in the planning phase. Follow best practices for coding, including writing unit tests and documentation.

- **Containerize the Application**: Create a Dockerfile to package your application and its dependencies. For example:
  ```dockerfile
  # Use an official Node.js runtime as a parent image
  FROM node:14

  # Set the working directory
  WORKDIR /usr/src/app

  # Copy package.json and install dependencies
  COPY package*.json ./
  RUN npm install

  # Copy the rest of the application code
  COPY . .

  # Expose the application port
  EXPOSE 3000

  # Command to run the application
  CMD ["npm", "start"]
  ```

- **Create CI/CD Pipeline**: Set up a CI/CD pipeline using your chosen tool (e.g., GitHub Actions) to automate testing and deployment processes. For example, a simple GitHub Actions workflow (`.github/workflows/ci.yml`) might look like this:
  ```yaml
  name: CI/CD Pipeline

  on:
    push:
      branches:
        - main

  jobs:
    build:
      runs-on: ubuntu-latest

      steps:
        - name: Checkout code
          uses: actions/checkout@v2

        - name: Set up Node.js
          uses: actions/setup-node@v2
          with:
            node-version: '14'

        - name: Install dependencies
          run: npm install

        - name: Run tests
          run: npm test

        - name: Build Docker image
          run: |
            docker build -t my-task-app .
            docker run -p 3000:3000 my-task-app
  ```

### 3. Deployment

- **Deploy the Application**: Choose a cloud provider (e.g., AWS, Azure, Google Cloud) to deploy your application. Use Kubernetes or Docker Compose to manage your containers.

- **Post-Deployment Monitoring**: Set up monitoring tools (e.g., Prometheus, Grafana) to track the performance and health of your application after deployment. Implement logging using the ELK stack or similar tools.

### 4. Presenting the Project

- **Prepare a Presentation**: Create a presentation that outlines your project, including:
  - Project goals and requirements
  - Technology stack and architecture
  - Key features and functionalities
  - CI/CD pipeline setup
  - Monitoring and logging strategies

- **Demo the Application**: Provide a live demonstration of the application, showcasing its features and functionality.

- **Gather Feedback**: After your presentation, invite peers to provide constructive feedback. Ask specific questions to guide the discussion, such as:
  - What did you find most valuable about the project?
  - Are there any areas for improvement or additional features you would suggest?
  - How well do you think the CI/CD pipeline was implemented?

### 5. Iterating Based on Insights

- **Review Feedback**: Analyze the feedback received during the presentation and identify actionable items for improvement.

- **Implement Changes**: Make necessary changes to the application based on the feedback. This could include refining features, improving documentation, or enhancing the CI/CD pipeline.

- **Reflect on the Project**: Take time to reflect on your experience throughout the project. Consider what went well, what challenges you faced, and how you can apply these lessons to future projects.

## Conclusion

In this lesson, we focused on applying the concepts learned throughout the course to a real-world capstone project. We covered the phases of planning, execution, deployment, and post-deployment monitoring, as well as the importance of presenting and reviewing the project with peers. This capstone project serves as a culmination of your learning, allowing you to demonstrate your understanding of DevOps principles and practices in a practical setting. In the next lesson, we will summarize the key takeaways from the course and discuss potential next steps for your DevOps journey.