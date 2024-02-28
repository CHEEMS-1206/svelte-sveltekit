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
</script>

<main>
	{#each users as user, index}
		<Greet name={user.firstName + " " + user.lastName} rollNum={index+1} />
	{/each}
	<Greet /> <!--Default prop in child is used-->
	<Greet {...spread} /> <!-- Spreading an object in parent for child to get values-->
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