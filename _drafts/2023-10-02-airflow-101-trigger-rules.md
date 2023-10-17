---
layout: post
title: Airflow 101 - Trigger Rules
author: Lucke Luz
---

**Note:** The code examples of this article with instructions to execute them are available at the linked 
[Github Repo](https://github.com/luckeluz/airflow-101).

## Task dependencies - the basics
Before diving into trigger rules, it's important to understand Airflow task dependencies.

So, let's start with the below example.

```python
...
```
*example_1_task_dependencies.py*

By running this DAG, we get this in Airflow UI.

*IMG Starting example - Running in Airflow UI*

According to the DAG definition the task "t1" runs after the task "t2", i.e. "t1" is a dependency of "t2". In this 
scenario, "t2" will only run if "t1" succeeds. In our example "t1" will always succeed, hence "t2" will always run.

Alright, let's now check that "t2" will really not run if "t1" fails. To achieve that, let's alter slightly our DAG's 
code.

```python
...
```
*example_2_failing_t1.py

We run the DAG and voilà... now "t2" didn't run and its state is *upstream_failed* because "t1" which is upstream of 
"t2" failed.

*IMG t2 failed - Airflow UI*

## How to assign trigger rules to tasks

So, now that we know how dependencies between DAGs, let's see how to manage them using trigger rules. A task's 
trigger rule will determine when the task will run based on its dependencies status.

To assign a trigger rule to a task we have to pass the parameter *trigger_rule* to the task decorator as shown in 
the example below.

```python
...
```
*example_3_assigning_trigger_rule.py

## Exploring each trigger rule

### All success

As you might have guessed, the trigger rule *all_success* is the default trigger rule in Airflow. In the previous 
examples, we showed how it works.

**Definition:** If all dependencies succeed, then run the task, else don't run.

### All failed

**Definition:** If all dependencies fail, then run the task, else don't run.

```python
...
```
*example_4_trigger_rule_all_failed.py*

### All done

### One failed

### One success

### None failed

### None skipped

### All skipped

### One done

### None failed and at least one success

### Always

## Mixing things up - complex use cases