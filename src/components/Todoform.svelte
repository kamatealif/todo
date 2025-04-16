<script>
      
      let todos = $state([{
        name: null
    }]);
    let todoName = $state("")
    let todoId = $state(0);

    const addTodo = () =>{
        if(todoName && todoDesc){
            todos.push({
                id: todoId, 
                name: todoName

            })
            todoId++;
            todoName = "";
        }
    }

</script>

    <form action=""
        onsubmit={addTodo}
        class="flex justify-center items-start flex-col gap-y-1" >
        <div class="flex flex-col gap-y-1">
            <label for="todoname"
                class="text-sm text-gray-500 dark:text-gray-400">Todo</label>
            <input type="text" id="todoname" name="todoname" placeholder="Todo name" required
            class="border border-gray-800 rounded-md p-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-transparent"
            bind:value={todoName}> 
        </div>
    
        <button type="submit" class="mt-4 text-white bg-pink-500 border-0 py-2 px-6 focus:outline-none hover:bg-pink-600 rounded" >Add Todo</button>
    </form>
