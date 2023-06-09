<script>
	import { onMount } from "svelte";
	export let ID = "";
	let player;
	let iframeApiReady = false;

	onMount(() => {
		console.log(player);
		var tag = document.createElement("script");
		tag.src = "https://www.youtube.com/iframe_api";
		var firstScriptTag = document.getElementsByTagName("script")[0];
		firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

		window.onYouTubeIframeAPIReady = () => {
			console.log("READY");
			window.dispatchEvent(new Event("iframeApiReady"));
			player = new YT.Player("video-player", {
				width: "640",
				height: "390",
				videoId: "M7lc1UVf-VE",
				playerVars: {
					"playsinline": 1
				},
				events: {
					"onReady": onPlayerReady,
					"onStateChange": onPlayerStateChange
				}
			});
		};

		function onPlayerReady(event) {
			event.target.playVideo();
		}
		var done = false;
		function onPlayerStateChange(event) {
			if (event.data == YT.PlayerState.PLAYING && !done) {
				setTimeout(stopVideo, 2000);
				done = true;
			}
		}
		function stopVideo() {
			player.stopVideo();
		}
	});
</script>

<!-- <svelte:head>
	<script>
		console.log(window.onYouTubeIframeAPIReady);
	</script>
	<script defer src="https://www.youtube.com/iframe_api"></script>
</svelte:head> -->

<h1>{ID}</h1>
<div id="video-player" bind:this={player} />

<style>
	/* CSS */
</style>
