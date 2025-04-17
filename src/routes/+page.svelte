<script lang="ts">
  // import Listtodo from "./components/Listtodo.svelte";
  import Todoform from "../components/Todoform.svelte";
  type Task = {
    id: string;
    title: string;
    completed: boolean;
  };
  let tasks = $state<Task[]>([]);

  function addTask(newTask) {
    tasks.push({
      id: crypto.randomUUID(),
      title: newTask,
      completed: false,
    });
  }
</script>

<main class="h-full w-full flex flex-col *:gap-y-4 justify-center items-center">
  <Todoform {addTask} />
  {#each tasks as task}
    <p>{task.title}</p>
  {/each}
</main>
