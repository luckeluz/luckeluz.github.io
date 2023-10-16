---
layout: post
title: Airflow 101 - Trigger Rules
author: Lucke Luz
---

In Airflow, trigger rules are what controls whether a task will run based on the status of its dependencies.

So, let's start with the below example.

```python
from datetime import datetime

from airflow.models import DAG

with dag as DAG(
    schedule=
)
```

According to the DAG definition the task "t1" runs after the task "t2", i.e. "t1" is a dependency of "t2". In

### All success

### All failed

### All done

### One failed

### One success

### None failed

### None skipped

### All skipped

### One done

### None failed and at least one success

### Always