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
	<label>
    <EmojiIcon defaultIcon={'☕️'} pid={'a'} />

    <input type=number bind:value={a} min=1 max=20>
      <div class='result-container'>
        <span class='result'>{a}</span>
        <span class='unit-measure'>ml</span>
      </div>
    <br>
    <span class='icon'></span>
    <input type=range bind:value={a} min=1 max=20>
  </label>
  
  <label>
    <EmojiIcon defaultIcon={'💧'} pid={'b'}/>
    
    <input type=number bind:value={bMultiplier} min=1 max=200>
    <div class='result-container'>
        <span class='result'>{b || 0}</span>
        <span class='unit-measure'>ml</span>
      </div>
  </label>

  <label>
    <EmojiIcon defaultIcon={'🥛'} pid={'c'}/>
    <input type=number bind:value={cMultiplier} min=0 max=200>
      <div class='result-container'>
        <span class='result'>{c || 0}</span>
        <span class='unit-measure'>ml</span>
      </div>
  </label>
</section>

<style>
	section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    flex: 0.2;
    width: 300px;
    margin: 0 auto;
	}

	h1 {
		width: 100%;
	}

  .hidden {
    display: none;
  }

  .pickerContainer {
    position: absolute;
    top: 360px;
  }

  .result-container {
    display: inline-flex;
    width: 70px;
  }

  .icon, .result {
    display: inline-block;
    height: 24px;
    text-align: center;
    line-height: 24px;
  }

  .icon {
    width: 24px;
    border: 1px solid #ccc;
    border-radius: 50%;
    margin-right: 8px;
  }
  .result {
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
