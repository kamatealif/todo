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

<form onsubmit={addTodo} class="mb-4">
  <label for="todoname"
    >Todo
    <input
      type="text"
      id="todoname"
      name="todoname"
      placeholder="Todo name"
      required
      bind:value={newTask}
    />
  </label>
  <div class="flex justify-end"><button>Add Todo</button></div>
</form>
