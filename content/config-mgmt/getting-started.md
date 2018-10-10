---
title: "Getting Started"
date: 2018-10-09T03:15:19Z
draft: false
---

To begin, let's create an app, populate its base environment, and then add an additional environment.
You'll first need to create or log in to a Mothership account.

### Create your first app and environment
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
       "env": "base",
       "name": "Mothership sample config",
       "urls": {
           "main": "https://mothership.cloud",
           "dashboard": "https://app.mothership.cloud",
           "docs": "https://docs.mothership.cloud"
       }
   }
   ```

7. Click the "Save" button in the lower-right corner.