<script>
	import "./global.css";
	// import VideoPlayer from "./components/VideoPlayer.svelte";
	import YoutubeVideo from "./components/YoutubeVideo.svelte";
	import YouTube from "svelte-youtube";
</script>

<main>
	<!-- <VideoPlayer ID="lala" /> -->
	<YoutubeVideo videoId="1wkPMUZ9vX4" />
	<YouTube
		videoId="1wkPMUZ9vX4"
		options={{
			height: "390",
			width: "640",
			playerVars: {
				autoplay: 0
			}
		}} />
</main>

<style>
	main {
		text-align: center;
	}
</style>
