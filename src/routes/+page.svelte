<script>
	let playing = false;

	const play = async () => {
		let audio = await new Audio(
			'https://cdn.pixabay.com/download/audio/2021/08/09/audio_9a2f521fc5.mp3'
		);
		if (playing == true) {
			audio.pause();
		} else {
			await audio.play();
		}
		console.log(playing)
		return !playing
	};

</script>

<div id="main">
	<h1>Sophie says</h1>
	<button on:click|self|preventDefault={playing = () => play()}>Summ!</button>
</div>

<style>
	:global(body) {
		height: 100vh;
		width: 100vw;
		background: url('wp.jpeg');
		background-size: cover;
		background-repeat: no-repeat;
	}
	#main {
		text-align: center;
		margin: auto;
		display: flex;
		vertical-align: center;
		flex-direction: column;
	}
	h1 {
		color: #fff;
		font-family: Arial, Helvetica, sans-serif;
	}
	button {
		max-width: 10vw;
		margin:auto;
	}
</style>
