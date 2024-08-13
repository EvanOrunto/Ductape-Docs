---
sidebar_position: 3
---

# Workpsaces

## Workspace Access

You can invite other users to collaborate with you in your workspace via the access command

- Create New Access (Owner Only)
- Fetch All Access (Owner Only)
- Revoke Access (Owner Only)

### CLI: Create Access (Owner Only)

```bash
ductape access --new
```

You would then be asked to provide the email address of the person to be invited, alongside the access level you want to grant

### CLI: Fetch Access (Owner Only)

```bash
ductape access --list
```

You would be provided a list of your teammates and their access levels

### CLI: Revoke Access (Owner Only)

```bash
ductape access --revoke
```

## Workspace Environment

The workspace has default environments that get created by default, each time a new app or integration project gets created. The cli provides you tools to update and manage these environments.

### CLI: Create Default Env

```bash
ductape workspace --env --new
```

You would then be asked to provide the email address of the person to be invited, alongside the access level you want to grant

### CLI: Update Default Env

```bash
ductape workspace --env --new
```

## Workspace Management

A workspace is a space for collaboration between teams. All apps and integration projects must belong to a workspace

- Fetch Current Workspace Details
- Change workspace
- Create a new workspace
- Update Workspace Details
- Fetch User Workspace Credentials

### CLI: Fetch Workspace Details

```bash
ductape workspace --info
```

### CLI: Change Workspace

```bash
ductape workspace --select
```

### CLI: Create New Workspace

```bash
ductape workspace --new
```

You would then be asked to provide the name of the workspace being created

### CLI: Fetch User Workspace Credentials

```bash
ductape workspace --credentials
```

The user credential includes the following fields:

- workspace_id
- user_id
- private_key

These user credentials as a trifecta are unique credentials that grant a user access to the workspace resources. They are to be treated carefully.
