<script>
  import "./styles/Global.svelte";
  import { onMount } from 'svelte';
  import Nav from './components/Nav.svelte';
  import TreeNode from './components/TreeNode.svelte';
  import Spinner from './components/Spinner.svelte';

  let data;

  onMount(async () => {
    const res = await fetch('http://82fc9574.eu.ngrok.io/ppl/28100045/CTLSPAR_151210150521/json');
    data = await res.json();
  });
</script>

<style>
  main {
    font-size: 12px;
    padding: 1em 1.5em;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, Courier, monospace;
  }
</style>

<Nav/>

<main>
  {#if data}
    <TreeNode {...data}/>
  {:else}
    <Spinner/>
  {/if}
</main>