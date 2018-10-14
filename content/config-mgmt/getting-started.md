---
title: "Getting Started"
date: 2018-10-09T03:15:19Z
draft: false
---

To begin, let's create an app, populate its base environment, and then add an additional environment.
You'll first need to create or log in to a Mothership account.

### Create your first app and base config
1. From the Mothership dashboard, select "New app" from the top right.
2. Next, provide a unique name for the app. You can also add a description to provide more context
   about what the app is for.
3. Click the "Create" button and your app will be created and added to the list of apps.
4. Click on the newly created app from the list. The list of available environments is displayed.
   You'll notice that a **base** environment has already been created.
5. Click on the "base" environment to edit it. The following panel should include a code editor
   with an empty JSON object.
6. Replace the contents of the editor with the following snippet:

    ```
    {
        "name": "Mothership sample config",
        "urls": {
            "main": "https://mothership.cloud",
            "dashboard": "https://app.mothership.cloud",
            "docs": "https://docs.mothership.cloud"
        }
    }
    ```

7. Click the "Save" button in the lower-right corner.

### Create an environment config
Now that we have our app and base config, we still need to create our first real environment. In this
scenario, our base config has what we might think of as "production" values in it. If they aren't
overridden by another environment, that's what the client will receive.

Let's now create a config for a staging environment.

1. Open the app created above if it's not already open so that the list of environments is displayed.
   (The list should show just the `base` environment.)
2. Click the "Add environment" button
3. Provide a name for the environment (e.g. `staging`) and click "Create."
4. Click on the newly created environment in the list and the editor should open.
   You'll see that Mothership initializes the editor with a JSON object containing
   an `env` field set to the name of the environment. This can be useful for debugging
   purposes or for use with template pointers.
5. Update the config so that the result looks something like this:

    ```
    {
        "env": "staging",
        "urls": {
            "dashboard": "https://app.dev.mothership.cloud"
        }
    }
    ```
    
6. Click the "Save" button in the lower-right corner.

Now we're ready to connect a client and view the result.

### Connecting a client
Mothership supports a growing number of languages and frameworks. To view a
complete list of official clients and those developed by the community, see
the [Client SDK docs](/sdks).

### Using template pointers