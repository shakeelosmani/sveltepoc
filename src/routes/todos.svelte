<script lang="ts">
    import type { Todo } from "src/models/todo";
    import { onMount } from 'svelte'
    
    export let todos: Array<Todo> = [];


    onMount(async () => {
        const res = await fetch('https://jsonplaceholder.typicode.com/todos')
        todos = await res.json();
        //window.alert("loaded everything... message using window")
    })     
</script>

<ul>
    {#each todos as todo}
        <li>{todo.id}</li>
        <li>{todo.title}</li>
        <li>{todo.userId}</li>
        <li>{todo.completed}</li>
    {/each}
</ul>
<br>
<p>Go back to <a href="/">Home</a></p>

<style lang="scss">
    ul {
        list-style: none;
    }
</style>