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

## SDK: Working With IntegrationBuilder

To work with integrations, you'll first need to create an instance of the IntegrationBuilder. Here’s how you can set up and manage integrations:

```typescript
const integrationBuilder = await ductape.getIntegrationBuilder();
```

## Integration Management

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

## Managing Integration Environments

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

## Feature Operations

Manage custom functions with the IntegrationBuilder. Use these methods to create, update, fetch, and list functions.

### Create Function

To create a new custom function, use the `createFunction` method. This method initializes a function based on the provided details.

```typescript
await integrationBuilder.createFunction(
  {
    tag: "FunctionTag",
    language: "js",
    function: "function code here",
    input: [
      // Sample input details
    ],
    output: {
      // Sample output details
    },
  },
  true
);
```

### Update Functions

To update an existing function, use the `updateFunction` method. This updates the function details with the given data. The function must already exist, and the `tag` parameter specifies which function to update.

```typescript
await integrationBuilder.updateFunction("FunctionTag", {
  language: "TypeScript",
  function: "updated function code here",
  input: [
    // Updated sample input details
  ],
  output: {
    // Updated sample output details
  },
});
```

### Fecth Function

To retrieve details of a specific function, use the `fetchFunction` method. This method requires the `tag` of the function you want to fetch.

```typescript
const func = integrationBuilder.fetchFunction("FunctionTag");
console.log(func);
```

### Fetch Functions

To retrieve all functions, use the `fetchFunctions` method. This method returns a list of all functions.

```typescript
const functions = integrationBuilder.fetchFunctions();
console.log(functions);
```

## Caching

Manage caching with the `IntegrationBuilder`. Use these methods to create, update, fetch, and list caching strategies.

### Create Cache

To create a new cache, use the `createCache` method. This method initializes a cache based on the provided details.

```typescript
await integrationBuilder.createCache(
  {
    tag: "CacheTag",
    sequence_tag: "SequenceTag",
    event_tag: "EventTag",
    expiry: 3600,
    period: "years",
  },
  true
);
```

### Update Cache

To update an existing cache, use the `updateCache` method. This updates the cache details with the given data. The cache must already exist, and the `tag` parameter specifies which cache to update.

```typescript
await integrationBuilder.updateCache("CacheTag", {
  sequence_tag: "UpdatedSequenceTag",
  event_tag: "UpdatedEventTag",
  expiry: 7200,
  period: "weeks",
});
```

### Fetch Cache

To retrieve details of a specific cache, use the `fetchCache` method. This method requires the `tag` of the cache you want to fetch.

```typescript
const cache = integrationBuilder.fetchCache("CacheTag");
console.log(cache);
```

### Fetch Caches

To retrieve all caches, use the `fetchCaches` method. This method returns a list of all caches.

```typescript
const caches = integrationBuilder.fetchCaches();
console.log(caches);
```

## Notification Management

Manage notifications with the `IntegrationBuilder`. Use these methods to create, update, fetch, and list notifications.

### Create Notification

To create a new notification, use the `createNotification` method. This method initializes a notification based on the provided details.

```typescript
await integrationBuilder.createNotification(
  {
    tag: "NotificationTag",
  },
  true
);
```

### Update Notification

To update an existing notification, use the `updateNotification` method. This updates the notification details with the given data. The notification must already exist, and the `tag` parameter specifies which notification to update.

```typescript
await integrationBuilder.updateNotification("NotificationTag", {
  tag: "UpdatedNotificationTag",
});
```

### Fetch Notification

To retrieve details of a specific notification, use the `fetchNotification` method. This method requires the `tag` of the notification you want to fetch.

```typescript
const notification = integrationBuilder.fetchNotification("NotificationTag");
console.log(notification);
```

### Fetch Notifications

To retrieve all notifications, use the `fetchNotifications` method. This method returns a list of all notifications.

```typescript
const notifications = integrationBuilder.fetchNotifications();
console.log(notifications);
```

## App Management

Manage applications with the `IntegrationBuilder`. Use these methods to add, update, and fetch apps.

### Add App

To add a new app, use the `addApp` method. This method initializes an app based on the provided details.

```typescript
await integrationBuilder.addApp(
  {
    access_tag: "AppTag",
    envs: [
      {
        app_env_slug: "AppEnv",
        integration_env_slug: "IntegrationEnv",
        variables: [{ key: "exampleKey", value: "exampleValue" }],
        auth: {
          auth_tag: "authTag",
          data: "data details",
        },
      },
    ],
  },
  true
);
```

### Update App

To update an existing app, use the `updateApp` method. This updates the app details with the given data. The app must already exist, and the `access_tag` parameter specifies which app to update.

```typescript
await integrationBuilder.updateApp("AppTag", {
  envs: [
    {
      app_env_slug: "UpdatedAppEnv",
      integration_env_slug: "UpdatedIntegrationEnv",
      variables: [{ key: "updatedKey", value: "updatedValue" }],
      auth: {
        /* Updated Authentication details */
      },
    },
  ],
});
```

### Fetch App

To retrieve details of a specific app, use the `fetchApp` method. This method requires the `access_tag` of the app you want to fetch.

```typescript
const app = integrationBuilder.fetchApp("AppTag");
console.log(app);
```

### Fetch Apps

To retrieve all apps, use the `fetchApps` method. This method returns a list of all apps.

```typescript
const apps = integrationBuilder.fetchApps();
console.log(apps);
```

## Feature Management

Manage features within your integration system using these methods to create, update, and fetch features.

### Create Feature

To add a new feature, use the `createFeature` method. This method initializes a feature based on the provided details.

```typescript
await integrationBuilder.createFeature(
  {
    tag: "FeatureTag",
    language: "js",
    function: "featureFunction",
    input: [
      {
        sampleValue: "value",
        description: "Sample input",
        required: true,
        maxLength: 100,
        minLength: 1,
        type: "string",
      },
    ],
    output: {
      type: "string",
      output_keys: [
        {
          sampleValue: "outputValue",
          description: "Output description",
          type: "string",
        },
      ],
    },
  },
  true
);
```

### Update Feature

To update an existing feature, use the `updateFeature` method. This method updates the feature details with the given data. The feature must already exist, and the `tag` parameter specifies which feature to update.

```typescript
await integrationBuilder.updateFeature("FeatureTag", {
  function: "updatedFeatureFunction",
  input: [
    {
      sampleValue: "updatedValue",
      description: "Updated input",
      required: false,
      maxLength: 150,
      minLength: 5,
      type: "string",
    },
  ],
  output: {
    type: "string",
    output_keys: [
      {
        sampleValue: "updatedOutputValue",
        description: "Updated output description",
        type: "string",
      },
    ],
  },
});
```

### Fetch Feature

To retrieve details of a specific feature, use the `fetchFeature` method. This method requires the `tag` of the feature you want to fetch.

```typescript
const feature = integrationBuilder.fetchFeature("FeatureTag");
console.log(feature);
```

### Fetch Features

To retrieve all features, use the `fetchFeatures` method. This method returns a list of all features.

```typescript
const features = integrationBuilder.fetchFeatures();
console.log(features);
```

## Database Management

Manage databases within your integration system using these methods to create, update, and fetch database records.

### Create Database

To add a new database, use the `createDatabase` method. This method initializes a database record based on the provided details.

```typescript
await integrationBuilder.createDatabase(
  {
    tag: "DatabaseTag",
  },
  true
);
```

### Update Database

To update an existing database record, use the `updateDatabase` method. This method updates the database record with the given data. The database must already exist, and the `tag` parameter specifies which database to update.

```typescript
await integrationBuilder.updateDatabase("DatabaseTag", {
  tag: "UpdatedDatabaseTag",
});
```

### Fetch Database

To retrieve details of a specific database record, use the `fetchDatabase` method. This method requires the `tag` of the database you want to fetch.

```typescript
const database = integrationBuilder.fetchDatabase("DatabaseTag");
console.log(database);
```

### Fetch Databases

To retrieve all database records, use the `fetchDatabases` method. This method returns a list of all databases.

```typescript
const databases = integrationBuilder.fetchDatabases();
console.log(databases);
```

## Job Management

Manage job records within your integration system using these methods to create, update, fetch, and run jobs.

### Create Job

To add a new job, use the `createJob` method. This method initializes a job record based on the provided details.

```typescript
await integrationBuilder.createJob(
  {
    tag: "JobTag",
  },
  true
);
```

### Update Job

To update an existing job record, use the `updateJob` method. This method updates the job record with the given data. The job must already exist, and the `tag` parameter specifies which job to update.

```typescript
await integrationBuilder.updateJob("JobTag", {
  tag: "UpdatedJobTag",
});
```

### Fetch Job

To retrieve details of a specific job record, use the `fetchJob` method. This method requires the `tag` of the job you want to fetch.

```typescript
const job = integrationBuilder.fetchJob("JobTag");
console.log(job);
```

### Fetch Jobs

To retrieve all job records, use the `fetchJobs` method. This method returns a list of all jobs.

```typescript
const jobs = integrationBuilder.fetchJobs();
console.log(jobs);
```

The `IntegrationBuilder` SDK streamlines managing your integration components with methods for creating, updating, fetching, and running records. These tools ensure your system remains organized and up-to-date, supporting efficient integration management.
