<script>
    // importing getContext to get value from context API
    import {getContext} from 'svelte'
    // export props name from child component and bind them in content
    export let name = "Abc", rollNum = "NA"
    const contextValue = getContext("contextKey")
</script>
<main>
    <h1>Hello {name} your roll number is {rollNum}</h1>
    <p>{contextValue}</p>
</main>
<style>

</style>