<script>
    let todos = $props()
</script>

   <div class="flex flex-col gap-y-1">
        <h1 class="text-2xl font-bold">Todos</h1>
        <ul class="list-disc">
            {#if todos}
                {#each todos as todo}
                    <li>{todo.name} - {todo.desc}</li>
                {/each}
            {:else}
                <li>No todos available</li>
            {/if}
        </ul>
    </div>
