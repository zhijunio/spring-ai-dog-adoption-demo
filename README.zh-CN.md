# Spring AI 狗狗领养助手 Demo

[![Java](https://img.shields.io/badge/Java-21-blue?logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.1.2-6DB33F?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Spring AI](https://img.shields.io/badge/Spring%20AI-2.0.2-6DB33F?logo=spring&logoColor=white)](https://spring.io/projects/spring-ai)
[![Maven](https://img.shields.io/badge/Maven-3.10.0-C71A36?logo=apachemaven&logoColor=white)](https://maven.apache.org/)
[![GitHub stars](https://img.shields.io/github/stars/zhijunio/spring-ai-dog-adoption-demo)](https://github.com/zhijunio/spring-ai-dog-adoption-demo/stargazers)
[![许可证](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](LICENSE)

简体中文 | [English](README.md)

这是一个由两个应用组成的狗狗领养助手示例。Web 应用使用 Spring AI、PostgreSQL/pgvector 和 MCP 预约服务回答领养问题并安排预约。

## 项目模块

- `adoptions`：Web 应用、PostgreSQL/pgvector 向量存储和持久化聊天记忆。
- `scheduler`：运行在 `8081` 端口、提供预约工具的 MCP 服务端。

## 环境要求

- JDK 21
- [mise](https://mise.jdx.dev/)（用于安装项目指定的 Java 和 Maven 版本）
- Docker Compose
- OpenAI API Key；使用 `qwen` profile 时需要 DashScope API Key

## 本地运行

安装项目工具链，并启动 PostgreSQL 和 pgvector：

```bash
mise install
cd adoptions
docker compose up -d
```

在第二个终端启动 MCP 预约服务：

```bash
cd scheduler
./mvnw spring-boot:run
```

再打开一个终端，配置模型提供商并启动 Web 应用：

```bash
export OPENAI_API_KEY=your-api-key
cd adoptions
./mvnw spring-boot:run
```

Web 应用地址：<http://localhost:8080/>。使用 Qwen 时，设置 `DASHSCOPE_API_KEY`，并以 `qwen` Spring profile 启动应用：

```bash
export DASHSCOPE_API_KEY=your-api-key
SPRING_PROFILES_ACTIVE=qwen ./mvnw spring-boot:run
```

## 文章

参阅[用 Spring AI 构建会思考的狗狗领养助手](https://blog.zhijun.io/posts/spring-ai-dog-adoption-showcase/)了解项目实现。

## 许可证

本项目采用 Apache License 2.0。完整许可条款请参阅 [LICENSE](LICENSE)。
