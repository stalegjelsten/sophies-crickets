<script>
	import { onMount } from 'svelte';
	let playing = false;
	let audio;
	onMount(() => {
		audio = new Audio('https://cdn.pixabay.com/download/audio/2021/08/09/audio_9a2f521fc5.mp3');
	});

	const play = async () => {
		if (playing == true) {
			audio.pause();
			playing = false;
		} else {
			await audio.play();
			audio.loop = true;
			playing = true;
		}
		console.log(playing);
	};
</script>

<main>
	<div id="hoved">
		<h1>Sophie says</h1>
		<button on:click|self|preventDefault={(playing = () => play())}>SUMM!</button>
	</div>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Display:wght@900&display=swap');
	:global(body) {
		background: url('/wp.jpeg');
		background-size: cover;
		background-repeat: no-repeat;
		background-position: center center;
		overflow: hidden;
	}
	main {
		height: 100vh;
		width: 100vw;
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		justify-content: center;
		vertical-align: center;
		flex-direction: column;
	}
	h1 {
		color: #fff;
		font-family: 'Red Hat Display', Arial;
		font-size: 72pt;
	}
	button {
		display: inline-block;
		outline: 0;
		cursor: pointer;
		border-radius: 6px;
		border: 2px solid #ff4742;
		background: 0 0;
		color: #ff4742;
		padding: 15pt 30pt 15pt 30pt;
		box-shadow: rgba(0, 0, 0, 0.07) 0px 2px 4px 0px, rgba(0, 0, 0, 0.05) 0px 1px 1.5px 0px;
		font-weight: 800;
		font-size: 36pt;
		font-family: 'Red Hat Display', Arial;
	}
	button:hover {
		color: #fff;
		background-color: #ff4742;
	}
</style>
