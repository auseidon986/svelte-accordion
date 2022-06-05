<script>
  import '$lib//Accordion/style.css';

	import { slide } from "svelte/transition";
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let item;

	export let entry
	export let isOpen
	const toggle = () => {
    isOpen = !isOpen
    dispatch(isOpen ? 'opened' : 'closed');
  }

</script>

<div bind:this={item}  aria-expanded={isOpen} class="accordion-item">
  <button on:click={toggle} class="accordion-item__button">
    <span>{entry[0]}
  </button>
  {#if isOpen}
  <div transition:slide={{ duration: 300 }} class="accordion-item__text">
    {entry[1]}
  </div>
  {/if}
</div>
