<script>  
  import EmojiIcon from "./EmojiIcon.svelte";
	import Ingredient from "./Ingredient.svelte";

	let baseValue = 10
  const ingredients = [
    {
      initIcon: '💧',
      initMultiplier: 9.1
    },
    {
      initIcon: '🥛',
      initMultiplier: 8
    }
  ]

</script>

<section>
  <h1>Proportionate</h1>
  <br>

	<div class='ingredient-row'>
    <Ingredient baseValue={baseValue} isBase={true} unit={'g'}/>
    <EmojiIcon initIcon={'☕️'} ingId={'base'} />
  </div>

  <div class='slider'>
    <input type=range bind:value={baseValue} min=1 max=20>
  </div>
  <br>

  {#each ingredients as ingredient, i}
    <div class='ingredient-row'>
      <Ingredient baseValue={baseValue} initMultiplier={ingredient.initMultiplier}/>
      <EmojiIcon initIcon={ingredient.initIcon} ingId={String(i)} />
    </div>
  {/each}
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
