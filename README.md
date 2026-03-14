# ft_transcendence

A full-stack web application developed as part of the 42 curriculum.
`ft_transcendence` is a single-page web application built around an online Pong project, with authentication, live chat, tournaments and a multi-service architecture.

It was a good way to build solid foundations in backend service design, real-time communication, deployment and security in a larger collaborative project.

## Features
- Single-page web application built around an online Pong project
- User accounts with authentication and profile management
- Local and online gameplay flows
- Tournament and matchmaking logic
- Live chat and real-time communication features
- Dockerized multi-service architecture
- HTTPS-enabled deployment
- Monitoring and logging components in the project stack

## Project structure
- `Makefile` — build and lifecycle commands for the whole stack
- `docker-compose.yml` — top-level Docker orchestration file
- `srcs/requierements/frontend/` — TypeScript frontend, pages, game logic and UI assets
- `srcs/requierements/services/chat-service/` — backend service for live chat and socket-based messaging
- `srcs/requierements/services/user-service/` — backend service for user accounts, authentication and user-related persistence
- `srcs/requierements/nginx/` — HTTPS entry point and reverse-proxy configuration
- `srcs/requierements/elk/` — Elasticsearch, Logstash and Kibana configuration
- `srcs/requierements/prometheus/` — Prometheus configuration and alerting rules
- `srcs/requierements/grafana/` — Grafana provisioning and dashboards

## Mandatory part
The mandatory part focuses on the application flow required to deliver a browser-based Pong experience with accounts and tournaments.

### Core application
- browser-based Pong experience
- single-page application flow
- user registration and authentication
- tournament and matchmaking features
- HTTPS-enabled access
- Docker-based project startup

### Core behavior
- serves a frontend application through a containerized stack
- handles user-related logic through dedicated backend services
- supports profile-related and account-related flows
- includes gameplay, tournament and chat-related project components
- routes traffic through nginx as the public entry point
- runs the full application through Docker and Compose-based orchestration

### What happens at runtime
- the stack is built and started through the project Makefile and Docker Compose
- nginx acts as the public entry point for the application
- the frontend handles the single-page navigation and game-related UI
- backend services process account, chat and other application logic
- monitoring and logging services can observe the running stack

### Subject requirements to respect
- the project must stay a single-page application
- the frontend must be based on TypeScript
- the website must run through Docker
- the application must provide a Pong game and tournament flow
- user input must be validated properly
- the project must be protected against common security issues such as SQL injection and XSS
- HTTPS must be enabled when backend features are used
- secrets and environment-specific credentials must stay out of git

## Notes
This repository comes from a collaborative 42 project built with [Gl1tsh](https://github.com/Gl1tsh), [HaruSnak](https://github.com/HaruSnak) and [tmoel1](https://github.com/tmoel1).
The other parts of the project mainly covered the frontend framework, chat, infrastructure, tournament systems and observability stack.

## My part in this project
My part in this project was the user-service.
That means the database-backed user management and authentication side of the project.

### What I worked on
- user accounts and authentication flows
- profile-related data and account updates
- match history on the user side
- blocking-related user features
- persistence for user-related data through the service database
- the API layer used by the rest of the project for user-side operations

### Main tools and technologies I used
- **Node.js** for the service runtime
- **Fastify** for the HTTP API and route handling
- **SQLite** for persistent user-related data
- **JWT** for authentication
- **bcrypt** for password hashing
- **Docker** for service integration inside the project stack

### Main notions involved in my part
- REST-style API design
- authentication and authorization
- password hashing
- token-based sessions with JWT
- input validation and sanitization
- SQL persistence and relational data
- profile and account lifecycle management
- service separation inside a bigger microservice-oriented project

## Usage
Build and start the full project stack:

```bash
make
```

Once the services are running, the main application and monitoring tools are available at:

- `https://localhost:8443` — main web application
- `http://localhost:5601` — Kibana
- `http://localhost:9090` — Prometheus
- `http://localhost:3010` — Grafana

The stack also exposes this technical endpoint:

- `http://localhost:9200` — Elasticsearch API

From the main application, you can create an account, log in and access the game and user-related features from the browser.

Build the images only:

```bash
make build
```

Start the containers:

```bash
make up
```

Stop the containers:

```bash
make down
```

Clean Docker resources:

```bash
make clean
```

Rebuild everything from scratch:

```bash
make re
```

## Learning outcomes
This project was my first real experience working on a larger full-stack application with multiple moving parts.
It helped build solid foundations in:
- collaborative project structure
- service-oriented backend design
- user management and authentication flows
- database-backed application logic
- Docker-based project orchestration
- HTTPS and web-application security constraints
- integrating one focused service inside a much bigger product
