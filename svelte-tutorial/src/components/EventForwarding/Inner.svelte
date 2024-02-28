<script>
    import { createEventDispatcher } from "svelte";
    // creating a fn to handle actions in parent
    const dispatch = createEventDispatcher()
    function greetFn(){
        dispatch("greetEvent","Hello from inner")
    }
</script>
<main>
    <button on:click={greetFn}>Greet</button> <!--Custom event passed on to parent-->
</main>