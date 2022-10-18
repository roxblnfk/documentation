---
id: skip-time-skip-automatically
title: Skip Time automatically
description: The test server is included in most SDKs is an in-memory implementation of Temporal Server that supports skipping time.
sidebar_label: Automatic method
tags:
  - guide-context
---

Learn to Time Skip automatically in the SDK of your choice. Start a test server process that automatically skips time as needed. For example, in the time skipping mode, timers, which include sleeps and conditional timeouts, are fast-forwarded except when Activities are running.
