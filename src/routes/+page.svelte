<script>  
  import EmojiIcon from "./EmojiIcon.svelte";
	import Ingredient from "./Ingredient.svelte";

	let baseValue = 10
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Proportionate POC app" />
</svelte:head>

<section>
  <h1>Proportionate</h1>
  <br>

	<div class='ingredient-row'>
    <Ingredient baseValue={baseValue} isBase={true} unit={'g'}/>
    <EmojiIcon defaultIcon={'☕️'} ingId={'a'} />
  </div>

  <div class='slider'>
    <input type=range bind:value={baseValue} min=1 max=20>
  </div>
  <br>

  <div class='ingredient-row'>
    <Ingredient baseValue={baseValue} presetMultiplier={9.1}/>
    <EmojiIcon defaultIcon={'💧'} ingId={'b'} />
  </div>

  <div class='ingredient-row'>
    <Ingredient baseValue={baseValue} presetMultiplier={8}/>
    <EmojiIcon defaultIcon={'🥛'} ingId={'c'} />
  </div>
</section>

<style>
	section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    flex: 0.2;
    width: fit-content;
    margin: 0 auto;
	}

	h1 {
		width: 100%;
	}

  .hidden {
    display: none;
  }

  .ingredient-container {
    display: inline-block;
  }

  .slider input {
    display: inline-block;
    padding: 0;
    width: 100%;
  }

</style>
