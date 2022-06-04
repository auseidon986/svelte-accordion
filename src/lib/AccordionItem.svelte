<script>
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
<style>

  :root {
    --header-bg: #ffffff;
    --active-header-bg: #f5f5f5;
    --red-color: #bb021b;
    --border-color: #cccccc;
    --icon-size: 14px;
    --icon-thikness: 4px;
  }

  .accordion-item__button {
    display: block;
    position: relative;
    font-size: 1.6rem; 
    cursor: pointer;
    border: solid 1px var(--border-color);
    width: 100%;
    text-align: left;
    margin: 0; 
    padding: 1.5rem 1.5rem 1.5rem 3rem;
    background-color: var(--header-bg);
    transition: background-color 0.2s ease-in, color 0.2s ease-in;
  }
  [aria-expanded=true] .accordion-item__button {color: var(--red-color); background-color: var(--active-header-bg);}


  .accordion-item__button:before, .accordion-item__button:after {
    content: "";
    border-color: var(--red-color);
    display: block;
    box-sizing: border-box;
    position: absolute;
    text-align: center;
    top: 50%;
    width: var(--icon-size);
    height: var(--icon-size);
  }

  .accordion-item__button:before {
    left: 12px;
    border-top: var(--icon-thikness) solid;
    transform: translateY(-2px);
  }

  .accordion-item__button:after {
    transition: transform 0.2s ease-in;
    transform: translateY(-50%);
    border-left: var(--icon-thikness) solid;
    left: 17px;
  }

  [aria-expanded=true] .accordion-item__button:after { transform: rotate(90deg) translateX(-2px) translateY(5px);}

  .accordion-item__text {
    font-size: 1.4rem; 
    border: solid 1px var(--border-color);
    border-top: none; border-bottom: none;
    position: relative;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
    padding: 1.5em 1.5em 1.5em 2em;
  }
  .accordion-item__text::before {
    content: "";
    border-left: solid 5px var(--red-color);
    border-right: solid 1px var(--border-color);
    position: absolute;
    left: 0; top: 0; bottom: 0; width: 0;
  }

  .accordion-item:last-child .accordion-item__text {
    border-bottom: solid 1px var(--border-color);
  }

</style>

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
