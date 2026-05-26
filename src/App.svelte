<script lang="ts">
  interface Todo {
    id: string;
    name: string;
    isCompleted: boolean;
  }

  let todos: Todo[] = [];
  let newTodo: string = "";
  let title = "Todo App";

  function addTodo(todo: Todo) {
    todos = [...todos, todo];
  }
</script>

<h1>{title}</h1>

<input
  type="text"
  bind:value={newTodo}
  onkeydown={(e) =>
    e.key === "Enter" &&
    addTodo({ id: crypto.randomUUID(), name: newTodo, isCompleted: false })}
/>
<p>{todos}</p>

<style>
  h1 {
    color: orangered;
  }
</style>
