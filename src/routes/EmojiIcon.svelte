<script>  
  import { onMount } from 'svelte';
  import { createPicker } from 'picmo';

  export let defaultIcon;
  /**
	 * @type {string}
	 */
  export let pid;
  let currentIcon = defaultIcon;

  function handleIconClick() {
    console.log('here')
    const container = document.querySelector(`.pickerContainer.pid-${pid}`);
    if (container) container.classList.toggle('hidden');
  }

  onMount(() => {
    const pickerContainer = document.querySelector(`.pickerContainer.pid-${pid}`);
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

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Proportionate POC app" />
</svelte:head>

<div>
  <span class='icon' on:click={handleIconClick}>{currentIcon}</span>
  <span class='pickerContainer pid-{pid} hidden'></span>
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
