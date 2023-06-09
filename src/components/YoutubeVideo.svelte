<script>
	import { onMount, onDestroy } from "svelte";
	import YoutubePlayer from "youtube-player";

	export let videoId;
	$: player && player.loadVideoById(videoId);

	let player;
	let options = {
		playerVars: {
			autoplay: 0
		}
	};

	onMount(() => {
		player = YoutubePlayer(player, options);
		player.loadVideoById(videoId);
		player.playVideo();
	});

	onDestroy(() => {
		player = null;
	});
</script>

<div id="youtube-player" bind:this={player} />
