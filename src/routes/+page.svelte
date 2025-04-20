<script lang="ts">
  import Listtodo from "../components/Listtodo.svelte";
  import Todoform from "../components/Todoform.svelte";
  type Task = {
    id: string;
    title: string;
    completed: boolean;
  };
  let tasks = $state<Task[]>([]);

  let currentFilter = $state("all");

  let filteredTask = $derived.by(() => {
    switch (currentFilter) {
      case "all":
        return tasks;
      case "completed":
        return tasks.filter((task) => task.completed);
      case "todo":
        return tasks.filter((task) => !task.completed);
    }
    return tasks;
  });

  let totalTasks = $derived(
    tasks.reduce((total, task) => total + Number(task.completed), 0)
  );
  function addTask(newTask) {
    tasks.push({
      id: crypto.randomUUID(),
      title: newTask,
      completed: false,
    });
  }

  function toggleDone(task) {
    task.completed = !task.completed;
  }

  function removeTask(id) {
    const index = tasks.findIndex((task) => task.id === id);
    tasks.splice(index, 1);
  }
</script>

<main
  class="h-full max-w-[680px] mt-1 mx-auto flex flex-col *:gap-y-4 justify-center items-center"
>
  <Todoform {addTask} />
  <div class="hr-text-wrapper mb-2">
    <div class="hr-text">Tasks</div>
  </div>
  {#if tasks.length > 0}
    <p>{totalTasks} / {tasks.length} Tasks Completed</p>
  {:else}
    <p>Add Tasak to Get STarted</p>
  {/if}

  {#if tasks.length > 0}
    <div class="flex justify-end mb-1 gap-x-1">
      <button
        onclick={() => (currentFilter = "all")}
        class:contrast={currentFilter === "all"}>All Task</button
      >
      <button
        onclick={() => (currentFilter = "todo")}
        class:contrast={currentFilter === "todo"}>Todo</button
      >
      <button
        onclick={() => (currentFilter = "completed")}
        class:contrast={currentFilter === "completed"}>Completed</button
      >
    </div>
  {/if}
  <Listtodo tasks={filteredTask} {toggleDone} {removeTask} />
</main>

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
