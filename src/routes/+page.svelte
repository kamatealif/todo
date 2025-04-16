<script>
    import Listtodo from "./components/Listtodo.svelte";
    import Todoform from "./components/Todoform.svelte";
    let todos = $props()
</script>

<main class="h-full w-full flex flex-col *:gap-y-4 justify-center items-center">
    <Form />
    <Listtodo {todos}/>
</main>