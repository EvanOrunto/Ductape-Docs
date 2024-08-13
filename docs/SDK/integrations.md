---
sidebar_position: 3
---

# Integrations

Integrations streamline interactions between systems, allowing seamless data exchange and process automation. Our integration framework provides robust tools for managing all aspects of integrations:

- **Integration Management:** Create, update, and initialize integrations, and retrieve details.
- **Environment Handling:** Manage integration environments, including creation, updates, and retrieval.
- **Function Operations:** Define, update, and fetch custom functions.
- **Caching:** Create, update, and access caching strategies.
- **Notification Management:** Set up, update, and fetch notifications.
- **App Management:** Add, update, and retrieve app details and configurations.
- **Feature Handling:** Create, update, and access integration features.
- **Database Operations:** Manage database configurations with create, update, and fetch functions.
- **Job Management:** Define, update, fetch, and execute integration jobs.
- **Access Tags:** Generate access tags for applications.
- **Stage Extraction:** Extract stages from input strings for workflow management.

## SDK: Working With IntegrationBuilder

To work with integrations, you'll first need to create an instance of the IntegrationBuilder. Here’s how you can set up and manage integrations:

```typescript
const integrationBuilder = await ductape.getIntegrationBuilder();
```

## SDK: Integration Management

### Create Integration

To create a new integration, use the `createIntegration` method. This function initializes an integration based on the provided data.

```typescript
await integrationManager.createIntegration({
  name: "IntegrationName",
  description: "Description of the integration",
  unique: true,
});
```

#### Options:

- name: `string` The name of the integration **\*required**.
- description: `string` A brief description **\*required**.
- unique: `string` A boolean indicating if the integration should be unique **\*optional**.

### Update Integration

To update an existing integration, use the `updateIntegration` method. This updates the integration details with the given data.

```typescript
await integrationManager.updateIntegration({
  name: "UpdatedIntegrationName",
  description: "Updated description",
});
```

### Fetch Integration

To retrieve details of the current integration, use the `fetchIntegration` method.

```typescript
const integration = integrationManager.fetchIntegration();
console.log(integration);
```

## SDK: Managing Integration Environments

With the `IntegrationBuilder`, you can effectively manage integration environments. Here’s a guide on how to use its key functions:

### Create Integration Environment

To create a new environment, use the `createEnv` function. Ensure the environment does not already exist before creating it:

```typescript
await integrationBuilder.createEnv(
  {
    env_name: "Development",
    slug: "dev",
    description: "Development Environment",
    envs: [], // List of application environments for this integration (optional)
    auth: {
      /* Authentication details here */
    }, // Authentication details for the environment (required)
  },
  true
);
```

#### Options:

- env_name: `string` The name of the environment (required).
- slug: `string` A unique identifier for the environment, usually 3 letters (required).
- description: `string` A description of the environment (optional).
- envs: List of application environments linked to this integration (optional).
- auth: Authentication details for the environment (required).

### Update Integration Environment

To update an existing environment, use the `updateEnv` function. Ensure the environment exists before updating:

```typescript
await integrationBuilder.updateEnv("dev", {
  env_name: "Updated Development",
  description: "Updated Development Environment Description",
});
```

### Fetch Integration Environment

To retrieve all environments or a specific one:

#### Fetch All Environments

```typescript
const environments = integrationBuilder.fetchEnvs();
console.log(environments);
```

#### Fetch Single Environment

```typescript
const environment = integrationBuilder.fetchEnv("dev");
console.log(environment);
```
