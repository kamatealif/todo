<script>
  let newTask = $state("");
  let { addTask } = $props();

  function addTodo(event) {
    event.preventDefault();
    if (newTask) {
      addTask(newTask);
      newTask = "";
    }
  }
</script>

<form
  onsubmit={addTodo}
  class="flex justify-center items-start flex-col gap-y-1"
>
  <label
    for="todoname"
    class="text-sm text-gray-500 dark:text-gray-400 flex flex-col gap-y-2"
    >Todo
    <input
      type="text"
      id="todoname"
      name="todoname"
      placeholder="Todo name"
      required
      class="border border-gray-800 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-transparent"
      bind:value={newTask}
    />
  </label>
  <button
    class=" text-white w-full bg-pink-500 border-0 py-2 px-6 focus:outline-none hover:bg-pink-600 rounded"
    >Add Todo</button
  >
</form>
