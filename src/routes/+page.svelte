<script>
	import { onMount } from 'svelte';
	let playing = false;
	let buttonClass = "silent";
	let audio;
	onMount(() => {
		audio = new Audio('https://cdn.pixabay.com/download/audio/2021/08/09/audio_9a2f521fc5.mp3');
	});

	const play = async () => {
		if (playing == true) {
			audio.pause();
			playing = false;
			buttonClass = "silent";
		} else {
			await audio.play();
			audio.loop = true;
			playing = true;
			buttonClass = "playing";
		}
		console.log(playing);
	};
</script>

<main>
	<div id="hoved">
		<h1>Sophie says</h1>
		<button on:click|self|preventDefault={(playing = () => play())} class={buttonClass}>SUMM!</button>
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
	button.playing {
		display: inline-block;
		outline: 0;
		cursor: pointer;
		border-radius: 6px;
		border: 4px solid #ff4742;
		background: 0 0;
		color: #fff;
		/* color: #ff4742; */
		padding: 15pt 30pt 15pt 30pt;
		box-shadow: rgba(0, 0, 0, 0.07) 0px 2px 4px 0px, rgba(0, 0, 0, 0.05) 0px 1px 1.5px 0px;
		font-weight: 800;
		font-size: 36pt;
		font-family: 'Red Hat Display', Arial;
		transition: all 0.1s ease-in-out;
		/* Start the shake animation and make the animation last for 0.5 seconds */
		animation: shake 0.5s;

		/* When the animation is finished, start again */
		animation-iteration-count: infinite;
	}

	@keyframes shake {
		0% {
			transform: translate(1px, 1px) rotate(0deg);
		}
		10% {
			transform: translate(-1px, -2px) rotate(-1deg);
		}
		20% {
			transform: translate(-3px, 0px) rotate(1deg);
		}
		30% {
			transform: translate(3px, 2px) rotate(0deg);
		}
		40% {
			transform: translate(1px, -1px) rotate(1deg);
		}
		50% {
			transform: translate(-1px, 2px) rotate(-1deg);
		}
		60% {
			transform: translate(-3px, 1px) rotate(0deg);
		}
		70% {
			transform: translate(3px, 1px) rotate(-1deg);
		}
		80% {
			transform: translate(-1px, -1px) rotate(1deg);
		}
		90% {
			transform: translate(1px, 2px) rotate(0deg);
		}
		100% {
			transform: translate(1px, -2px) rotate(-1deg);
		}
	}
	button.silent {
		display: inline-block;
		outline: 0;
		cursor: pointer;
		border-radius: 6px;
		border: 4px solid #ff4742;
		background: 0 0;
		color: #fff;
		/* color: #ff4742; */
		padding: 15pt 30pt 15pt 30pt;
		box-shadow: rgba(0, 0, 0, 0.07) 0px 2px 4px 0px, rgba(0, 0, 0, 0.05) 0px 1px 1.5px 0px;
		font-weight: 800;
		font-size: 36pt;
		font-family: 'Red Hat Display', Arial;
		transition: all 0.1s ease-in-out;
	}
	button:hover {
		color: #fff;
		background-color: #ff4742;
		transform: scale(1.2);
	}
</style>
