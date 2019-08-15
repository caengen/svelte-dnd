<script>
	import Canvas from './Canvas.svelte';
	let count = 0;
	$: doubled = count * 2;
	const handleClick = () => count++;

	$: if (count >= 10) {
		alert("Count to high!")
		count--;
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {count}!</h1>
<h2>And hello doubled {doubled}</h2>

<button on:click={handleClick}>+ count</button>

<Canvas />