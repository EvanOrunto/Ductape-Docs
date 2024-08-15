---
sidebar_position: 1
---

# Getting Started

To work the SDK, you need to initialise the ductape instance. To initialise the ductape instance, you first need to fetch the user workspace credentials.
On the CLI, enter the following command:

```bash
ductape workspace --credentials
```

The user credentials includes the following fields:

- workspace_id
- user_id
- private_key

To initialise the ductape instance in your code, you should run the following:

```typescript
import Ductape from ‘ductape';
const user_id = process.env.DUCTAPE_USER_ID;
const workspace_id = process.env.DUCTAPE_WORKSPACE_ID;
const private_key = process.env.DUCTAPE_PRIVATE_KEY;
const ductape = new Ductape({ user_id, workspace_id, private_key });
```

The above implementation assumes that you have set your workspace_id, user_id and private_key as DUCTAPE_WORKSPACE_ID, DUCTAPE_USER_ID and DUCTAPE_PRIVATE_KEY respectively in your env file.




