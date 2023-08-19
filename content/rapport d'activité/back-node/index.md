---
title: "Back Node"
date: 2023-08-09T02:56:54+02:00
draft: false
---

On utilise [NestJS](https://docs.nestjs.com) 
pour sa stabilité et car il
utilise express que nous avons vu en cours.

Il permet de generer une documentation OpenAPI
simplement https://docs.nestjs.com/openapi/introduction

Il permet egalement de generer des CRUDs qui
s'interfacent avec OpenAPI
https://docs.nestjs.com/recipes/crud-generator

Generation d'analytics
---

On utilise les instructions ChatGPT suivantes

Setting up Firebase Analytics in a Node.js environment involves using the Firebase Admin SDK to log events and perform analytics-related tasks on the server-side. Firebase Analytics is primarily designed for use in client-side applications, but you can use the Admin SDK to work with analytics data in a Node.js environment.

Here's a step-by-step guide to setting up Firebase Analytics in a Node.js application:

1. **Create a Firebase Project:**

   If you don't have a Firebase project, create one by visiting the [Firebase Console](https://console.firebase.google.com/). Set up your project and enable Firebase Analytics.

2. **Install Firebase Admin SDK:**

   In your Node.js project, install the Firebase Admin SDK using npm or yarn:

   ```bash
   npm install firebase-admin
   ```

3. **Obtain Service Account Key:**

   In your Firebase project settings, generate a service account key:

   - Go to Project Settings > Service accounts.
   - Click "Generate new private key."
   - Save the JSON key file securely. This key is used to authenticate your Node.js application with Firebase.

4. **Initialize Firebase Admin SDK:**

   In your Node.js script, initialize the Firebase Admin SDK using the service account key:

   ```javascript
   const admin = require('firebase-admin');

   const serviceAccount = require('path/to/serviceAccountKey.json');

   admin.initializeApp({
     credential: admin.credential.cert(serviceAccount),
     databaseURL: 'https://your-project-id.firebaseio.com', // Replace with your Firebase project's database URL
   });

   // Now you can use admin to interact with Firebase services, including analytics.
   ```

5. **Logging Events:**

   With the Firebase Admin SDK initialized, you can log events to Firebase Analytics. Keep in mind that Firebase Analytics events are primarily designed for client-side applications, but you can use the Admin SDK to log events from the server-side.

   ```javascript
   const analytics = admin.analytics();

   // Log a custom event
   const event = {
     name: 'custom_event',
     params: {
       param1: 'value1',
       param2: 'value2',
     },
   };

   analytics.logEvent(event);
   ```

6. **View Analytics Data:**

   After logging events, you can view the data in the Firebase Analytics dashboard. Keep in mind that server-side events might not provide all the same insights as client-side events.

Remember that Firebase Analytics' primary use case is tracking events from client-side applications (e.g., mobile apps, web apps), and it might not be optimized for extensive server-side analytics. If you need advanced server-side analytics, you might consider using other analytics tools that are more tailored to server-side tracking.

Additionally, Firebase Analytics has certain limits and pricing considerations. Make sure to review the Firebase documentation and pricing information to understand its capabilities and potential costs.