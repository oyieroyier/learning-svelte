<script>
	let color = "red";

	let firstName = "Jimi";
	let lastName = "Hendrix";
	let beltColor = "Black";

	// Syntax for a reactive value in Svelte:
	$: fullname = `${firstName}, ${lastName}`

	/* A reactive statement always warches the value passed to it and when that value changes, the statement runs. */
	// Syntax for a reactive statement in Svelte:
	$: console.log(beltColor);

	/* If you want to perform a more complex statement maybe spanning several lines, you put that code block inside curly braces
	Only one value needs to change for the code block to run.
	Not all the values
	
	NOTE: We can use other reactive values inside our reactive statements*/
	
	// Here's a simple example
	$:{
		console.log(firstName);
		console.log(lastName);
		console.log(fullname);
	}

	const handleClick = () => color = "green"
	const handleChange = (e) => color = e.target.value
</script>

<main>
	<!-- First foray into reactive states in Svelte -->
	<h1 style="color: {color}">The color is {color}!</h1>
	<button on:click={handleClick}>CLICK TO CHANGE TO GREEN</button>
	<input type="text" bind:value={color}>

	<hr>	
	<hr>

	<!-- Deeper foray into reactive values -->

	<p>{fullname} - {beltColor} Belt</p>
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltColor}>
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