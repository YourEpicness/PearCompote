<script lang="ts">
	let name: string = "Johnny";
	let age: number = 21;

	// Svelte version of "labeled statements"
	// $: updates the page whenever the variable specified changes
	$: uppercaseName = name.toUpperCase();

	$: console.log(name);

	$: if (name === 'Not Johnny') {
		console.log('It runs');
		age = 12
	}

	function incrementAge():void {
		age += 1
	}

	function changeName():void {
		name = "Not Johnny"
	}
</script>

<main>
	<h1>Hello {uppercaseName}!</h1>
	<p>I am {age} years old! </p>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button on:click={incrementAge}> Change Age </button>
	<button on:click={changeName}> Change Name</button>
</main>

<style lang="scss">
	$color: blue;

	h1 {
		color: $color;
	}
</style>