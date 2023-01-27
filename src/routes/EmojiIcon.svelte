<script>  
  import { onMount } from 'svelte';
  import { createPicker } from 'picmo';

  export let defaultIcon;
  /**
	 * @type {string}
	 */
  export let ingId;
  let currentIcon = defaultIcon;

  function handleIconClick() {
    console.log('here')
    const container = document.querySelector(`.pickerContainer.ingId-${ingId}`);
    if (container) container.classList.toggle('hidden');
  }

  onMount(() => {
    const pickerContainer = document.querySelector(`.pickerContainer.ingId-${ingId}`);
    const picker = createPicker({
      rootElement: pickerContainer
    });

    // The picker emits an event when an emoji is selected. Do with it as you will!
    picker.addEventListener('emoji:select', event => {
      currentIcon = event.emoji;
      pickerContainer.classList.toggle('hidden');
      console.log('Emoji selected:', event.emoji);
    });
  })
</script>

<div>
  <span class='icon' on:click={handleIconClick}>{currentIcon}</span>
  <span class='pickerContainer ingId-{ingId} hidden'></span>
</div>


<style>

  div {
    display: inline-block;
  }

  .hidden {
    display: none;
  }

  .pickerContainer {
    position: absolute;
  }

  .icon {
    display: inline-block;
    height: 32px;
    width: 32px;
    line-height: 32px;
    bottom: 2px;
    border: 1px solid #000;
    border-radius: 50%;
    text-align: center;
    cursor: pointer;
    position: relative;
  }
  .icon:hover {
    background-color: #fff;
  }
</style>
