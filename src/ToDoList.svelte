<script>
  import { toDoItems } from "./store";
  import { fade, scale } from "svelte/transition"

  function removeFromList(i) {
    $toDoItems.splice(i, 1);
    $toDoItems = $toDoItems;
  }
</script>

{#each $toDoItems as item, index}
  <div class="toDoItems" in:scale out:fade="{{ duration: 500 }}">
    <label class="check-wrap" for="check-{index}">
      <input bind:checked={item.status} type="checkbox" id="check-{index}" />
      <span class:checked={item.status}>{item.text}</span>
    </label>
    <button on:click={() => removeFromList(index)}>Delete</button>
    <br />
  </div>
{/each}

<style>
  .check-wrap {
    display: inline;
  }
  .checked {
    text-decoration: line-through;
  }
  .toDoItems {
    text-align: left;
  }
</style>
