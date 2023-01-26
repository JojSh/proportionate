<script>
	let a = 1
  $:bMultiplier = 10
  $:cMultiplier = 8
	$:b = limitTo2DP(a * bMultiplier)
	$:c = limitTo2DP(a * cMultiplier)

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
	<label>
    <span class='icon'>a</span>
    <input type=number bind:value={a} min=0 max=20>
      <div class='result-container'><span class='result'>{a}</span></div>
    <br>
    <span class='icon'></span>
    <input type=range bind:value={a} min=0 max=20>
  </label>
  
  <label>
    <span class='icon'>b</span>
    <input type=number bind:value={bMultiplier} min=0 max=200>
      <div class='result-container'><span class='result'>{b || 0}</span></div>
  </label>

  <label>
    <span class='icon'>c</span>
    <input type=number bind:value={cMultiplier} min=0 max=200>
      <div class='result-container'><span class='result'>{c || 0}</span></div>
  </label>
</section>

<style>
	section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    flex: 0.6;
    width: 240px;
    margin: 0 auto;
	}

	h1 {
		width: 100%;
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
    min-width: 24px;
    border-radius: 12px;
    padding: 2px 8px;
  }

  input {
    width: 100px;
    padding: 2px 8px;
    height: 24px;
    border-radius: 12px;
    border: 1px solid #ccc;
  }

</style>
