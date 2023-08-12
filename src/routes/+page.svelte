<script>
	import { onMount } from 'svelte';
	let WOTD =
		'One summer night a man stood on a low hill overlooking a wide expanse of forest and field. By the full moon hanging low in the west he knew what he might not have known otherwise: that it was near the hour of dawn. A light mist lay along the earth, partly veiling the lower features of the landscape, but above it the taller trees showed in well defined masses against a clear sky. Two or three farmhouses were visible through the haze, but in none of them, naturally, was a light. Nowhere, indeed, was any sign or suggestion of life except the barking of a distant dog, which, repeated with mechanical iteration, served rather to accentuate than dispel the loneliness of the scene.';
	let currentPosition = 0;
	function handleKeyDown(event) {
		if (event.key === ' ') {
			event.preventDefault(); 
        }
		if (currentPosition < WOTD.length && event.key === WOTD[currentPosition]) {
			currentPosition++;
		}
	}

	onMount(() => {
		window.addEventListener('keydown', handleKeyDown);

		return () => {
			window.removeEventListener('keydown', handleKeyDown);
		};
	});
</script>

<div class="layout">
	<nav>
		<h1 class="title">🔥 sveltype</h1>
	</nav>
</div>
<br>
<div>
	<h1>
		{WOTD.slice(0, currentPosition)}{#if currentPosition < WOTD.length}<span class="underline"
				>{WOTD[currentPosition]}</span
			>{/if}{WOTD.slice(currentPosition + 1)}
	</h1>
</div>

<style>
	.underline {
		text-decoration: underline;
		color: red; /* optional: to make the current letter stand out more */
	}
    .title{
        font-size: 50px;
    }
</style>
