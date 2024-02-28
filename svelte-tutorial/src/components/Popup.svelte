<script>
    // using createEventDispatcher to create dispatch
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher() 
    const dataFromChildToParent = "from child component to parent via custom event" // data for sending to parent
</script>
<main>
    <div>
        <h1>Hello from Popup</h1>
        <!-- whenever we need to fire a custom event we can do so by dispatching it from child component  -->
        <!-- the dispatch accepts two values, first being name of the event and second the data from child to parent component  -->
        <button on:click={()=> dispatch("close", {dataFromChildToParent})}> Close Me</button>
    </div>
</main>