<script>
// @ts-nocheck

  export let isBase = false
  export let baseValue
  export let presetMultiplier
  export let unit = 'ml'

  $:multiplier = isBase ? baseValue : presetMultiplier;
  $:result = isBase ? baseValue : limitTo2DP(baseValue * multiplier);

  /**
	 * @param {number} value
	 */
  function limitTo2DP (value) {
    if (value == Math.round(value)) return value
    return value.toFixed(2)
  }

</script>

<div class='ingredient-container'>
  <input type=number bind:value={multiplier} min=1 max=200>
  <div class='result-container'>
    <span class='result'>{result}</span>
    <span class='unit-measure'>{unit}</span>
  </div>
</div>

<style>
  .ingredient-container {
    display: inline-block;
  }

  input {
    width: 100px;
    padding: 2px 8px;
    height: 24px;
    border-radius: 12px;
    border: 1px solid #ccc;
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

</style>

