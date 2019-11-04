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
## Problem: So much context to pass
@table[table-header table-fragment](tables/macros.csv)

+++ 
### Solution: SideCar
![Logo](https://media.giphy.com/media/l3vR9paUkdrl9GxUc/source.gif)

