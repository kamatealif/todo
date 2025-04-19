<script>
  let { tasks, toggleDone, removeTask } = $props();
</script>

<section class="mt-2">
  {#each tasks as task, index}
    <article class="flex justify-between items-center">
      <label>
        <input
          type="checkbox"
          checked={task.completed}
          onchange={() => toggleDone(task)}
        />
        <span class:task-completed={task.completed}>{task.title}</span>
      </label>
      <button class=" outline" onclick={() => removeTask(index)}
        ><svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="lucide lucide-trash2-icon lucide-trash-2"
          ><path d="M3 6h18" /><path
            d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"
          /><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2" /><line
            x1="10"
            x2="10"
            y1="11"
            y2="17"
          /><line x1="14" x2="14" y1="11" y2="17" /></svg
        > Delete</button
      >
    </article>
  {/each}
</section>

<style>
  .task-completed {
    text-decoration: line-through;
  }
  button {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.3rem;
    background: transparent;
    border: 1px solid red;
    border-radius: 5px;
    color: red;
  }
</style>
