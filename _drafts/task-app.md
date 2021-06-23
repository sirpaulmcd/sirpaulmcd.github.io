---
layout: default
title: Task App
permalink: /projects/task-app/
parent: Projects
# grand_parent: Blog
has_children: false
nav_order: 1
nav_exclude: false
has_toc: false
---

# Task App

A full-stack To-Do List application. After creating an account, users can manage their user information as well as To-Do style tasks in various lists. The project repo can be found [here](https://github.com/sirpaulmcd/Task-App).

## How to use

Check and see if the project is currently deployed [here](http://taskapp.paulsprojects.xyz). If not, a development build can be easily created with the following instructions:

- Download Docker Desktop and Git (prerequisite)
- Clone the project [repo](https://github.com/sirpaulmcd/Task-App) to your computer
- Open a terminal at the root level of the project folder and use the command `docker-compose --env-file docker-compose.env up --build`
- Open your browser to [http://localhost:3000/](http://localhost:3000/)

## Preview

### Sign Up or Login

### Manage your account

### Create tasks for various lists

- Task creation
- Completing a task
- Editing a task (change lists)
- Deleting a task

## Stack and Deployment

Task App is built using the MERN stack:

- **M**ongoDB document database (with Mongoose)
- **E**xpressJS API backend
- **R**eactJS frontend
- **N**odeJS runtime environment

Task App is deployed using:

- Docker (containerized environments)
- DigitalOcean Droplet (remote linux virtual machine)
- Nginx (web server, reverse proxy)
- Certbot (SSL certificate)

## Learning

I chose a To-Do List style application because I didn't want to reinvent the wheel on my first attempt at a full-stack web application. Although the app may seem rather simple, I was surprised to find out how much critical thinking goes on behind the scenes of a typical web application. To create/deploy this Task App, I needed to take in an ocean of knowledge. To help get my point across, I've organized some noteworthy technologies/concepts that were necessary for this project.

**General Web Development**

- JavaScript/Typescript languages
- NodeJS runtime environment
- User authentication/management best practices
- HTTP Protocol
- JSON Web Tokens (JWT)
- Browser Cookies

**Frontend Client**

- React library
- MaterialUI library
- React-transition-group library
- Dynamic routing
- Axios API interactions and related data management
- Responsive styling for page resizing (CSSGrid and Flexbox)

**Backend API**

- ExpressJS framework
- Postman (API development tool)
- Password storage (hash and salt)
- Managing authentication tokens/cookies
- CRUD operations with database
- Sorting, filtering, and pagination
- File uploads
- API testing (supertest)

**Database**

- MongoDB (NoSQL database)
- Mongoose (ODM library for Mongo)

**General Development and Deployment**

- Git (version control)
- GitHub Actions (automating QA checks)
- Docker (containerizing applications)
- Managing environment variables
- DigitalOcean Droplets (remote linux virtual machine)
- Linux server management and best practices
- Nginx (web server, reverse proxy)
- Registering and configuring internet domain names
- Certbot (enalbing HTTPS)

Needless to say, I'm glad to have this project under my belt. Creating and deploying a full-stack application for the first time is a huge milestone for me and I feel much more competent than when I started.

## Moving Forward

Backlog (if I feel like it):

- Implement custom user lists (currently, users can only use premade list categories)
- User list sharing (let multiple users view/manage the same list)
- Continuous Integration (server automatically serves latest docker image)
- Email verification
