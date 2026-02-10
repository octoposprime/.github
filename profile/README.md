# 🐙 OctopOS Prime

> Modern, scalable software ecosystem based on microservice architecture

[![Email](https://img.shields.io/badge/Email-info@octoposprime.com-red)](mailto:info@octoposprime.com)
[![Location](https://img.shields.io/badge/Location-USA-green)]()
[![Followers](https://img.shields.io/badge/Followers-81-orange)]()

## 📋 Table of Contents

- [Overview](#-overview)
- [System Architecture](#-system-architecture)
- [Repository Structure](#-repository-structure)
- [Technology Stack](#-technology-stack)
- [Installation and Getting Started](#-installation-and-getting-started)
- [Contributing](#-contributing)
- [License](#-license)

## 🎯 Overview

**OctopOS Prime** is a comprehensive software platform developed using modern software development principles and microservice architecture. The system consists of independently deployable microservices that communicate via Protocol Buffers.

### Key Features

- 🏗️ **Microservice Architecture**: Independent, scalable services
- 🔐 **Security**: JWT-based authentication and authorization
- 📡 **GraphQL API Gateway**: Single point access to all services
- 📱 **Cross-Platform**: Web and mobile applications
- 🐳 **Containerization**: Easy deployment with Docker
- 📊 **Observability**: Centralized logging and monitoring

## 🏛️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Client Layer                             │
│  ┌──────────────┐              ┌──────────────┐             │
│  │  Web Client  │              │ Mobile App   │             │
│  │  (op-web-    │              │ (op-mo-app)  │             │
│  │   site)      │              │   Flutter    │             │
│  └──────────────┘              └──────────────┘             │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                    API Gateway                              │
│              ┌──────────────────────┐                       │
│              │   op-be-graphql      │                       │
│              │   (GraphQL Gateway)  │                       │
│              └──────────────────────┘                       │
└─────────────────────────────────────────────────────────────┘
                           │
           ┌───────────────┼───────────────┐
           ▼               ▼               ▼
┌─────────────────────────────────────────────────────────────┐
│                Backend Microservices                        │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐     │
│  │ op-be-   │  │ op-be-   │  │ op-be-   │  │ op-be-   │     │
│  │  auth    │  │  user    │  │ logging  │  │  book    │     │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘     │
│                                                             │
│  ┌──────────┐              ┌──────────────────────┐         │
│  │ op-be-   │              │   op-be-shared       │         │
│  │  dlr     │              │  (Common Library)    │         │
│  └──────────┘              └──────────────────────┘         │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                   SDK & Protocol Layer                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │
│  │  op-go-sdk-  │  │  op-go-sdk-  │  │   op-proto   │       │
│  │     srv      │  │     clt      │  │   (ProtoBuf) │       │
│  └──────────────┘  └──────────────┘  └──────────────┘       │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                    OS & Infrastructure                      │
│  ┌──────────────┐              ┌──────────────┐             │
│  │  op-go-os    │              │  op-infra    │             │
│  │              │              │              │             │
│  └──────────────┘              └──────────────┘             │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                  Data & Cache Layer                         │
│              PostgreSQL + Redis                             │
└─────────────────────────────────────────────────────────────┘
```

## 📦 Repository Structure

### 🔌 Protocol & SDK Layer

| Repository | Description | Technology | Stars |
|-----------|----------|-----------|---------|
| [op-proto](https://github.com/octoposprime/op-proto) | Protocol Buffers definitions - Communication protocol for all services | Protocol Buffers | ⭐ 58 |
| [op-go-os](https://github.com/octoposprime/op-go-os) | OctopOS Prime operating system layer | Go | ⭐ 57 |
| [op-go-sdk-srv](https://github.com/octoposprime/op-go-sdk-srv) | Server-side SDK - Server-side development library | Go | ⭐ 58 |
| [op-go-sdk-clt](https://github.com/octoposprime/op-go-sdk-clt) | Client-side SDK - Client-side development library | Go | ⭐ 56 |

### 🔐 Backend Services

| Repository | Description | Port | Stars |
|-----------|----------|------|---------|
| [op-be-graphql](https://github.com/octoposprime/op-be-graphql) | GraphQL API Gateway - Main API router | 18080 | ⭐ 13 |
| [op-be-auth](https://github.com/octoposprime/op-be-auth) | Authentication and authorization service | 18084 | ⭐ 5 |
| [op-be-user](https://github.com/octoposprime/op-be-user) | User management service | 18082 | ⭐ 17 |
| [op-be-logging](https://github.com/octoposprime/op-be-logging) | Centralized logging service | 18081 | - |
| [op-be-book](https://github.com/octoposprime/op-be-book) | Book/content management service | - | ⭐ 7 |
| [op-be-dlr](https://github.com/octoposprime/op-be-dlr) | DLR (Data Layer Repository) service | 18083 | - |
| [op-be-shared](https://github.com/octoposprime/op-be-shared) | Backend shared libraries | - | ⭐ 14 |
| [op-be-docs](https://github.com/octoposprime/op-be-docs) | Backend documentation | - | - |

### 🖥️ Frontend & Mobile

| Repository | Description | Technology | Stars |
|-----------|----------|-----------|---------|
| [op-web-site](https://github.com/octoposprime/op-web-site) | Web application | TypeScript/CSS/HTML | ⭐ 11 |
| [op-mo-app](https://github.com/octoposprime/op-mo-app) | Mobile application (Android/iOS) | Flutter | ⭐ 17 |

### 🛠️ Infrastructure & DevOps

| Repository | Description | Technology | Stars |
|-----------|----------|-----------|---------|
| [op-infra](https://github.com/octoposprime/op-infra) | Infrastructure as Code, deployment scripts | Shell Scripts | ⭐ 8 |

### 🎨 Design & Community

| Repository | Description | Stars |
|-----------|----------|---------|
| [op-design](https://github.com/octoposprime/op-design) | Design system and style guides | ⭐ 16 |
| [octo-bot](https://github.com/octoposprime/octo-bot) | Discord community management bot | - |
| [.github](https://github.com/octoposprime/.github) | Organization profile and templates | ⭐ 8 |

## 🔧 Technology Stack

### Backend
- **Language**: Go (Golang)
- **API**: GraphQL
- **Protocol**: Protocol Buffers (gRPC)
- **Authentication**: JWT (JSON Web Tokens)
- **Database**: PostgreSQL
- **Cache**: Redis
- **Container**: Docker
- **Network**: Docker Network

### Frontend
- **Web**: TypeScript, CSS, HTML
- **Mobile**: Flutter (Dart)

### DevOps & Infrastructure
- **Container Orchestration**: Docker
- **Scripting**: Shell Scripts
- **CI/CD**: GitHub Actions

### Monitoring & Logging
- **Logging**: Centralized logging service (op-be-logging)
- **Port Management**: Dedicated port assignment for each service

## 🚀 Installation and Getting Started

### Requirements

```bash
- Docker & Docker Compose
- Go 1.21+ (for backend development)
- Flutter 3.0+ (for mobile development)
- Node.js 18+ (for web development)
- PostgreSQL 15+
- Redis 7+
```

### Environment Variables

Required environment variables for all backend services:

```env
# Database
POSTGRES_USERNAME=op
POSTGRES_PASSWORD=op
POSTGRES_DATABASE=op

# Authentication
JWT_SECRET_KEY=op

# Cache
REDIS_PASSWORD=op

# Testing
TEST=true
```

### Create Docker Network

```bash
docker network create op
```

### Start Backend Services

```bash
# Logging service
docker run --pull=always -d --expose 18081 -p 18081:18080 \
  --network op -e TEST=true --name op-be-logging \
  ghcr.io/octoposprime/op-be-logging:latest

# User service
docker run --pull=always -d --expose 18082 -p 18082:18080 \
  --network op -e TEST=true --name op-be-user \
  ghcr.io/octoposprime/op-be-user:latest

# GraphQL API Gateway
docker run --pull=always -d --expose 18080 -p 18080:18080 \
  --network op -e TEST=true --name op-be-graphql \
  ghcr.io/octoposprime/op-be-graphql:latest

# DLR service
docker run --pull=always -d --expose 18083 -p 18083:18080 \
  --network op -e TEST=true --name op-be-dlr \
  ghcr.io/octoposprime/op-be-dlr:latest

# Auth service
docker run --pull=always -d --expose 18084 -p 18084:18080 \
  --network op -e TEST=true --name op-be-auth \
  ghcr.io/octoposprime/op-be-auth:latest
```

### Stop Services

```bash
docker stop op-be-logging op-be-user op-be-graphql op-be-dlr op-be-auth
docker rm op-be-logging op-be-user op-be-graphql op-be-dlr op-be-auth
```

### Port Structure

| Service | Internal Port | External Port |
|--------|---------|----------|
| GraphQL Gateway | 18080 | 18080 |
| Logging | 18080 | 18081 |
| User | 18080 | 18082 |
| DLR | 18080 | 18083 |
| Auth | 18080 | 18084 |

## 📚 Microservice Architecture Principles

### 1. Independent Deployment
Each service runs in its own Docker container and can be deployed independently.

### 2. Protocol Buffers Communication
Inter-service communication is done via Protocol Buffers (gRPC), which provides:
- Type-safe communication
- High performance
- Automatic code generation

### 3. API Gateway Pattern
`op-be-graphql` serves as the single entry point for all client requests.

### 4. Shared Library
`op-be-shared` provides common functions and utilities, preventing code duplication.

### 5. Centralized Logging
`op-be-logging` centrally collects logs from all services.

## 🔐 Security

- **JWT Authentication**: Token-based authentication
- **Service Isolation**: Each service in isolated Docker container
- **Environment Variables**: Sensitive information stored as environment variables
- **Network Isolation**: Service isolation via Docker network

## 🤝 Contributing

OctopOS Prime is an open source project and we welcome your contributions!

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: Add amazing feature'`)
4. Push your branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards

- Use `gofmt` for Go code standards
- Use [Conventional Commits](https://www.conventionalcommits.org/) for commit messages
- Write unit tests for every change
- Keep documentation up to date

## 📞 Contact

- **Website**: [octoposprime.com](http://octoposprime.com)
- **Email**: [info@octoposprime.com](mailto:info@octoposprime.com)
- **Location**: United States of America
- **Discord**: Community bot active (octo-bot)

## 📄 License

All repositories in this project are licensed under **MIT License**.

## 👥 Contributors

**37 contributors** have made **732 commits** to the OctopOS Prime organization.

<div align="center">

<a href="https://github.com/husamettinarabaci" title="husamettinarabaci - 176 contributions">
  <img src="https://avatars.githubusercontent.com/u/5726898?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="husamettinarabaci">
</a>
<a href="https://github.com/Sddilora" title="Sddilora - 122 contributions">
  <img src="https://avatars.githubusercontent.com/u/122971619?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="Sddilora">
</a>
<a href="https://github.com/aleyna0f" title="aleyna0f - 68 contributions">
  <img src="https://avatars.githubusercontent.com/u/118018067?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="aleyna0f">
</a>
<a href="https://github.com/Maraza25" title="Maraza25 - 45 contributions">
  <img src="https://avatars.githubusercontent.com/u/70588276?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="Maraza25">
</a>
<a href="https://github.com/ikramylmz" title="ikramylmz - 40 contributions">
  <img src="https://avatars.githubusercontent.com/u/152586341?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="ikramylmz">
</a>
<a href="https://github.com/Smnrgcl" title="Smnrgcl - 38 contributions">
  <img src="https://avatars.githubusercontent.com/u/153975823?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="Smnrgcl">
</a>
<a href="https://github.com/akadir8" title="akadir8 - 27 contributions">
  <img src="https://avatars.githubusercontent.com/u/109678256?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="akadir8">
</a>
<a href="https://github.com/suhedadogan50" title="suhedadogan50 - 26 contributions">
  <img src="https://avatars.githubusercontent.com/u/135768038?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="suhedadogan50">
</a>
<a href="https://github.com/Feyzanrs" title="Feyzanrs - 23 contributions">
  <img src="https://avatars.githubusercontent.com/u/141928475?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="Feyzanrs">
</a>
<a href="https://github.com/Weal1041" title="Weal1041 - 21 contributions">
  <img src="https://avatars.githubusercontent.com/u/144017529?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="Weal1041">
</a>
<a href="https://github.com/aminenurgynk" title="aminenurgynk - 16 contributions">
  <img src="https://avatars.githubusercontent.com/u/130973404?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="aminenurgynk">
</a>
<a href="https://github.com/mervegonc" title="mervegonc - 15 contributions">
  <img src="https://avatars.githubusercontent.com/u/117481952?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="mervegonc">
</a>
<a href="https://github.com/nurbeyzaoztrk" title="nurbeyzaoztrk - 14 contributions">
  <img src="https://avatars.githubusercontent.com/u/120026216?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="nurbeyzaoztrk">
</a>
<a href="https://github.com/ebrarkesici" title="ebrarkesici - 12 contributions">
  <img src="https://avatars.githubusercontent.com/u/141298599?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="ebrarkesici">
</a>
<a href="https://github.com/SoyluAlaattin" title="SoyluAlaattin - 12 contributions">
  <img src="https://avatars.githubusercontent.com/u/136907277?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="SoyluAlaattin">
</a>
<a href="https://github.com/baburakbas" title="baburakbas - 10 contributions">
  <img src="https://avatars.githubusercontent.com/u/82142760?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="baburakbas">
</a>
<a href="https://github.com/yavuz-yusuf" title="yavuz-yusuf - 9 contributions">
  <img src="https://avatars.githubusercontent.com/u/142804723?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="yavuz-yusuf">
</a>
<a href="https://github.com/SeyyidhanTaskin" title="SeyyidhanTaskin - 9 contributions">
  <img src="https://avatars.githubusercontent.com/u/109666785?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="SeyyidhanTaskin">
</a>
<a href="https://github.com/samiigll" title="samiigll - 8 contributions">
  <img src="https://avatars.githubusercontent.com/u/148059353?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="samiigll">
</a>
<a href="https://github.com/yusufyilmazf" title="yusufyilmazf - 5 contributions">
  <img src="https://avatars.githubusercontent.com/u/109434872?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="yusufyilmazf">
</a>
<a href="https://github.com/eboreis" title="eboreis - 5 contributions">
  <img src="https://avatars.githubusercontent.com/u/100617437?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="eboreis">
</a>
<a href="https://github.com/nedimtoymus" title="nedimtoymus - 5 contributions">
  <img src="https://avatars.githubusercontent.com/u/136761371?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="nedimtoymus">
</a>
<a href="https://github.com/furkanadiiguzel" title="furkanadiiguzel - 4 contributions">
  <img src="https://avatars.githubusercontent.com/u/101877734?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="furkanadiiguzel">
</a>
<a href="https://github.com/ahmetarabaci42" title="ahmetarabaci42 - 3 contributions">
  <img src="https://avatars.githubusercontent.com/u/158732628?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="ahmetarabaci42">
</a>
<a href="https://github.com/esmanrshn" title="esmanrshn - 2 contributions">
  <img src="https://avatars.githubusercontent.com/u/128504391?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="esmanrshn">
</a>
<a href="https://github.com/krmlp" title="krmlp - 2 contributions">
  <img src="https://avatars.githubusercontent.com/u/151014319?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="krmlp">
</a>
<a href="https://github.com/samedfenerli" title="samedfenerli - 2 contributions">
  <img src="https://avatars.githubusercontent.com/u/157889420?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="samedfenerli">
</a>
<a href="https://github.com/HalilTurkmen10" title="HalilTurkmen10 - 2 contributions">
  <img src="https://avatars.githubusercontent.com/u/140647268?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="HalilTurkmen10">
</a>
<a href="https://github.com/doganabdussamed" title="doganabdussamed - 2 contributions">
  <img src="https://avatars.githubusercontent.com/u/140983328?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="doganabdussamed">
</a>
<a href="https://github.com/johsquaree" title="johsquaree - 2 contributions">
  <img src="https://avatars.githubusercontent.com/u/130278251?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="johsquaree">
</a>
<a href="https://github.com/Aysesdka3450" title="Aysesdka3450 - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/167804362?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="Aysesdka3450">
</a>
<a href="https://github.com/arzuuddemir" title="arzuuddemir - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/119745513?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="arzuuddemir">
</a>
<a href="https://github.com/kasryan" title="kasryan - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/120013347?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="kasryan">
</a>
<a href="https://github.com/begumnurbayraktar" title="begumnurbayraktar - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/169983471?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="begumnurbayraktar">
</a>
<a href="https://github.com/coverskull" title="coverskull - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/169452444?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="coverskull">
</a>
<a href="https://github.com/haticebabaoglu" title="haticebabaoglu - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/100375578?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="haticebabaoglu">
</a>
<a href="https://github.com/sudenznl" title="sudenznl - 1 contributions">
  <img src="https://avatars.githubusercontent.com/u/118690915?v=4" width="80" height="80" style="border-radius: 50%; margin: 5px;" alt="sudenznl">
</a>

</div>

### 🏆 Top Contributors

| Rank | Contributor | Total Commits | Repositories |
|------|-------------|---------------|--------------|
| 1 | [husamettinarabaci](https://github.com/husamettinarabaci) | 176 | 27 |
| 2 | [Sddilora](https://github.com/Sddilora) | 122 | 15 |
| 3 | [aleyna0f](https://github.com/aleyna0f) | 68 | 1 |
| 4 | [Maraza25](https://github.com/Maraza25) | 45 | 8 |
| 5 | [ikramylmz](https://github.com/ikramylmz) | 40 | 1 |
| 6 | [Smnrgcl](https://github.com/Smnrgcl) | 38 | 6 |
| 7 | [akadir8](https://github.com/akadir8) | 27 | 4 |
| 8 | [suhedadogan50](https://github.com/suhedadogan50) | 26 | 1 |
| 9 | [Feyzanrs](https://github.com/Feyzanrs) | 23 | 9 |
| 10 | [Weal1041](https://github.com/Weal1041) | 21 | 1 |

## 🌟 Statistics

Growing community with over **300+** stars across repositories!

---

<div align="center">
  <strong>Built with ❤️ by OctopOS Prime Team</strong>
  <br/>
  <sub>Making microservices development easier and scalable</sub>
</div>
