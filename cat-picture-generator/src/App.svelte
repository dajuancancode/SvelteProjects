<script>
	import axios from "axios"
	
	let image;
	
	const getCatPicture = async () => {
		try{
				let response = await axios.get('https://api.thecatapi.com/v1/images/search', { params: { limit:1, size:"full" } } ) // Ask for 1 Image, at full resolution
				image = response.data[0].url // the response is an Array, so just use the first item as the Image
		}catch(err){
				console.log(err)
		}
	}
</script>

<main>
	<button on:click = {getCatPicture}>
		Get New Cat
	</button>
	<div class="catImageContainer">
		{#if image}
		<img src="{image}" alt="Cat doing something"/>
		{:else}
		<p>Click the button to view an image or gif of a cat</p>
		{/if}
	</div>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	button {
		display: inline-block;
		padding: 10px 30px;
		border-radius: 50px;
		background: white;
		border: 2px solid #eb2f06;
		transition: all ease-in-out .5s;
		cursor: pointer;
	}

	button:hover {
		border: 2px solid transparent;
		background: #eb2f06;
		color: #fff;
	}

	.catImageContainer {
		width: 750px;
		height: 750px;
		text-align: center;
		overflow: hidden;
	}

	img {
		max-width: 100%;
		height: auto;
	}
</style>