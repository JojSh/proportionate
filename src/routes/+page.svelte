<script>  
  import EmojiIcon from "./EmojiIcon.svelte";

	let a = 10
  $:bMultiplier = 9.1
  $:cMultiplier = 8
	$:b = limitTo2DP(a * bMultiplier)
	$:c = limitTo2DP(a * cMultiplier)

  /**
	 * @param {number} value
	 */
  function limitTo2DP (value) {
    if (value == Math.round(value)) return value
    return value.toFixed(2)
  }
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Proportionate POC app" />
</svelte:head>

<section>
  <h1>Proportionate</h1>
  <br>
	<div class='ingredient-row'>
    <input type=number bind:value={a} min=1 max=20>
    <div class='result-container'>
      <span class='result'>{a}</span>
      <span class='unit-measure'>g</span>
    </div>
    <EmojiIcon defaultIcon={'☕️'} pid={'a'} />
  </div>

  <div class='ingredient-row slider'>
    <input type=range bind:value={a} min=1 max=20>
  </div>

  <br>
  
  <div class='ingredient-row'>
    <input type=number bind:value={bMultiplier} min=1 max=200>
    <div class='result-container'>
      <span class='result'>{b || 0}</span>
      <span class='unit-measure'>ml</span>
    </div>

    <EmojiIcon defaultIcon={'💧'} pid={'b'}/>
  </div>

  <div class='ingredient-row'>
    <input type=number bind:value={cMultiplier} min=0 max=200>
    <div class='result-container'>
      <span class='result'>{c || 0}</span>
      <span class='unit-measure'>ml</span>
    </div>

    <EmojiIcon defaultIcon={'🥛'} pid={'c'}/>
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

  .ingredient-row {
    display: inline-block;
  }
  .ingredient-row.slider input {
    padding: 0;
    width: 100%;
  }

  .result-container {
    display: inline-flex;
    width: 94px;
  }

  .result {
    display: inline-block;
    height: 24px;
    text-align: center;
    line-height: 24px;
    background-color: white;
    margin-left: 8px;
    border: 1px solid #000000;
    width: fit-content;
    min-width: 48px;
    border-radius: 12px;
    padding: 2px 8px;
  }

  .unit-measure {
    line-height: 38px;
    margin-left: 4px;
  }

  input {
    width: 100px;
    padding: 2px 8px;
    height: 24px;
    border-radius: 12px;
    border: 1px solid #ccc;
  }

</style>
