# Yoga Prisma Starter

![](https://prisma.gallerycdn.vsassets.io/extensions/prisma/vscode-graphql/0.1.7/1550374189143/Microsoft.VisualStudio.Services.Icons.Default)

<!-- TABLE OF CONTENTS -->

## Table of Contents

- [About the Project](#about-the-project)
  - [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Configuration](#configureation)
- [Acknowledgements](#acknowledgements)

<!-- ABOUT THE PROJECT -->

## About The Project

Yoga Prisma Starter is an Apollo GraphQL Server wrapped with Prisma. It is hosted on Heroku using Docker.

**Prisma ** is a replacement for traditional ORMs and delivers the connection to a database that allows you to access the db with graphl framework.

**Yoga ** is a GraphQL Server with focus on easy setup, performance & great developer experience.

### Built With :green_heart:

- [Prisma](https://www.prisma.io/with-graphql/)
- [Apollo](https://www.apollographql.com/)
- [GraphQL Yoga](https://github.com/prisma-labs/graphql-yoga)
- [Heroku](https://www.heroku.com/)
- [Docker](https://www.docker.com/)


<!-- GETTING STARTED -->

## Getting Started

To get a local copy up and running follow these steps.

### Prerequisites

Install NPM

### Installation

1. Clone the repo

```sh
git clone https://github.com/kflan-io/yoga-prisma-starter.git
```

2.  Install NPM packages

- npm

```sh
npm install
```

- yarn

```sh
yarn install
```

<!-- yarn install npm@latest -->

### Configuration

1. Create TWO files, `.env.` and `.env.prod` and enter two keys: 
```JS
PRISMA_ENDPOINT=http://localhost:4466 
PRISMA_SECRET=myPrismaSecret
```

2. Verify your file, datamodel.prisma, is correct. [prisma introspect another db to get data].

3. Install packages and fix any depencencies:
```BASH
$ npm install && npm audit fix
```

4.  Run the docker (two) containers: 
```BASH
$ docker-compose up -d
```

5.  Run a Prisma Deploy to check for any connection errors:
```BASH
$ prisma deploy
```
If that runs, then prisma is setup locally and running on `http://localhost:4466` & `http://localhost:4466/_admin`

6.  Visit [Prisma.io](https://app.prisma.io/) and set up the production version, an online DB with Heroku.
- `Add Server` (under the Servers tab), enter server name and description and `Create Server`
- `Create Database` using Heroku. 
Now that you have the DB, follow the steps to set up the server, using Heroku again, and `Create Server` for the DB.

7. Link that new DB server to your local setup:
`$ prisma deploy -n` and pick that newly create DB, which will give you the production endpoint on Heroku. 

8. Update ./prisma.yml file: 
```JS
endpoint: ${env:PRISMA_ENDPOINT}
secret: ${env:PRISMA_SECRET}
datamodel: datamodel.prisma
```

9. Update ./.env.prod file: 
```JS
PRISMA_ENDPOINT=https://your-new-heroku-endpoint`
PRISMA_SECRET=myPrismaSecret
```

10. 
```BASH
$ npm run deploy-prod
```

   <!-- ACKNOWLEDGEMENTS -->

## Acknowledgements

- [Prisma.io](https://www.prisma.io/)
- [Set Up Prisma with Docker](https://www.prisma.io/docs/get-started/01-setting-up-prisma-new-database-JAVASCRIPT-a002/)
- [Prisma API token](https://www.prisma.io/docs/reference/prisma-api/concepts-utee3eiquo#api-token)
