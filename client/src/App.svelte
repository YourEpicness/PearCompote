<script lang="ts">
	import ContactCard from './ContactCard.svelte'

	let name: string = "Johnny";
	let age: number = 21;
	let title: string = "Janitor";
	let description: string = "A cleaning man";
	let image: string = ""

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

	function nameInput(e) {
		const enteredValue = e.target.value;
		name = enteredValue;
	}
</script>

<main>
	<h1>Hello {uppercaseName}!</h1>
	<p>I am {age} years old! </p>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<!-- Method One of binding input data to variable -->
	<!-- <input type="text" value={name} on:input={nameInput}> -->
	<input type="text" bind:value={name} />
	<input type="text" bind:value={title}/>
	<input type="text" bind:value={image}/>
	<textarea rows="3" bind:value={description}/>
	<button on:click={incrementAge}> Change Age </button>
	<button on:click={changeName}> Change Name</button>

	<!-- Destructuring only works when variable name and input are the same -->
	<ContactCard 
	userName={name} 
	jobTitle={title} 
	{description} 
	userImage={image}/>
</main>

<style lang="scss">
	$color: blue;

	h1 {
		color: $color;
	}
</style>