# Spring AI Dog Adoption Demo

[![Java](https://img.shields.io/badge/Java-21-blue?logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.1.2-6DB33F?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Spring AI](https://img.shields.io/badge/Spring%20AI-2.0.2-6DB33F?logo=spring&logoColor=white)](https://spring.io/projects/spring-ai)
[![Maven](https://img.shields.io/badge/Maven-3.10.0-C71A36?logo=apachemaven&logoColor=white)](https://maven.apache.org/)
[![GitHub stars](https://img.shields.io/github/stars/zhijunio/spring-ai-dog-adoption-demo)](https://github.com/zhijunio/spring-ai-dog-adoption-demo/stargazers)
[![License](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](LICENSE)

[简体中文](README.zh-CN.md) | English

A two-application sample for a dog adoption assistant. The web app uses Spring AI, PostgreSQL with pgvector, and an MCP scheduler service to answer adoption questions and arrange appointments.

## Project modules

- `adoptions` — the web application, PostgreSQL/pgvector vector store, and persistent chat memory.
- `scheduler` — an MCP server that provides appointment scheduling tools on port `8081`.

## Requirements

- JDK 21
- [mise](https://mise.jdx.dev/) to install the pinned Java and Maven versions
- Docker Compose
- An OpenAI API key, or a DashScope API key when using the `qwen` profile

## Run locally

Install the project toolchain and start PostgreSQL with pgvector:

```bash
mise install
cd adoptions
docker compose up -d
```

In a second terminal, start the MCP scheduler:

```bash
cd scheduler
./mvnw spring-boot:run
```

In another terminal, configure your model provider and start the web app:

```bash
export OPENAI_API_KEY=your-api-key
cd adoptions
./mvnw spring-boot:run
```

The web app listens on <http://localhost:8080/>. To use Qwen, set `DASHSCOPE_API_KEY` and start the app with the `qwen` Spring profile:

```bash
export DASHSCOPE_API_KEY=your-api-key
SPRING_PROFILES_ACTIVE=qwen ./mvnw spring-boot:run
```

## Article

See [Build a Thinking Dog Adoption Assistant with Spring AI](https://blog.zhijun.io/posts/spring-ai-dog-adoption-showcase/) for the walkthrough.

## License

This project is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for the full terms.
