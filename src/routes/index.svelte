<script context="module">
	export const prerender = true;
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<script>
  import Accordion from '$lib/Accordion.svelte'
</script>

<section>

  <h1>IDFive Accordion using SvelteKit</h1>

  <div class="container">
    <Accordion></Accordion>
  </div>

</section>


<style>
  .container {
    max-width: 720px;
    margin: auto;
  }

  h1 {font-size: 2rem; padding: 2rem; text-align: center;}
</style>
