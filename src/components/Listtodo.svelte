<script>
  let { tasks } = $props();
</script>

<div class="hr-text-wrapper mb-2">
  <div class="hr-text">Tasks</div>
</div>
<section class="mt-2">
  {#each tasks as task}
    <article>
      <p>{task.title}</p>
    </article>
  {/each}
</section>

<style>
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
    color: #7a288a;
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
