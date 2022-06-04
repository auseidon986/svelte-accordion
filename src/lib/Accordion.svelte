<script>
	import { onMount } from 'svelte';
	import { tick } from "svelte";
	import Item from './AccordionItem.svelte'

	const data = {
		'foo': 'Foo Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.',
		'bar': 'Bar Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.',
		'baz': 'Baz Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
	}

	let current = ''

	onMount(() => {
		setTimeout(() => current = 'foo', 200)
	});

</script>

<div class="accordion-wrapper">
	<div class="accordion-wrapper__status">
		<p>Currently selected section: <b>{current ? current : 'None'}</b> </p>
	</div>
	
	<div class="accordion accordion-wrapper__accordion">
		{#each Object.entries(data) as entry, i}
			<Item {entry} isOpen={current == entry[0]} on:opened="{() => current = entry[0]}" on:closed="{() => current = ''}" />
		{/each}
	</div>
	
</div>

<style>
  .accordion-wrapper {
    font-size: 1.6rem;
  }
</style>

