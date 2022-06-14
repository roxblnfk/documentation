---
id: how-to-set-a-workflow-run-timeout-in-python
title: How to Workflow Run timeout in Python
sidebar_label: Workflow Run timeout
description: Workflow Run timeout
tags:
  - python
  - how-to
---

When setting [`client.start_workflow`](https://python.temporal.io/temporalio.client.client#start_workflow) or [`client.execute_workflow`](https://python.temporal.io/temporalio.client.client#execute_workflow) you can provide `run_timeout` as a parameter to set the timeout of a single Workflow run.

```python
handle = await client.start_workflow(
    "my workflow name",
    id="your-workflow-id",
    task_queue="your-task-queue",
    run_timeout=timedelta(seconds=1),
)
```