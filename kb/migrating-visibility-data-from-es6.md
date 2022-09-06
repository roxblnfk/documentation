---
slug: migrate-visibility-data-from-es6
title: Migrate visibility data from ES6
tags:
  - kb-article
date: 2022-29-08T00:00:00Z
---

Support for Elasticsearch v7 (ES7) was added to the 1.7.0. Temporal Server update.
This introduces several breaking changes, including the removal of mapping types.
These changes make ES6 incompatible with ES7.

There are several ways to update your Temporal Server to support ES7.
Upgrade ES6 to ES7, and then use one of the methods below to update your server.

Visibility data can be migrated through reindexing.
After updating Elasticsearch, run a reindexing process to move data from ES6 to ES7.

:::note
If you are using AWS Elasticsearch, only upgrade to version 7.7.
:::

## Fresh install

1. Install the latest version of Temporal Server.

2. Install ES7 as shown in the Elasticsearch documentation.

3. To set the Elasticsearch version in Temporal server:

- Iet the ES version in the server's static config file:

  ```
  persistence:
    datastores:
      es-visibility:
        elasticsearch:
          version: "v7"
  ```

- Set ES_VERSION to v7 in the pre-build docker image.

## Upgrade with temporary shutdown

1. Shut down the Temporal Cluster.

2. Upgrade ES6 to ES7 according to Elasticsearch's documentation.

## Rolling Upgrade

1. Update the Server to the latest release.

2. Add the following to the dynamic config:

   ```
   history.visibilityProcessorEnabled:
     - value: false
   ```

3. Restart the Server.
   Workflow visibility information won't be updated.

4. Upgrade ES6 to ES7 following steps from the Elasticsearch documentation.

5. Start ES7.
   Visibility read queries will temporarily generate errors.
   Write queries are blocked because the processor is disabled.

6. Switch to ES7 in the Server's static config:

   ```
   persistence:
     datastores:
       es-visibility:
         elasticsearch:
           version: "v7"
   ```

7. Set ES_VERSION env to v7 if you are using pre-build docker image.

8. Remove this from the dynamic config:

   ```
   history.visibilityProcessorEnabled:
     - value: false
   ```

9. Restart the Server one more time.