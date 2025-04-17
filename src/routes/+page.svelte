<script lang="ts">
  import Listtodo from "../components/Listtodo.svelte";
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

<main
  class="h-full max-w-[680px] mt-1 mx-auto flex flex-col *:gap-y-4 justify-center items-center"
>
  <Todoform {addTask} />
  <Listtodo {tasks} />
</main>
