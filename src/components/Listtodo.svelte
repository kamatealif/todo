<script>
  let { tasks, toggleDone } = $props();
</script>

<section class="mt-2">
  {#each tasks as task}
    <article>
      <label>
        <input
          type="checkbox"
          checked={task.completed}
          onchange={() => toggleDone(task)}
        />
        <span class:task-completed={task.completed}>{task.title}</span>
      </label>
    </article>
  {/each}
</section>

<style>
  .task-completed {
    text-decoration: line-through;
  }
</style>
