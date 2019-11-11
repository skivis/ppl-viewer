<script>
  import Node from './Node.svelte';

  export let expanded = true;
  export let name;
  export let nodes;

  function toggle() {
    expanded = !expanded;
  }
</script>

<style>
  span {
    padding: 0 0 0 1.5em;
    background: url(https://svelte.dev/tutorial/icons/folder.svg) 0 0.1em no-repeat;
    background-size: 1em 1em;
    /* font-weight: bold; */
    cursor: pointer;
    color: #d73a49;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .expanded {
    background-image: url(https://svelte.dev/tutorial/icons/folder-open.svg);
  }

  ul {
    padding: 0.2em 0 0 1.5em;
    margin: 0 0 0 .5em;
    list-style: none;
    border-left: 1px solid #eee;
  }

  li {
    padding: 0.2em 0;
  }
</style>

<span class:expanded on:click={toggle}>{name}</span>

{#if expanded}
  <ul>
    {#each nodes as node}
      <li>
        {#if node.nodes}
          <svelte:self {...node}/>
        {:else}
          <Node {...node}/>
        {/if}
      </li>
    {/each}
  </ul>
{/if}