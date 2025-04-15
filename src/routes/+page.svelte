<script>
    
    let todos = $state([{
        name: "",
        desc: ""
    }]);
    let todoName = $state("")
    let todoDesc = $state("")
    let todoId = $state(0);

    const addTodo = () =>{
        if(todoName && todoDesc){
            todos.push({
                id: todoId, 
                name: todoName,
                desc: todoDesc

            })
            todoId++;
            todoName = "";
            todoDesc = "";
        }
    }

</script>
<main class="h-full w-full flex flex-col *:gap-y-4 justify-center items-center">
    
    <form action=""
        class="flex justify-center items-start flex-col gap-y-1" >
        <div class="flex flex-col gap-y-1">
            <label for="todoname"
                class="text-sm text-gray-500 dark:text-gray-400">Todo</label>
            <input type="text" id="todoname" name="todoname" placeholder="Todo name" required
            class="border border-gray-800 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-transparent"
            bind:value={todoName}> 
        </div>
    
        <div class="flex flex-col gap-y-1">
            <label for="tododesc" class="text-sm text-gray-500 dark:text-gray-400">Description</label>
            <input type="text"
            bind:value={todoDesc} name="tododesc" id="tododesc" class="border border-gray-800 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-transparent "placeholder="Todo description" required>
        </div>
        <button type="submit" class="mt-4 text-white bg-pink-500 border-0 py-2 px-6 focus:outline-none hover:bg-pink-600 rounded" onclick={addTodo}>Add Todo</button>
    </form>

<hr class="w-full border-gray-800 mt-2 mb-2">
<div >
    <div class="flex flex-col gap-y-1">
        <h1 class="text-2xl font-bold">Todos</h1>
        <ul class="list-disc">
            {#each todos as todo}
                <li>{todo.name} - {todo.desc}</li>
            {/each}
        </ul>
    </div>
</div>
</main>
