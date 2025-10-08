--8<-- "snippets/2-bug-special-characters.js"

!!! note "The Bug 'Special characters'"
    Level: Beginner

## Add a new Task

Open the TODO App and add a Task with an exclamation mark `!`

- Add a task with an exclamation mark! or a special character for that matter, like this:

![TODO App](img/todo_app_exclamation.png)

- Now type ENTER to add the task

![TODO App](img/todo_app_exclamation2.png)

- What happened? As you can see the signs are being removed. Why?

Let's continue with the bug hunting again! Now, let's assume we are new developers in the TODO app company. How difficult would it be to find the bug? To know where is the app running? which pod is delivering the requests? which namespace and line of code? Well, not with Dynatrace! We already learned how easy it was to find the TODO app within the Kubernetes App and from there we opened the traces in the Distributed Tracing app, so let's go there.

!!! example "Fix the bug 🪲🛠️"
    Go back to your Codespace and find the source code for the `TodoController`. It should be under the following path: `app/src/main/java/com/dynatrace/todoapp/TodoController.java`. Once you apply the fix, run the following commands:

    ```bash
    cd /workspaces/enablement-live-debugger-bug-hunting
    chmod +x redeploy-todoapp.sh
    ./redeploy-todoapp.sh
    ```
<br>
<details>
<summary>💡 Hint</summary>

Before
```javascript
String todoTitle = newTodoRecord.getTitle().replaceAll("[^a-zA-Z0-9\\s]+", "");
newTodoRecord.setTitle(todoTitle);
```

After
```javascript
//String todoTitle = newTodoRecord.getTitle().replaceAll("[^a-zA-Z0-9\\s]+", "");
String todoTitle = newTodoRecord.getTitle();
newTodoRecord.setTitle(todoTitle);
```
</details> 
<br>

<div class="grid cards" markdown>
- [Click here to Continue the quest:octicons-arrow-right-24:](2-bug-hunt-via-tracing.md)
</div>
