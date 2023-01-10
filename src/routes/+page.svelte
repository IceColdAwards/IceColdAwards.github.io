<script>
  import RoundGlass from "$lib/assets/roundglass.jpg"
  import ShopGlass from "$lib/assets/shopglass.jpg"
  import WoodyGlass from "$lib/assets/woodyglass.jpg"
  import SunriseCubes from "$lib/assets/sunrisecubes.jpg"
  import RockyGlass from "$lib/assets/rockyglass.jpg"
  import HeartLake from "$lib/assets/heartlake.jpg"

  let first_pic = RoundGlass
  // Bottom to top all the pictures except the first
  let pics = [ShopGlass, WoodyGlass, SunriseCubes, RockyGlass, HeartLake]

	let y;
  let height;
  let width;

  let best_prefix = ""
  $: best_prefix = (width / height > 1.25) ? "The best ice water of" : ""
</script>

<svelte:window bind:scrollY={y} bind:innerHeight={height} bind:innerWidth={width}/>
<svelte:head>
    <title>Ice Water Awards</title> 
</svelte:head>


<div class="parallax-container" >
	<img
    style="transform: translate(0,{-y / 2}px); z-index=-1"
		src={first_pic}
    alt="A very frosty glass of ice water"
	>
  {#each pics as pic, i}
		<img
      style="transform: translate(0,{-y / 2}px); top: {(i + 1) * 92.5}vh; z-index = {i}; visibility: {(y > height * 1.85 * (i + 1) - height * 0.95) ? "visible" : "hidden"}"
			src={pic}
      alt=""
		>
  {/each}
</div>

<div class="text">
	<span class="big head1" style="opacity: {1 - Math.max(0, y / 250)}">
    Because nothing is better than
	</span>

	<span class="big head2" style="opacity: {1 - Math.max(0, (y - 400) / 150)}">
    ICE
	</span>

	<div class="foreground">
    <span class="announce">{best_prefix} December 2022:</span>
    <span class="award">Fogo de Chão</span>
    <span class="location">Minneapolis, MN</span>
	</div>
	<div class="foreground">
    <span class="announce">{best_prefix} November 2022:</span>
    <span class="award">IkaSan</span>
    <span class="location">Omaha, NE</span>
	</div>
	<div class="foreground">
    <span class="announce">{best_prefix} October 2022:</span>
    <span class="award">Abrohome</span>
    <span class="location">Ames, IA</span>
	</div>
	<div class="foreground">
    <span class="announce">{best_prefix} September 2022:</span>
    <span class="award">Half Price Books</span>
    <span class="location">St. Louis Park, MN</span>
	</div>
	<div class="foreground">
    <span class="announce">{best_prefix} August 2022:</span>
    <span class="award">Literally the Tap</span>
    <span class="location">Ames, IA</span>
	</div>
	<div class="foreground">
	  <span class="big" style="font-size: 10vh">
      Stay Frosty!
	  </span>
    <a href="/about" style="pointer-events:all">About Us</a>
    <p>Copyright © Freez Arctica 2222</p>
    <p>No Rights Reserved</p>
	</div>
</div>

<style>
  .big {
    color: darkblue;
		text-align: center;
    width: 100%;
    z-index: 1;
  }
  .head1 {
    position: fixed;
    top: 10vh;
    font-size: 10vh;
  }
  .head2 {
    position: fixed;
    top: 45vh;
    font-size: 25vh;
  }
	.parallax-container {
		position: fixed;
    object-fit: cover;
    width: 100%;
	}

	.parallax-container img {
		position: fixed;
    width: 100%;
    will-change: transform;
    pointer-events: none;
	}

	.text {
		position: relative;
		width: 100%;
		color: rgb(220,113,43);
		text-align: center;
		padding: 4em 0em 0.0em 0em;
		box-sizing: border-box;
		pointer-events: none;
	}

	span {
		display: block;
		font-size: 1em;
		will-change: transform, opacity;
	}

	.foreground {
		margin-top: 125vh;
		width: 100%;
		height: 30vh;
		background-color: white;
		color: rgb(0, 10, 20);
    padding: 13vh 0vh 17vh;
	}

	:global(body) {
		margin: 0;
		padding: 0;
		background-color: white;
	}

  .announce {
    font-size: 7vh;
    color: gold;
    white-space: nowrap;
  }
  .award {
    font-size: 12vh;
    color: darkblue;
  }

  .location {
    font-size: 6vh;
    white-space: nowrap;
  }
</style>
