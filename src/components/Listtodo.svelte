<script>
  import { fade } from "svelte/transition";
  let { tasks, toggleDone, removeTask } = $props();
</script>

<section class="mt-2">
  {#each tasks as task}
    <article class="flex justify-between items-center" transition:fade>
      <label>
        <input
          type="checkbox"
          checked={task.completed}
          onchange={() => toggleDone(task)}
        />
        <span class:task-completed={task.completed}>{task.title}</span>
      </label>
      <button class=" outline" onclick={() => removeTask(task.id)}>
        Delete</button
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
  }
</style>
