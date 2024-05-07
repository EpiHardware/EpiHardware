# EpiHardware: E-Business Platform for Computer Parts

Welcome to the GitHub repository of EpiHardware, your go-to e-business platform specializing in the sale of computer
parts. Built using React for the frontend and Symfony for the backend, this platform offers a robust, scalable, and
user-friendly interface for purchasing computer hardware online.

## Table of Contents

- [Getting Started](#getting-started)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Application](#running-the-application)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing
purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Before you begin, ensure you have the following tools installed on your system:

- **Git**
- **PHP** (version 7.4 or higher)
- **Composer** - for managing PHP dependencies
- **Node.js** (including npm) - for managing JavaScript dependencies
- **Symfony CLI** - for local development and testing
- **Docker** - for containerization

### Installation

This application is shipped with Docker and Docker Compose for containerization. It uses other projects that need to be
cloned recursively. You can do so with the following command:

```bash
git clone git@github.com:EpiHardware/EpiHardware.git --recursive
```

Edit the `.env` environment file and make the necessary changes in accordance to your local setup.

### Running the Application

To run the application, execute the following command:

Without Docker:

```bash
cd EpiHardware-frontend
npm install
npm run start
```

```bash
cd EpiHardware-backend
composer install
symfony console doctrine:migration:migrate
symfony console doctrine:fixtures:load
mkdir config/jwt
openssl genpkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096
# Enter a passphrase when prompted
openssl pkey -in config/jwt/private.pem -out config/jwt/public.pem -pubout
symfony server:start
````

With docker:

```bash
cd EpiHardware
docker-compose up
```