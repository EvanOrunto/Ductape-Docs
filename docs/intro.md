---
sidebar_position: 1
slug: /
---

# Intro

Let's discover **Ductape in less than 5 minutes**.

## What is Ductape

Ductape allows you to build scalable and maintainable integrations with code. You can build products and features on top of those integrations without the need for extensive coding. With ductape, you can also orchestrate between various microservices, or coordinate between different API vendors. This level of control and automation not only simplifies the development process but also enhances the efficiency of your workflows.

Ductape allows you to:

- Build integrations that scale with your business needs.
- Ensure maintainability and flexibility in your integration solutions.
- Develop products and features on top of integrations.
- Implement retries for robustness in the face of transient errors.
- Set timeouts to control response times and enhance performance.
- Orchestrate seamlessly between different microservices.
- Quickly add new products and features to meet evolving business demands.

All this adds up to giving you the power to build fast and scale faster. You can build more products and add features as quickly as you want.

## Ductape Components

APPS: These are your RESTful applications which provide a suite of functionalities for your clients and customers

- **ACTIONS**: These are the individual functionalities, that are encapsulated within a single API call
- **FEATURES**: These allow you to bundle up multiple actions with custom logic and components
  to seamlessly build new functionality
- **PROCESS**: These execute features, by receiving an input and providing an output as defined in
  the feature
- **JOBS**: These handle long-running processes and workflows.

## Getting Started

### Installation

To get started, Install the ductape cli and sdk with npm or yarn

##### NPM

```bash
npm install -g ductape-cli ductape-sdk
```

##### YARN

```bash
yarn add ductape-cli ductape-sdk
```

After installation you have to create an account using the cli

### User

#### CLI: User Registration

```bash
ductape register
```

and follow the prompts to fill in your first name, last name, email address and password

#### CLI: User Login

```bash
ductape login
```

Here you are expected to login as the user you just created. When logging in, you will be required to select or create a workspace which would be the workspace you will be working from in the cli session

If you are joining an existing workspace, you can see and select said workspace.

### Workspace Setup and Management

A workspace is a space for collaboration between teams. All apps and integration projects must belong to a workspace. When you register or login, you are prompted to create a new workspace or join a pre-existing one.

To **create a workspace**, you use the following command:

```bash
ductape workspace --new
```

You will be asked to provide the name of the workspace you want to create.
To **change workspace**, you use the following command:

```bash
ductape workspace --select
```
