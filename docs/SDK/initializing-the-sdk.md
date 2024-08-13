---
sidebar_position: 1
---

# Getting Started

To work the SDK, you need to initialize the ductape instance. To initialize the ductape instance. you need to fetch the user workspace credentials on the CLI using the get user credentials command earlier shared.

```typescript
import Ductape from "@ductape";
const user_id = process.env.DUCTAPE_USER_ID;
const workspace_id = process.env.DUCTAPE_WORKSPACE_ID;
const private_key = process.env.DUCTAPE_PRIVATE_KEY;
const ductape = new Ductape({ user_id, workspace_id, private_key });
```
A more indepth exploration of the SDK can be found here: https://link-to-sdk-docs.com

