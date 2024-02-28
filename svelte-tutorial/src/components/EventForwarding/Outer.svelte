<script>
    import Inner from "./Inner.svelte";
    // either we can use the fn here or we can pass it on to parent
    function greetFn(event){
        console.log("we have in outer : ")
        console.log(event.detail)
    }
</script>
<main>
    <!-- <Inner on:greetEvent={(event)=>{greetFn(event)}}/>  // Listening to greeEvent event -->
    <Inner on:greetEvent/> <!--Forwarding the greet event to the parent element-->
</main>