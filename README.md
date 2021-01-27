
<!-- PROJECT SHIELDS -->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

## Containerised Go Application + NGINX

Simple solution that runs a Hello World Go application along with NGINX and enables scalability with security best practices

## Getting Started

### Prerequisites

Ports `80` and `443` shoudl be availabe in your localhost or machine where you run this code.

## Usage

```
docker-compose up --scale go-webapp=3
```
_Where `go-webapp=3` is the amount of instances for the Go webapp_

> Then open `http://localhost`

## Security Measures

- Dropped all capabilities for `go-webapp` container
- Dropped all capabilities, added necessary ones for `nginx` container
- Rootless container for `go-webapp`
- `nginx-alpine` image is used from a trusted repository
- Only necessary ports are exposed or open
- Used fixed versions rather than "latest" for Docker images

## Static code analysis

Here are some recommendations for both Dockerfile and Go application.

#### Dockerfile

Use Hadolint. This will output issues if there are any.
```
docker run --rm -i hadolint/hadolint < Dockerfile
```

#### Go application

Using SonarQube. For this purpose, we can spin up a docker container and analyze the code.

```
docker run -d --name sonarqube -p 9000:9000 sonarqube
```

Also using linters and code coverage would be great


## Code Review Guidelines

- Select the Git strategy that works best for the team (e.g: GitHub flow, Gitflow, etc)
- For this purpose, I'm using GitHub flow so developers shouldn't commit straight to `master` branch
- Feature branches should be created, then a Pull Request should be generated (`master` <- `feature/mycoolstuff`) and assign to a different developer, not the PR owner.
- A PR should be reviewed and approved before merging back to master.
- Constructive Feedback is welcomed. If you think the code meets the quality createria, great. Otherwise, provide comments with feedback and perhaps some ideas that could make the code look better, so it can be taken to next level of quality.
- If a comment is not enough or there are different opinions, have a chat/meeting in order to have better communication.

> Goals of Code Review:
>- Improve code quality
>- Reduce number of potential bugs
>- Learn and get better at coding

#### Next steps:
- Use `linters`, `code coverage tools`, `static code analysis`, `static security tools` in a CI/CD pipeline as well as in your workstation (git hooks). This will improve the quality, experience and reduce human code review times 


## Access rights, Logging and Encryption

- Access rights can be hablded through basic NGINX authentication or a third party solution
- Access loggin can be handled through NGINX logger
- Application logging can be handled with differnt tools (like logstash)
- Encryption on-the-fly can be handled with HTTPS (TLS certificates need to be setup)
- Encryption at rest can be handled direct from the cloud provider (AWS Fargate, EC2)
- Code updates should always be code reviewed and approved 

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact

Gerardo Prieto - [@sherarr](https://twitter.com/sherarr)
Project Link: [https://github.com/sherar/go-nginx-webapp](https://github.com/sherar/go-nginx-webapp)