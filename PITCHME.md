![](images/ork8.png)

---?image=images/tasks.png&size=auto 100%

---?image=images/dependencies.png&size=auto 100%

---?image=images/flow.png&size=auto 100%

---?image=images/execution-external.png&size=auto 100%

---?image=images/context-problem.png&size=auto 100%

+++

## Solutions

Macros:
```bash
curl -X POST http://localhost:9000/tasks/trigger
{
 "taskId": 2, 
 "parentTaskId": __parentTaskId__ , 
 "parentTaskExecutionId":  __parentTaskExecutionId__
}
```

```bash
curl -X POST http://localhost:9000/tasks/trigger
{
 "taskId": 2, 
 "parentTaskId": 1 , 
 "parentTaskExecutionId": 101
}
```

+++
@snap[north span-100]

## Problem: So much context to pass

Variable | Description
-- | --
{{ execution_date }} | the execution_date (pendulum.Pendulum)
{{ prev_execution_date }} | the previous execution date (if available) (pendulum.Pendulum)
{{ prev_execution_date_success }} | execution date from prior succesful dag run (if available) (pendulum.Pendulum)
{{ prev_start_date_success }} | start date from prior successful dag run (if available) (pendulum.Pendulum)
{{ next_execution_date }} | the next execution date (pendulum.Pendulum)
{{ dag }} | the DAG object
{{ macros }} | a reference to the macros package, described below
{{ task_instance }} | the task_instance object
{{ conf }} | the full configuration object located at airflow.configuration.conf which represents the content of your airflow.cfg
{{ run_id }} | the run_id of the current DAG run
{{ dag_run }} | a reference to the DagRun object

+++ 
### Solution: SideCar
![Logo](https://media.giphy.com/media/l3vR9paUkdrl9GxUc/source.gif)

