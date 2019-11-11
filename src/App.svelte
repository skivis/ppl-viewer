<script>
  import { onMount } from 'svelte';
  import TreeNode from './components/TreeNode.svelte';

  let node;

  onMount(async () => {
    await getFile()
  })

  function getFile() {
    fetch('http://localhost:5001/ppl/5513000100000084/DCPAR___151207114110/json')
      .then(resp => resp.json())
      .then(data => (node = data));
  }
</script>

<main>
  {#if node}
    <TreeNode {...node}/>
  {:else}
    <span>Loading...</span>
  {/if}
</main>