<script>

  import tinycolor from "tinycolor2";  

	let hexColor = "";
	let rgbColor = '';
	let color = "#DDF7FE";

  let textColor = "rgb(38, 38, 38)";
  let placeholderColor = "rgb(100, 100, 100)";

	$: getColours(), hexColor

	function getColours(){

		if(hexColor.length === 6){

			let splitColor = hexColor.match(/.{1,2}/g);
			let r = parseInt(splitColor[0], 16)
			let g = parseInt(splitColor[1], 16)
			let b = parseInt(splitColor[2], 16)

      rgbColor = `rgb(${r},${b},${g})`;
			color = `#${hexColor}`;

      if(tinycolor(color).isLight()){
        textColor = "rgb(38, 38, 38)";
        placeholderColor = "rgb(100, 100, 100)";
      }else{
        textColor = "rgb(255, 255, 255)";
        placeholderColor = "rgb(200, 200, 200)";
      }

		}


	}


</script>

<main style="--background-color: {color}; --color-input: {textColor}; --color-placeholder: {placeholderColor};">
	<div class="controls">
		<div class="controls__hex">
			<input type="text" bind:value={hexColor} maxlength="6" placeholder="#DDF7FE"/>
		</div>
		<div class="controls__rgb">
			<input type="text" bind:value={rgbColor} placeholder="rgb(221,247,254)"/>
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

  input{
    height: 40px;
    width: 300px;
    border: none;
    border-bottom: solid 2px grey;
    background-color: transparent;
    color: var(--color-input);
    font-family: futura-pt-bold, sans-serif;
    font-size: 1.4em;
    &::placeholder{
      color: var(--color-placeholder);
      font-family: futura-pt-bold, sans-serif;
    }
  }
</style>