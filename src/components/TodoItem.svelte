<script lang="ts">
  let { todo, toggleComplete, deleteTodo } = $props();
</script>

<ul>
  <li class:isCompleted={todo.isCompleted}>{todo.name}</li>
  <input
    type="checkbox"
    id={todo.id}
    onclick={() => toggleComplete(todo.id)}
  /><label for="isCompleted">Completed</label>
  <button onclick={() => deleteTodo(todo.id)}>Delete</button>
</ul>

<style>
  .isCompleted {
    text-decoration: line-through;
  }

  ul {
    list-style: none;
  }
</style>
