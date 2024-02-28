<script>
	// importing components
	import Greet from "./components/Greet.svelte";

	// defining values for components to use
	const users = [
		{firstName : "Priyanshu", lastName : "Singh"},
		{firstName : "Anuj", lastName : "Singh"}
	]
	const spread = {
		name : "Rajesh",
		rollNum : 5
	}
	// setting the context for child to access
	import { setContext } from "svelte";
	const contextValue = "Good Morning !"
	setContext("contextKey", contextValue)

  	import Popup from "./components/Popup.svelte";
	let show = false
	function closePopup(event){
		show = false
		console.log(event.detail) // accesing values passed from child component via custom event
	}

	// Event forwarding
	import Outer from "./components/EventForwarding/Outer.svelte";
	// fn that deals with forwarded events
	function greetFn(event){
        console.log("we have in app : ")
        console.log(event.detail)
    }
</script>

<main>
	{#each users as user, index}
		<Greet name={user.firstName + " " + user.lastName} rollNum={index+1} />
	{/each}
	<Greet /> <!--Default prop in child is used-->
	<Greet {...spread} /> <!-- Spreading an object in parent for child to get values--> 

	<!-- popup handling via custom component events  -->
	<button on:click={()=> show = true}>Show Popup</button>
	{#if show}
		<Popup on:close={closePopup}/> <!--Using custom made component event dispatched from child component-->
	{/if}

	<!-- Event forwarding  -->
	<Outer on:greetEvent={(event)=>greetFn(event)}/> <!--Event handled by child->child component-->
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>