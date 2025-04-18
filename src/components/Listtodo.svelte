<script>
  let { tasks, toggleDone } = $props();
</script>

<div class="hr-text-wrapper mb-2">
  <div class="hr-text">Tasks</div>
</div>
<section class="mt-2">
  {#each tasks as task}
    <article>
      <label>
        <input
          type="checkbox"
          checked={task.completed}
          onchange={() => toggleDone(task)}
        />
        <span class:done={task.completed}>{task.title}</span>
      </label>
    </article>
  {/each}
</section>

<style>
  .done {
    text-decoration: line-trhough;
  }
  .hr-text-wrapper {
    position: relative;
    width: 100%;
    text-align: center;
    margin: 20px 0;
  }

  .hr-text {
    position: relative;
    display: inline-block;
    padding: 0 10px;
    font-size: 18px;
    color: #e1d2e4;
    background-color: #2d2d2d;
  }

  .hr-text-wrapper::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 0;
    width: 100%;
    height: 1px;
    background-color: #ffffff;
    transform: translateY(-50%);
    z-index: -1;
  }
</style>
