---
id: how-to-handle-a-signal-in-a-workflow-in-python
title: How to handle a Signal in a Workflow
sidebar_label: Handle a Signal in a Workflow
description: Handle a Signal in a Workflow
tags:
  - developer-guide
  - sdk
  - python
---

To send a Signal from to the Workflow, use the [`signal`](https://python.temporal.io/temporalio.client.workflowhandle#signal) method from the [`WorkflowHandle`](https://python.temporal.io/temporalio.client.workflowhandle) class.

This will signal for `run_id` if present.

```python
await handle.signal("some signal")
```