---
sidebar_position: 2
---

# Apps

Apps can be managed by both the CLI and SDK.

- Create App
- Update App Details
- Import App Documentation
- Update App Actions
- Setting Up App Environments
- Add Action Data Validation
- Add App Variables
- Add App Constants
- Add App Authentication
- Add App Events

## Working With AppBuilder

You need to create a builder instance for each app you would be building, in this documentation, we will be working with a builder for an app called Appify.

```typescript
const appify = await ductape.getAppBuilder();
```

You can access further information about the appBuilder [here](https://docs.io/)

## Create App

You can create an app with the appBuilder [createApp](http://createappdocs.io/)

```typescript
await appify.createApp({
  app_name: "Appify",
  description: "Api for Creating Apps",
});
```

## Manage App Environments

The appBuilder class provides us the opportunity to create, read, update and delete app environments. App environments are the various environments your app runs in

- Create App Environments
- Fetch App Environments
- Fetch Single App Environment
- Update App Environment
- Delete App Environment

### Create Environment

To create the app environment, use the [createEnv](http://http.appenv.io/) function of the appBuilder class

```typescript
import { DataFormats } from ‘@ductape/types/enums’

await appify.createEnv({
   env_name: 'develop',
   slug: 'dev',
   description: 'Development Environment',
   whitelist: false,
   active: true,
   base_url: 'https://dev.appify.io',
   request_type: DataFormats.JSON
})
```

#### Options:

- env_name: `string`, the name of the new environment to be added \*\*\*required\_
- slug: `string`, a 3 letter slug that is a short version of the env name _\*\*required_
- description: `string`, a description of the app environment _\*\*optional_
- whitelist: `boolean`, do people who integrate with the env require to be whitelisted _\*\*optional_
- active: `boolean`, is the env active for third party integrations? _\*\*optional_
- base_url: `string`, the environment base url \*\*\*optional\_
- request_type: `enum`, JSON \*\*\*optional\_

### Fetch Environment

Fetch app environments with the `fetchEnvs` function

```typescript
const sandbox = appify.fetchEnv(‘snd’);
console.log(sandbox);
```

### Update Environment

Update app environment with updateEnv function

```typescript
const slug = ‘dev’;
await appify.updateEnv(slug, {base_url: ‘http://dev.app-iffy.io’});
```

#### Options:

- env_name: `string`, the name of the new environment to be added \*\*\*optional\_
- description: `string`, a description of the app environment _\*\*optional_
- whitelist: `boolean`, do people who integrate with the env require to be whitelisted _\*\*optional_
- active: `boolean`, is the env active for third party integrations? _\*\*optional_
- base_url: `string`, the environment base url \*\*\*optional\_
- request_type: `enum`, JSON \*\*\*optional\_

## App Actions

An app action is an individual actions that can be performed by an application e.g login, signup, process payment etc. They following functions can be performed with app actions

- Import Actions from Docs
- Fetch App Actions
- Fetch Single App Action
- Update Action
- Update Action Data Validation

### Importing Actions

You need to create an instance of the ductape [actionImporter](http://iosos.io/) class from the ductape instance which provides functionality around importing actions into apps

```typescript
const importer = await ductape.getActionImporter();

const filePath = ‘/__dirname__/app.postman.ts’;

const data = fs.readFileSync(filePath,’utf8’);
const jsonData = JSON.parse(data);

importer.importPostmanV21(jsonData, false, app_id);
```

Currently ductape only works with the postman documentation v2.1 format. With postman v2 and OpenApi formats being in the works

You can access further information about the actionImporter [here](https://docs.io/)

### Fetch Actions

To fetch all app actions you can use the [fetchActions](https://i.o/) function as below

```typescript
const actions = appify.fetchActions();
```

### Fetch Single Action

To fetch a single action you can use the [fetchAction](https://i.o/) function as below

```typescript
const action_tag = actions[0].tag;
const action = appify.fetchAction(action_tag);
```

### Update Action

To update an action you can use the [updateAction](https://i.o/) function as below

```typescript
import {InputTypes} from ‘ductape/types/enums’;
const action_tag = actions[0].tag;
appify.updateAction(action_tag, {
    method: “POST”,
    name: “Process Payment”,
    base_url: ‘https://api.appify.dev’
    request_type: DataFormats.JSON,
    description: “process payments for appify clients”,
    resource: “/:user_id/payment?from_username=jackie&to_username=james”,
    body: {
        sample: {
    from_amount: 300,
            to_amount: 296,
        },
        type: InputTypes.JSON
    },
    headers: {
        authorization: ‘Bearer 16172728hsbsbsbsgwgy171y1’
    }
    responses: [{
        name: ‘Successfully Sent’,
        tag: ‘successful_payment’,
        success: true,
        status_code: 200,
        response_format: DataFormats.JSON,
        is_status_code_success: true,
        body: {
            id: ‘71882929101011919’,
            from_username: ‘jackie’,
            to_username: ‘james’,
            from_amount: 300,
            to_amount: ‘296’
        }
    }]
});
```

## App Auth

You can setup authentication and authorization flows

- Create Auth
- Update Auth
- Fetch Auth
- Fetch One Auth

### Create Auth

```typescript
import { AppAuthSetupTypes, TokenPeriods } from ‘@ductape/types/enums’;

appify.createAuth({
	name: “User Login”,
	tag: “login_auth”,
	setup_type: AppAuthSetupTypes.CREDENTIALS,
	expiry: 7,
	period: TokenPeriods.HOURS,
	action_tag: “login”
});
```

### Update Auth

```typescript
const auth_tag = “login_auth”;

appify.updateAuth(auth_tag, {
expiry: 1,
period: TokenPeriods.DAYS
});
```

### Fetch Auths

```typescript
const auths = appify.fetchAuths();
```

### Fetch One Auth

```typescript
const auth_tag = “login_auth”;
Const auth = appify.fetchAuth(auth_tag);
```

## SDK: Managing App Constants

Constants are fixed values used throughout your application. The `AppBuilderService` provides methods to create, update, and retrieve these constants.

### Creating Constant

Add a new constant with the `createConstant` function.

```typescript
await appify.createConstant({
  key: "MY_CONSTANT_KEY",
  value: "ConstantValue",
  type: "string", // or another valid type from DataTypes
  description: "A constant used for ...",
});
```

#### Options:

- key: `string`, unique identifier. **\*required**
- value: `string`, the constant's value. **\*required**
- type: `string`, data type (must be valid). **\*required**
- description (string, optional): Description of the constant. **\*optional**

### Update Constant

Use `updateConstant` to modify an existing constant. Provide the key and the new data.

```typescript
await appify.updateConstant("MY_CONSTANT_KEY", {
  value: "UpdatedValue",
  description: "Updated description",
});
```

### Fetch All Constants

Retrieve a list of all constants using `fetchConstants`.

```typescript
const constants = await appify.fetchConstants();
console.log(constants);
```

### Fetch a Single Constant

Get details of a specific constant with `fetchConstant`.

```typescript
const constant = await appify.fetchConstant("MY_CONSTANT_KEY");
console.log(constant);
```

## Managing App Variables

App variables are dynamic values used within your application. With the `AppBuilderService`, you can create, update, and manage these variables efficiently.

### Create a Variable

Use the `createVariable` function to add a new variable.

```typescript
await appify.createVariable({
  key: "MY_VARIABLE_KEY",
  type: "string", // or another valid type from DataTypes
  required: true,
  description: "A variable used for ...",
  minlength: 1,
  maxlength: 100,
});
```

#### Options:

- key: `string`, unique identifier. **\*required**
- type: `string`, data type (must be valid). **\*required**
- required: `boolean`, whether the variable is mandatory. **\*required**
- description: `string`, description of the variable. **\*required**
- minlength: `number`, minimum length (for string types). **\*required**
- maxlength: `number`, maximum length (for string types). **\*required**

### Updating a Variable

To modify an existing variable, use the `updateVariable` function. Provide the key and the new data.

```typescript
await appify.updateVariable("MY_VARIABLE_KEY", {
  description: "Updated description",
  maxlength: 200,
});
```

### Fetch All Variable

Retrieve a list of all variables with the `fetchVariables` function.

```typescript
const variables = await appify.fetchVariables();
console.log(variables);
```

### Fetch a Single Variable

Get details of a specific variable by its key using `fetchVariable`.

```typescript
const variable = await appify.fetchVariable("MY_VARIABLE_KEY");
console.log(variable);
```

## Managing App Events

Events are critical for handling various actions and triggers within your application. With the `AppBuilderService`, you can create, update, and manage events effectively.

### Create an Event

Use the `createEvent` function to add a new event to your app.

```typescript
await appify.createEvent({
  name: "User Signup",
  tag: "user_signup",
  setup_type: "webhook",
  description: "Triggered when a new user signs up",
  resource: "https://example.com/webhook",
  method: "POST",
  request: {
    /* request sample data */
  },
  response: {
    /* response sample data */
  },
  body: {
    /* event body sample data */
  },
});
```

#### Options:

- \_id: `string` Unique identifier of the event. **\*optional**
- name: `string` The name of the event. **\*required**
- tag: `string` A unique tag for the event. **\*required**
- setup_type: `string` Type of setup for the event, must be one of the predefined AppEventSetupTypes. **\*required**
- description: `string` Description of the event. **\*required**
- resource: `string` URL path for the event resource. Must match urlPathPattern. **\*required**
- method: `string` HTTP method for the event, must be one of the predefined HttpMethods. **\*required**
- request: `object` Schema for request data, validated against requestSampleSchema. **\*required**
- response: `object` Schema for response data, validated against responseSampleSchema. **\*required**
- body: `object` Schema for the event body, validated against sampleSchema. **\*required**

### Updating an Event

Modify an existing event using the `updateEvent` function. Provide the tag and new data.

```typescript
await appify.updateEvent("user_signup", {
  description: "Updated description for user signup",
  resource: "https://example.com/updated-webhook",
});
```

### Fetch All Events

Retrieve a list of all events with the `fetchEvents` function.

```typescript
const events = await appify.fetchEvents();
console.log(events);
```

### Fetch a Single Event

Get details of a specific event by its tag using `fetchEvent`.

```typescript
const event = await appify.fetchEvent("user_signup");
console.log(event);
```
