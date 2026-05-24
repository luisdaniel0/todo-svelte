<script lang="ts">
  import TodoItem from "./components/TodoItem.svelte";

  interface Todo {
    id: string;
    name: string;
    isCompleted: boolean;
  }

  let todos = $state<Todo[]>([]);
  let newTodo = $state("");

  const title = "Todo App";

  function addTodo(todo: Todo) {
    todos = [...todos, todo];
    newTodo = "";
  }

  function toggleComplete(id: string) {
    todos = todos.map((todo) => {
      if (todo.id === id) {
        return { ...todo, isCompleted: !todo.isCompleted };
      } else {
        return todo;
      }
    });
  }

  function deleteTodo(id: string) {
    todos = todos.filter((todo) => todo.id !== id);
  }
</script>

<h1>{title}</h1>

<div class="todos">
  {#each todos as todo (todo.id)}
    <TodoItem {todo} {toggleComplete} {deleteTodo} />
  {/each}
</div>

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
