<script>
	import { fade, fly } from 'svelte/transition';

	import EmojiDisplay from "./EmojiDisplay.svelte";
	import EmojiDescription from "./EmojiDescription.svelte";
	import Button from "./Button.svelte";

	let isLoaded = false;
	let currentEmoji = '🥶'
	const emojis = ['🥳', '🧐', '😎', '🤩'];
	let coord = {x: '', y: ''};

	function randomizeEmoji() {
		return emojis[Math.floor(Math.random() * emojis.length)];
	}

	function handleRandomButton() {
		currentEmoji = randomizeEmoji();
	}

	setTimeout(() => {
		isLoaded = true;
	}, 2000);

	function handleMouseMove(event) {
		coord.x = event.clientX;
		coord.y = event.clientY;
	}
</script>

<svelte:head>
    <link rel="stylesheet" href="https://unpkg.com/terminal.css@0.7.2/dist/terminal.min.css" />
</svelte:head>

<main class="container" on:mousemove="{handleMouseMove}">
	<p>Mouse position : {coord.x} x {coord.y}</p>

	<h1>Emoji</h1>

	<ul>
		{#each emojis as item}
		<li>{item}</li>
		{/each}
	</ul>

	{#if isLoaded}
		<div in:fly={{ y:200, duration: 2000}} out:fade>
			<EmojiDisplay {currentEmoji} />
			<EmojiDescription />
			<Button 
				title={'randomize'}
				on:click|once={handleRandomButton} />
		</div>
	{:else}
		<h2>Waitt bro...</h2>
	{/if}

	<Button title={'Toggle'} on:click={()=> isLoaded = !isLoaded} />
</main>
