<script>
  import { Router, Link, Route } from "svelte-routing";
  import Home from "./routes/Home.svelte";
  import ColourConverter from "./routes/ColourConverter.svelte";
  export let url = "";
</script>

<Router url="{url}">
	<nav>
    <div class="nav">
			<div class="nav__logo">
				<h1>CSS Tools</h1>
			</div>
			<div class="nav__links">
				<Link class="nav__links__link" to="/">Home</Link>
    		<Link class="nav__links__link" to="colour">Colour</Link>
			</div>
		</div>
  </nav>
	<div>
		<Route path="colour" component="{ColourConverter}" />
		<Route path="/" ><Home /></Route>
	</div>
</Router>

<style lang="scss">
	nav{
		padding: 10px 30px;
    position: fixed;
    width: 100%;
    box-sizing: border-box;
    display: flex;
    -webkit-box-pack: center;
    justify-content: center;		
	}
	
	.nav{
		padding: 20px;
    display: flex;
    -webkit-box-align: center;
    align-items: center;
    -webkit-box-pack: justify;
    justify-content: space-between;
    box-sizing: border-box;
    max-width: 1600px;
    width: 100%;
		border-radius: 20px;
    background-color: rgb(255, 255, 255);
    width: 100%;
    box-shadow: rgba(109, 109, 109,0.5) 3px 3px 10px -3px;

		&__links{
			display: flex;
			gap: 1rem;
		}

		
	}

</style>