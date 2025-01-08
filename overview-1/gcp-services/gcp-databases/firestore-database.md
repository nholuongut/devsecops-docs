---
description: Create a Firestore Database from within the DuploCoud platform.
---

# Firestore Database

Firestore is a flexible, scalable database for mobile, web, and server development from Google Cloud Platform. It's part of Firebase, a platform for developing mobile and web applications. Firestore is a NoSQL document database that simplifies storing, syncing, and querying data across multiple platforms and devices.

There are two Firestore Database modes to choose from:&#x20;

* **Firestore Native Mode** is the default mode for Firestore. It provides a richer feature set and supports more advanced querying capabilities, such as compound queries and real-time updates. Use Firestore Native for new projects and applications that require real-time updates and advanced querying features.
* **Datastore Mode** provides a subset of Firestore's features and capabilities, supports a simpler data model, and lacks support for nested subcollections. Use Datastore Mode for migrating existing applications from Google Cloud Datastore to Firestore or for applications that do not require real-time updates or complex querying capabilities.

## Creating a Firestore Database

1. From the **Tenant** list box in the upper left, select your Tenant name.
2. From the nholuongut portal, navigate to **Cloud Services** -> **Firestore Database**.
3.  Click **Add**. The **Add Firestore DB** page displays. \


    <figure><img src="../../../.gitbook/assets/firestore 1.png" alt=""><figcaption></figcaption></figure>
4. In the **Name** field, enter a name for your database.
5. From the **Type** list box, select **FIRESTORE\_NATIVE** or **DATASTORE\_MODE**.&#x20;
6. Select your location from the **Location** list box.&#x20;
7. From the **Point in Time Recovery Enablement** list box, enable or disable point in time recovery, or lock your resources pessimistically.&#x20;
8. From the **Delete Protection State list box,** enable or disable delete protection.&#x20;
9. Click **Create**. Your Firestore Database is created.&#x20;

<figure><img src="../../../.gitbook/assets/firestore 2.png" alt=""><figcaption><p>The details for the created Firestore Database.</p></figcaption></figure>



