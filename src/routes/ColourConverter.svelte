<script>
	let hexColor = "";
	let rgbColor = {r: 0, g: 0, b: 0};
	let color = "#ffffff";



	$: getColours(), hexColor

	function getColours(){

		console.log("Get Color");

		if(hexColor.length === 6){

			let splitColor = hexColor.match(/.{1,2}/g);
			let r = parseInt(splitColor[0], 16)
			let g = parseInt(splitColor[1], 16)
			let b = parseInt(splitColor[2], 16)

			console.log("{r,g,b}", {r,g,b});

			rgbColor = {r,g,b}
			color = `#${hexColor}`

		}


	}


</script>

<main style="--background-color: {color}">
	<div class="controls">
		<div class="controls__hex">
			<input type="text" bind:value={hexColor} maxlength="6"/>
		</div>
		<div class="controls__rgb">
			<input type="text" bind:value={rgbColor.r}/>
			<input type="text" bind:value={rgbColor.g}/>
			<input type="text" bind:value={rgbColor.b}/>
		</div>
	</div>
</main>

<style lang="scss">


	main {
		background-color: var(--background-color);
		height: 100vh;
		width: 100vw;
		display: flex;
		justify-content: center;
		align-items: center;
		box-sizing: border-box;
	}

	.controls{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		&__hex{
			margin-bottom: 20px;
		}
	}
</style>