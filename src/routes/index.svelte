<script context="module">
	export const prerender = true;
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<script>
  import '$lib//Accordion/style.css';
  import Accordion from '$lib/Accordion/Accordion.svelte'
</script>

<section>

  <h1>Svelte Accordion</h1>

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
