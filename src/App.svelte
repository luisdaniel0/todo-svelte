<script lang="ts">
  interface Todo {
    id: string;
    name: string;
    isCompleted: boolean;
  }

  let todos = $state<Todo[]>([]);
  let newTodo = $state("");

  let title = "Todo App";

  function addTodo(todo: Todo) {
    todos = [...todos, todo];
    newTodo = "";
    console.log(todos);
  }

  function toggleComplete(e, id: string) {
    console.log(e);

    todos = todos.map((todo) => {
      if (todo.id === id) {
        return { ...todo, isCompleted: !todo.isCompleted };
      } else {
        return todo;
      }
    });
  }
</script>

<h1>{title}</h1>

{#each todos as todo (todo.id)}
  <li>{todo.name}</li>
  <input
    type="checkbox"
    id={todo.id}
    onclick={(e) => toggleComplete(e, todo.id)}
  /><label for="isCompleted">Completed</label>
{/each}

<input
  type="text"
  bind:value={newTodo}
  onkeydown={(e) =>
    e.key === "Enter" &&
    addTodo({ id: crypto.randomUUID(), name: newTodo, isCompleted: false })}
/>

<style>
  h1 {
    color: orangered;
  }
</style>
